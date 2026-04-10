# ue4模组开发中创建预览音频的问题

## 需求概述

近来为某个神秘游戏寻得一程序，通过ue4 mod的方式进行lua注入从而添加自定义音乐。随后一日，模组更新了特性，支持在bgm选择界面时加入了预览音频的逻辑。其自述文件如此写：

> You can provide a separate audio file to be used as the
> preview (on the BGM select screen) instead of the default behavior of
> playing the main track from its loop start point.
>
> Place a file named `<audio_file_name>_Preview` with any supported extension (`.mp3`, `.wav`, `.ogg`, `.flac`) alongside the main audio file. For example:
>
> ```text display
> Songs/
>   MY_AUDIO.wav
>   MY_AUDIO_Preview.mp3   <- this will be used for the BGM select preview
> ```
>
> The preview file does not need to match the main
> track's format. Preview files are automatically excluded from the song
> list - they won't appear as separate tracks.

可以看到，这个逻辑是非常傻瓜式的。然而当我在准备开始制作预览音频的时候发现，我竟然塞了快七十首歌，如果用au/audacity手动一个个处理的话是非常耗费时间的。

---

## 自动化实现

那么，如果要寻求脚本批处理的方法来“偷懒”，我第一个想到的是用ffmpeg来进行简单粗暴的一刀切式处理，统一截取音频的某个时间段落来做到省事。但是这种方法无疑是不好的，因为不同的歌曲编排不同，通常预览音频都是截取歌曲的高潮部分，而这种方式容易截取出来一些不知所谓的东西出来。

这时候，我竟然蠢人灵机一动，想起之前在某篇洋人写的文章里提到了python的Librosa库这个东西，

Librosa 是 Python 中**专业、轻量、最常用的音频与音乐分析库**，可以读取音频、计算节奏、BPM、音量、鼓点等特征，通过数学算法识别音频中能量最强、节奏最密集的片段，从而实现自动检测高潮、剪辑片段等功能，是做音频处理、音乐提取和自动化剪辑的核心工具。用这个库做一个程序实现，好像正好可以满足我既要又要的需求。

---

### 代码实现

```python
import os
import numpy as np
import librosa
import ffmpeg
```

这三行是导入库。os是处理文件用的，np是数学计算库，第三个是本尊，最后一个还得用他，因为后面要切分。

```python
# ====================== 你可以改的参数 ======================
PREVIEW_DURATION = x   # 预览音频长度（秒）
MIN_START = 10         # 不从最开头截，避免前奏空白
# ===========================================================

```

赋值两个变量

```python
def make_preview(audio_path):
#  定义一个函数，专门处理单个音频文件。
print(f"正在分析：{audio_path}")
# 打印文件名输出 （给自己看的）

# 加载音频
y, sr = librosa.load(audio_path, sr=None)
duration = librosa.get_duration(y=y, sr=sr)
# 读音频，得到：
# y = 音频波形数据
# sr = 采样率
# duration = 音频总时长
# 计算每帧能量
        hop_length = 512
        rms = librosa.feature.rms(y=y, hop_length=hop_length)[0]
        times = librosa.times_like(rms, sr=sr, hop_length=hop_length)

        # 只考虑 MIN_START ~ (总时长-预览长度) 之间的片段
        valid_mask = times >= MIN_START
        valid_times = times[valid_mask]
        valid_rms = rms[valid_mask]
        if len(valid_times) == 0:
            start = 0
# 只看 10 秒以后 的片段，避免前奏。如果有效片段为空，就从 0 秒开始。
        else:
            # 找到能量最大的帧作为起点
            best_idx = np.argmax(valid_rms)
            start = valid_times[best_idx]

# 找到能量最大的位置 = 高潮起点。
            # 保证不超尾
            max_start = duration - PREVIEW_DURATION
            start = min(start, max_start)
    # 输出文件名（命名规则：原名_Preview.mp3）
    base, ext = os.path.splitext(audio_path)
    out_path = f"{base}_Preview.mp3"

try:
        stream = ffmpeg.input(audio_path, ss=start, t=PREVIEW_DURATION)
        stream = ffmpeg.output(stream, out_path, q:a=2)
        ffmpeg.run(stream, overwrite_output=True, quiet=True)

# ffmpeg干的事：


'''
ss=start：从高潮开始
t=8：截 8 秒
q:a=2：高质量 MP3
overwrite：覆盖旧文件
quiet：不输出日志
'''

        fname_lower = f.lower()
# 遍历文件
        # 只处理原始音乐，跳过已生成的预览文件
        if fname_lower.endswith(exts) and "_preview" not in fname_lower:
            make_preview(f)
#统一转小写避免问题

```


没了，再见。👋

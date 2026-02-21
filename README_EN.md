# Make Demo GIF / MP4

[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Colab](https://img.shields.io/badge/platform-Google%20Colab-orange.svg)](https://colab.research.google.com/github/hiroaki-com/colab-video-converter/blob/main/make_demo_gif_mp4_en.ipynb)
[![FFmpeg](https://img.shields.io/badge/FFmpeg-compatible-blueviolet.svg)](https://ffmpeg.org/)

English | [日本語](./README.md)

![make_demo_en](https://github.com/user-attachments/assets/4056749b-17b6-463d-b865-36d1e50f4364)

### Overview

A Google Colab tool that converts screen recordings and other video files into GIF or MP4 optimized for GitHub and social media. Merging, quality tuning, playback speed adjustment, and targeted zoom are all handled through a notebook UI — no command-line required.

Supported input formats: `.mov` `.mp4` `.avi` `.mkv` `.webm`

#### Key Features

- Merge multiple videos with drag-and-drop order selection
- Output as GIF or MP4 (H.264)
- Preset quality profiles (GitHub README / SNS lightweight / High quality) or fully custom
- Playback speed control (0.75x – 2.0x, custom value also supported)
- Zoom feature (highlight specific areas in screen recording demos)
- Save locally or to Google Drive

#### Who Is This For

- Developers who want to embed screen recordings directly into GitHub READMEs or social media
- Developers who want to emphasize important UI interactions in demo videos
- Engineers who want to produce polished demo videos without writing ffmpeg commands
- Technical writers creating lightweight GIFs for blogs or documentation

---

### Quick Start

#### Open in Colab

```
https://colab.research.google.com/github/hiroaki-com/colab-video-converter/blob/main/make_demo_gif_mp4_en.ipynb
```

> Runs on CPU runtime. No GPU required.

#### Step-by-Step

1. Open the notebook in Google Colab
2. Run cells from top to bottom
3. Step ② — Upload your video file(s) (multiple files supported)
4. Step ③ — Set the merge order (skipped automatically for a single file)
5. Step ④ — Choose output format, quality, and playback speed
6. Step ⑤ — Run the conversion
7. Step ⑥ — Preview the result
8. Step ⑦ — Configure zoom settings (optional)
9. Step ⑧ — Generate final output
10. Step ⑨ — Select a save destination and download

---

### Choosing an Output Format

| Format | Characteristics | Best For | Not Ideal For |
|---|---|---|---|
| GIF | Auto-plays, loops, works in any Markdown renderer. 256 colors, larger file size | GitHub README (auto-play required), Zenn / Qiita | Size-constrained environments |
| MP4 (H.264) | High quality, small file size, full color. Requires a media player | X / Slack / GitHub README (click-to-play) | Scenarios requiring auto-play or looping |

---

### Quality Settings

#### GIF Presets

| Preset | Width | FPS | Colors | Use Case |
|:---|:---:|:---:|:---:|:---|
| GitHub README | 960px | 15fps | 256 | README embedding (recommended) |
| SNS / Lightweight | 640px | 10fps | 128 | Minimize file size |
| High Quality | 1280px | 20fps | 256 | Quality-first output |
| Custom | any | any | any | Fine-grained control |

#### MP4 Presets

| Preset | CRF | Notes |
|:---|:---:|:---|
| High Quality | 18 | Larger file size |
| Standard | 23 | Balanced (recommended) |
| Lightweight | 28 | Smaller file size |
| Custom | 0–51 | Fine-grained control |

#### Playback Speed

| Option | Multiplier |
|:---|:---:|
| Normal | 1.0x |
| 1.5× Speed | 1.5x |
| 2.0× Speed | 2.0x |
| 0.75× Speed | 0.75x |
| Custom | 0.1x – 10.0x |

---

### Zoom Feature

Highlight important UI interactions in your screen recording demos.

#### How to Use

1. Play the preview in Step ⑥ to identify timestamps where you want to zoom
2. Check "Add zoom" in Step ⑦
3. Click "+ Add Zoom Event" to add a zoom event
4. Configure each event:
   - Zoom area (select from 3×3 grid)
   - Max zoom level (1.1x – 5.0x)
   - Start time and duration for zoom-in / hold / zoom-out
5. Run Step ⑧ to generate the final output

> You can add multiple zoom events, but make sure they don't overlap in time.

---

### Platform Size Limits (as of Feb 2026)

| Platform | Supported Formats | Size Limit |
|---|---|---|
| GitHub README | GIF / MP4 / MOV | 100 MB (video) / 10 MB (GIF) |
| Zenn | GIF | 3 MB |
| Qiita | GIF / MP4 | 100 MB |
| X (standard) | MP4 / MOV | 512 MB |
| Slack | GIF / MP4 / MOV and more | 1 GB |

> If a GIF exceeds 15 MB, the notebook automatically displays a warning with suggestions to reduce file size.

---

### Upload Limits

| Condition | Approximate Limit |
|---|---|
| Per file | ~2 GB |
| Multiple files | 2 GB × number of files |

---

### Save Options

| Destination | Description |
|---|---|
| Download locally | Saved via the browser download dialog |
| Save to Google Drive | Auto-copied to the specified path (includes mount step) |
| Both | Executes both options simultaneously |

---

### Tech Stack

- Runtime: Google Colab (Python 3.10+)
- Conversion Engine: FFmpeg
- UI: ipywidgets
- Storage: Google Drive API / local download

---

### License

MIT License. See [LICENSE](LICENSE) for details.

### Credits

- [FFmpeg](https://ffmpeg.org/) - Video conversion engine
- [Google Colab](https://colab.research.google.com/) - Free cloud runtime

### Support

- Bug reports: [Issues](https://github.com/hiroaki-com/colab-video-converter/issues)
- Questions & discussion: [Discussions](https://github.com/hiroaki-com/colab-video-converter/discussions)

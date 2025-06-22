<div align="center">

# 🎨 glyph
> **Convert images and video to ASCII art**

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/user/glyph)
[![License](https://img.shields.io/badge/license-MIT-blue)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Linux%20%7C%20macOS%20%7C%20Windows-lightgrey)](https://github.com/user/glyph)

</div>

---

## 📋 Table of Contents
- [🔧 Installation](#-installation)
- [⚡ Basic Usage](#-basic-usage)
- [🎯 Options](#-options)
- [📸 Image Examples](#-image-examples)
- [🎬 Video Examples](#-video-examples)
- [💡 Tips](#-tips)

---

## 🔧 Installation

### 📦 Homebrew (Recommended)
```bash
brew install glyph
```

### 🏗️ Build from Source
```bash
# Optimized build
zig build -Doptimize=ReleaseFast

# Direct execution
zig build run -Doptimize=ReleaseFast -- [options]
```

> **📍 Executable location:** `./zig-out/bin/glyph`

### 🎥 Video Dependencies
> **⚠️ Note:** Only needed for video processing (will be optional in the future)

<details>
<summary><strong>🐧 Linux</strong></summary>

```bash
sudo apt-get install libavutil-dev libavformat-dev libavcodec-dev libswscale-dev
```
</details>

<details>
<summary><strong>🍎 macOS</strong></summary>

```bash
brew install ffmpeg pkgconf
```
</details>

<details>
<summary><strong>🪟 Windows</strong></summary>

```bash
choco install ffmpeg-shared
```
</details>

---

## ⚡ Basic Usage

```bash
glyph -i <input_file> -o <output_file> [options]
```

> **💡 Tip:** To render directly on terminal, omit the `-o` option

---

## 🎯 Options

### 📋 Basic Options
| Option | Description | Default |
|--------|-------------|---------|
| `-h, --help` | Show help | - |
| `-i, --input <file>` | Input media file (local path/URL) | **Required** |
| `-o, --output <file>` | Output file (txt/img/vid) | **Required** |
| `-c, --color` | Use color ASCII characters | Disabled |
| `-n, --invert_color` | Invert color values | Disabled |
| `-s, --scale <float>` | Scale factor | `1.0` |
| `-e, --detect_edges` | Enable edge detection | Disabled |
| `-b, --brightness_boost <float>` | Adjust brightness | `1.0` |

### ⚙️ Advanced Options
| Option | Description | Default |
|--------|-------------|---------|
| `--full_characters` | Use all ASCII characters | Limited |
| `--ascii_chars <string>` | Custom characters | `" .:-=+*%@#"` |
| `--disable_sort` | Don't sort characters by size | Sorted |
| `--block_size <u8>` | Block size | `8` |
| `--threshold_disabled` | Disable threshold | Enabled |
| `--codec <string>` | Encoding codec | Auto-detect |
| `--keep_audio` | Preserve audio from input video | No audio |
| `--stretched` | Resize media to fit terminal window | Original size |
| `-f, --frame_rate` | Target frame rate for video output | Input FPS |

### 🔍 Edge Detection Filters
| Option | Description | Default |
|--------|-------------|---------|
| `--sigma1 <float>` | Sigma1 value for DoG filter | `0.3` |
| `--sigma2 <float>` | Sigma2 value for DoG filter | `1.0` |
| `--dither floydstein` | Dithering algorithm | Disabled |

---

## 📸 Image Examples

### 🔰 Basic Usage
```bash
# Basic image
glyph -i input.jpg -o output.png

# Text file output
glyph -i input.jpg -o output.txt
```

### 🌈 With Color
```bash
glyph -i input.png -o output.png -c
```

### 🎨 Advanced Configuration
```bash
# With edge detection, color and custom scale
glyph -i input.jpeg -o output.png -s 4 -e -c

# With brightness boost and URL input
glyph -i "https://w.wallhaven.cc/full/p9/wallhaven-p9gr2p.jpg" -o output.png -e -c -b 1.5
```

### 💻 Terminal Display
```bash
# Render directly on terminal
glyph -i "https://w.wallhaven.cc/full/p9/wallhaven-p9gr2p.jpg" -e -c -b 1.5
```

---

## 🎬 Video Examples

### 🎥 Basic Video
```bash
# Process video with codec and audio
glyph -i /path/to/video.mp4 -o ascii.mp4 --codec hevc_nvenc --keep_audio
```

### 📺 Terminal Playback
```bash
# Video stretched to fit terminal
glyph -i /path/to/video.mp4 --stretched -c
```

### ⚡ Encoding Configuration
```bash
# With custom ffmpeg options
glyph -i /path/to/video.mp4 -o ascii.mp4 -c --codec libx264 --keep_audio -- -preset fast -crf 20
```

---

## 💡 Tips

### 📝 Output Formats
- **Images:** Use `.png` for better compatibility
- **Text:** Use `.txt` for plain text files
- **Video:** Supports multiple formats

### 🖥️ Compatibility
- **Windows:** Use short arguments (`-i`, `-o`, etc.) recommended
- **URLs:** Only supported for images, not for videos

### 🎯 Recommendations
- Experiment with `-s` to adjust detail
- Combine `-e` and `-c` for better visual results
- Use `-b` to adjust contrast in dark images

---

<div align="center">

**✨ Enjoy creating ASCII art! ✨**

</div>
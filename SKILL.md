---
name: video-subtitles
description: Generate SRT subtitle files from video or audio using OpenAI Whisper. Free, local, no API key needed.
---

# Video Subtitles (Whisper)

Generate `.srt` subtitle files from any video or audio file using OpenAI Whisper. Runs locally — no API key, no cloud, no cost.

## Prerequisites

Install Whisper (one-time):

```bash
# macOS
brew install openai-whisper

# pip (any OS)
pip install openai-whisper
```

Requires `ffmpeg`:

```bash
# macOS
brew install ffmpeg

# Ubuntu/Debian
sudo apt install ffmpeg
```

## Usage

### Basic — Generate SRT from a video

```bash
whisper video.mp4 --model medium --output_format srt
```

Output: `video.srt` in the current directory.

### Specify language

```bash
whisper video.mp4 --model medium --output_format srt --language es
```

### Multiple output formats at once

```bash
whisper video.mp4 --model medium --output_format all
```

Produces `.srt`, `.vtt`, `.txt`, `.tsv`, and `.json`.

### Process multiple files

```bash
whisper *.mp4 --model medium --output_format srt
```

### Output to a specific directory

```bash
whisper video.mp4 --model medium --output_format srt --output_dir ./subtitles
```

## Models

| Model | Size | Speed | Accuracy | Best for |
|-------|------|-------|----------|----------|
| `tiny` | 39 MB | Fastest | Lower | Quick drafts, short clips |
| `base` | 74 MB | Fast | OK | Casual use |
| `small` | 244 MB | Medium | Good | Most videos |
| `medium` | 769 MB | Slower | Great | Recommended default |
| `large` | 1.5 GB | Slowest | Best | Professional use, difficult audio |

The model downloads automatically on first use.

## Tips

- **Start with `medium`** — best balance of speed and accuracy for most content
- **Use `small` for quick iterations** — review, fix, re-run if needed
- **Non-English content**: add `--language` flag for better accuracy
- **Long videos**: Whisper handles them fine, just takes proportionally longer
- **Edit the SRT after**: Whisper is good but not perfect — review timestamps and fix any errors

## SRT Format

```
1
00:00:01,000 --> 00:00:04,500
This is the first subtitle line.

2
00:00:05,000 --> 00:00:08,200
And this is the second one.
```

SRT files work in VLC, YouTube uploads, Premiere, Final Cut, DaVinci Resolve, and most video editors.

## Supported Input Formats

Any format ffmpeg can read: `.mp4`, `.mov`, `.avi`, `.mkv`, `.webm`, `.mp3`, `.wav`, `.ogg`, `.flac`, `.m4a`, and more.

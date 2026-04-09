# AI YouTube Shorts Generator User Manual

## Overview

This manual explains how to run the generator in day-to-day use.

## Basic Setup

1. Install Python
2. Install FFmpeg
3. Install ImageMagick
4. Create a virtual environment
5. Install Python dependencies
6. Add `OPENAI_API` to `.env`

## Commands

### Run interactively

```bash
python main.py
```

### Run with a YouTube URL

```bash
python main.py "https://youtu.be/VIDEO_ID"
```

### Run with a local video file

```bash
python main.py "C:\path\to\video.mp4"
```

### Run in auto-approve mode

```bash
python main.py --auto-approve "C:\path\to\video.mp4"
```

## Typical Workflow

1. provide a source video
2. wait for transcription
3. wait for highlight selection
4. confirm or auto-approve the selected segment
5. let the pipeline crop and subtitle the video
6. review the final MP4

## Input Recommendations

Best source material:
- clear spoken audio
- one main speaker
- educational or commentary content
- long-form video with coherent narrative segments

Less reliable source material:
- overlapping speakers
- heavy background noise
- music-dominant content
- very low-resolution recordings

## Output Review Checklist

Before publishing, check:
- subtitle timing
- subtitle readability
- crop framing
- clip start quality
- clip ending quality
- title relevance

## Troubleshooting

### No transcription output

Check:
- audio extraction succeeded
- whisper dependencies installed
- source audio is intelligible

### Highlight selection fails

Check:
- `.env` contains `OPENAI_API`
- network access is available
- the transcription text is not empty

### Subtitle render fails

Check:
- ImageMagick installation
- font availability
- local policy restrictions

### Final render fails

Check:
- FFmpeg installation
- source clip exists
- enough disk space is available

## Recommended Operating Style

For best results:
- use `--auto-approve` only for bulk testing
- keep manual review for client-facing outputs
- maintain a clean folder for source and output files

## Suggested Commercial Workflow

1. receive long-form source video
2. run generator
3. review final clip
4. export publishing copy
5. optionally run multiple times for several candidate clips

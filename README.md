# AI YouTube Shorts Generator

> Based on [AI-Youtube-Shorts-Generator](https://github.com/Anil-matcha/AI-Youtube-Shorts-Generator) by SamurAIGPT (MIT). The original copyright notice is kept in [LICENSE](LICENSE).

Generate vertical short-form videos from long-form source content.

This project takes a YouTube URL or local video file, transcribes the content, selects a highlight segment with an LLM, crops the video into a 9:16 layout, burns subtitles, and renders a Shorts-ready MP4.

## What It Does

- accepts YouTube URLs and local video files
- extracts audio from the source video
- transcribes speech with `faster-whisper`
- selects a highlight segment with OpenAI
- crops the clip into vertical format
- burns subtitles into the output
- renders a final short-form MP4

## Current Pipeline

```text
Input video
  -> audio extraction
  -> transcription
  -> highlight selection
  -> clip extraction
  -> vertical crop
  -> subtitle overlay
  -> final render
```

## Main Files

- `main.py`
  Main entrypoint and orchestration flow.
- `Components/YoutubeDownloader.py`
  Downloads YouTube input.
- `Components/Edit.py`
  Extracts audio and trims the source clip.
- `Components/Transcription.py`
  Runs speech-to-text.
- `Components/LanguageTasks.py`
  Chooses the highlight segment with an LLM.
- `Components/FaceCrop.py`
  Converts the clip to vertical framing.
- `Components/Subtitles.py`
  Renders captions into the video.

## Requirements

- Python 3.10+
- FFmpeg available on PATH
- ImageMagick available on PATH
- OpenAI API key

Recommended:
- GPU for faster transcription

## Installation

### 1. Clone

```bash
git clone https://github.com/inviy/AI-Youtube-Shorts-Generator.git
cd AI-Youtube-Shorts-Generator
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS/Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

GPU-oriented environment:

```bash
pip install -r requirements.txt
```

CPU-only environment:

```bash
pip install -r requirements-cpu.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```env
OPENAI_API=your_openai_api_key_here
```

## Usage

### Interactive

```bash
python main.py
```

### YouTube URL

```bash
python main.py "https://youtu.be/VIDEO_ID"
```

### Local MP4

```bash
python main.py "C:\path\to\video.mp4"
```

### Auto-approve mode

```bash
python main.py --auto-approve "https://youtu.be/VIDEO_ID"
```

## Output

The pipeline creates a final file named like:

```text
my-video-title_a1b2c3d4_short.mp4
```

It also uses temporary working files during processing and removes them when the run succeeds.

## Commercial Use Notes

This repository is most useful as a processing engine inside a larger content workflow.

Good use cases:
- long-form video to Shorts conversion
- podcast clipping
- educational content repurposing
- agency-assisted short-form production

Less suitable as-is:
- full self-serve SaaS without operational work
- fully autonomous publishing without review

## Project Docs

- `HANDOVER_MANUAL.md`
  For the next developer or operator taking over the project.
- `USER_MANUAL.md`
  For daily usage, setup, and operator workflows.

## Current Limitations

- quality depends heavily on transcription quality
- highlight selection depends on LLM prompting
- subtitle styling depends on local font and ImageMagick setup
- fully automated publishing is not included
- GPU setup is environment-sensitive

## Recommended Next Steps

1. stabilize CPU-only execution
2. add structured job output folders
3. expose the pipeline through a thin API
4. add batch processing and review tooling
5. package it as a commercial Shorts workflow

# AI YouTube Shorts Generator Handover Manual

## Purpose

This document is for the next developer or operator taking over the repository.

This project is a video-processing engine for converting long-form video into short-form vertical clips. It is not yet a complete product platform.

## Current State

What is working conceptually:
- source video input
- transcription
- highlight selection
- vertical conversion
- subtitle rendering
- final MP4 output

What still requires hands-on operation:
- environment setup
- dependency management
- API key configuration
- quality review
- operational packaging for commercial use

## Critical Flow

The project depends on the following order:

1. input video
2. audio extraction
3. transcription
4. highlight selection
5. clip extraction
6. vertical crop
7. subtitle render
8. final output render

If a run fails, first identify which of these stages broke.

## Important Files

- `main.py`
  Main orchestration logic.
- `Components/Edit.py`
  Audio extraction and clip trimming.
- `Components/Transcription.py`
  Speech-to-text execution.
- `Components/LanguageTasks.py`
  Highlight selection prompt and LLM call.
- `Components/FaceCrop.py`
  Vertical crop behavior.
- `Components/Subtitles.py`
  Subtitle rendering.
- `requirements.txt`
  Main dependency set.
- `requirements-cpu.txt`
  CPU-oriented dependency set.

## Required External Dependencies

- FFmpeg
- ImageMagick
- OpenAI API key

Without these, the pipeline is incomplete.

## Environment Notes

This project is sensitive to local environment issues.

Common trouble spots:
- FFmpeg missing from PATH
- ImageMagick security policy blocking subtitle operations
- GPU/CUDA mismatch
- missing fonts
- OpenAI API key missing or invalid

## Operational Recommendation

Treat this repository as an engine, not a final product.

Best next use:
- wrap it with a thin service layer
- run it on approved input only
- keep a manual review step before publishing

Do not assume this repo is ready for full unattended production publishing.

## Quality Risks

- highlight selection may choose weak clips
- transcription errors can degrade captions
- face cropping may not fit every format well
- subtitle layout may require template tuning

## Commercialization Guidance

Use this code to power:
- long-form to Shorts conversion service
- agency-assisted video repurposing
- vertical-specific clipping workflows

Avoid positioning it immediately as:
- a full autonomous content factory
- a fully reliable self-serve product without QA

## Handover Checklist

Before handing over the project, confirm:
- environment setup is documented
- API key handling is known
- system dependencies are installed
- one successful end-to-end run has been demonstrated
- output location and naming are understood
- common failure points have been explained

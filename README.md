# <img src="https://upload.wikimedia.org/wikipedia/commons/b/b8/YouTube_Logo_2017.svg" alt="YouTube Logo" width="35"/> YouTube Transcript Summarizer


This project fetches and summarizes YouTube video transcripts related to Optical Character Recognition (OCR) using `youtube_transcript_api` and `transformers`.

## Features

### 1. Video ID Extraction
Extracts the video ID from a YouTube URL.

```python
def extract_video_id(url):
    match = re.search(r"v=([a-zA-Z0-9_-]+)", url)
    return match.group(1) if match else None
```

### 2. Transcript Retrieval
Fetches the English transcript of a YouTube video.

```python
transcript_data = YouTubeTranscriptApi.get_transcript(video_id, languages=['en'])
text = " ".join([entry['text'] for entry in transcript_data])
```

### 3. Bullet-Point Summarization
Summarizes the transcript into key points using an NLP model.

```python
summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
summary = summarizer(text, max_length=150, min_length=50, do_sample=False)
```

## Processed Videos
- **OCR Explained** (ID: gBSh9JI28UQ): Introduction to OCR.
- **Tesseract OCR in Python** (ID: lcB0LYNp0oI): Using Tesseract.

## Requirements
```bash
pip install youtube_transcript_api==1.1.0 transformers torch
```

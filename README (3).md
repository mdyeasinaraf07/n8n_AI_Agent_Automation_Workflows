# YouTube Video Automation Pipeline

> Turns a single topic into a finished video, from AI-written script to automatic YouTube upload.

![YouTube Video Automation Pipeline workflow](../images/youtube-video-automation-pipeline.png)

## Overview

| | |
|---|---|
| **Category** | Content Automation |
| **Key technologies** | n8n, OpenAI, Groq, Pixabay API, JSON2Video, YouTube API |
| **Type** | Personal project |
| **Workflow file** | [YouTube Video Automation Pipeline.json](../YouTube%20Video%20Automation%20Pipeline.json) |

## Business Problem

Publishing video content consistently takes hours per video for scripting, sourcing visuals, editing and uploading. For small teams and creators, that effort does not scale.

## Solution

One workflow handles the entire chain. Given a topic, it writes the script with AI, plans the scenes, collects matching visuals, renders the video through a video-generation API and uploads the finished file to YouTube.

## How It Works

1. The workflow starts from a topic input.
2. An AI agent (OpenAI) writes the script.
3. A JavaScript step and an API request prepare the generated content.
4. A second AI agent (Groq) plans the scenes and search terms.
5. The workflow loops over the scenes and fetches matching visuals from the Pixabay API.
6. The scenes are sent to the JSON2Video API to render the video.
7. The workflow waits, checks the render status and retrieves the finished video URL.
8. The video is uploaded to YouTube automatically.

## Business Value

- One topic in, one finished video out, with no manual editing step.
- Consistent output at a steady pace.
- Modular design: script, visuals and rendering can each be swapped independently.

## Tech Stack

| Component | Role |
|---|---|
| n8n | Pipeline orchestration, looping and waiting |
| OpenAI | Script generation |
| Groq | Scene planning |
| Pixabay API | Stock visuals |
| JSON2Video API | Video rendering |
| YouTube API | Automated upload |

## Workflow Source

The full n8n workflow is in this repository: [YouTube Video Automation Pipeline.json](../YouTube%20Video%20Automation%20Pipeline.json). Click the file to read the workflow code.

## Setup

1. In n8n, choose Import from File and select the workflow JSON above.
2. Create your own credentials for each node that needs one:
   - OpenAI API key
   - Groq API key
   - Pixabay API key
   - JSON2Video API key
   - Google API key for the Generative Language request
   - YouTube OAuth2
3. Replace placeholder values (marked `YOUR_...`) with your own.
4. Run the workflow manually with a test topic and review the output before enabling automatic upload.
5. Run a test execution, then activate the workflow.

---

Built by [Md Yeasin Arafat](https://github.com/mdyeasinaraf07) | [LinkedIn](https://www.linkedin.com/in/md-yeasin-arafat-848387254) | [Portfolio](https://mdyeasinarafat-portfolio.lovable.app)

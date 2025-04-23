# Project Documentation: YouTube Summarizer
## Overview
This project is a web application that allows users to submit a YouTube video URL and receive a summarized transcript of the video. The application is built using FastAPI and serves both the user interface and the summarization functionality from a single deployment.

## Features
* YouTube Transcript Extraction: Extracts the transcript of a YouTube video using the youtube_transcript_api.
* Text Summarization: Summarizes the transcript using a pre-trained model from the transformers library.
* User Interface: A simple HTML page for submitting YouTube URLs and displaying the summarized transcript.
* Deployment: The application is deployed as a Docker container on an AWS EC2 instance.

## Project Structure
.Dockerignore
.gitignore
Dockerfile
main.py
requirements.txt
deploy-to-ec2.yml
static/
  index.html

## Key Files
* main.py: Implements the application logic and serves the user interface.
* static/index.html: The HTML page for interacting with the application.
* Dockerfile: Defines the Docker image for the application.
* requirements.txt: Lists Python dependencies.
* deploy-to-ec2.yml: AWS CloudFormation template for deploying the application on an EC2 instance.

## Installation and Setup
Prerequisites
* Python 3.10+
* Docker
* AWS CLI (for deployment)

### Local Setup
1. Clone the repository
<pre>
```bash
    git clone <repository-url>
    cd <repository-folder>
</pre>

2. Install dependencies
<pre>
```bash
    pip install -r requirements.txt
</pre>

3. Run the application locally:
<pre>
```bash
    uvicorn main:app --host 0.0.0.0 --port 8000
</pre>
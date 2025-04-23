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
  git clone `repository-url`
  cd `repository-folder`
</pre>

2. Install dependencies
<pre>
  pip install -r requirements.txt
</pre>

3. Run the application locally:
<pre>
  uvicorn main:app --host 0.0.0.0 --port 8000
</pre>
4. Access the application in your browser at `http://localhost:8000`

## Deployment
### Deployment on EC2
1. Prepare AWS Environment:
  * Ensure you have an EC2 KeyPair for SSH access.
  * Configure your AWS CLI with appropriate credentials.
2. Deploy Using CloudFormation:
  * Use the deploy-to-ec2.yml template to deploy the application:
  <pre>
    aws cloudformation create-stack --stack-name yt-summarizer-stack \
    --template-body file://deploy-to-ec2.yml \
    --parameters ParameterKey=KeyName,ParameterValue=`YourKeyPairName`
  </pre>
  * Replace `YourKeyPairName` with the name of your EC2 KeyPair.

3. Access the Application:

  * Once the stack is created, retrieve the public IP or DNS of the EC2 instance from the CloudFormation outputs.
  * Access the application in your browser at http://`PublicIP`.

## How to Use
1. Open the application in your browser.
2. Enter the YouTube video URL in the input field.
3. Click the "Send" button.
4. The summarized transcript will appear below the input field.

## Dependencies
* fastapi
* uvicorn
* torch
* transformers
* youtube_transcript_api

## Future Improvements
1. Add error messages for invalid YouTube URLs.
2. Improve the summarization model for better accuracy.
3. Enhance the user interface for a more modern look.
4. Add support for multiple languages in transcript summarization.
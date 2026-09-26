# BITNBUILD-hakathon

# AI-Powered Interview Bot

An AI-powered interview platform that conducts personalized interviews based on a candidate's resume and target role, adapts questions according to candidate responses, provides interview feedback, and records neutral interview-integrity observations.

## Problem

Traditional initial interviews can be time-consuming and inconsistent. Candidates also have limited access to realistic interview practice and structured feedback.

The goal of this project is to create an AI-powered interview experience that can:

- Understand a candidate's resume
- Generate personalized interview questions
- Conduct an interactive interview
- Adapt questions based on responses
- Evaluate interview performance
- Provide a structured final report
- Record attention and integrity-related observations

## Features

### 1. Resume-Based Interview

The candidate uploads a resume and selects a target job role.

The system uses the candidate's resume and role to generate personalized interview questions instead of relying only on a fixed question list.

### 2. Adaptive Interviewing

The AI evaluates the candidate's responses and generates the next question based on the previous answer.

The interview can adjust its direction and difficulty depending on the candidate's responses.

### 3. AI Evaluation

After the interview, the system generates a structured report containing:

- Overall score
- Strengths
- Gaps / areas to improve
- Technical evaluation
- Communication observations
- Interview summary

The report is intended to support human decision-making and should not be treated as a final hiring decision by itself.

### 4. Voice Interaction

The interview supports browser-based speech features:

- Speech recognition for candidate answers
- Speech synthesis for AI questions

A text-based fallback is available if browser speech functionality is unavailable.

The speech-transcription system also includes handling to prevent repeated words caused by continuously changing interim speech-recognition results.

### 5. Interview Integrity Monitoring

The system uses the candidate's camera to record neutral attention-related observations.

Current observations include:

- Face not detected
- Multiple faces detected
- Attention-related observations

The system uses confirmation thresholds and cooldowns to reduce noisy or repeated alerts.

These observations are not treated as proof of cheating or wrongdoing.

### 6. Local AI

The main interview intelligence runs locally using:

- Ollama
- Qwen3 8B

Qwen3 is used for:

- Resume understanding
- Candidate profile extraction
- Personalized question generation
- Answer evaluation
- Adaptive questioning
- Final interview report generation

## Technology Stack

### Frontend

- React
- Vite
- JavaScript / JSX
- CSS
- Browser Web Speech API
- Browser camera and microphone APIs

### Backend

- Node.js
- Express.js
- REST APIs

### AI

- Ollama
- Qwen3 8B

### Computer Vision

- face-api.js
- Browser-side face detection
- Multi-face detection
- Attention-related observations

### Database

- Supabase (optional)

The application can also run without Supabase using in-memory storage/configuration when database credentials are not provided.

## Architecture

```text
                    Candidate
                        |
                        v
                +---------------+
                |   Frontend    |
                | React / Vite  |
                +-------+-------+
                        |
                        v
                +---------------+
                |    Backend    |
                | Node / Express|
                +-------+-------+
                        |
             +----------+----------+
             |                     |
             v                     v
      +-------------+       +-------------+
      |  Ollama     |       |  Supabase   |
      | Qwen3 8B    |       |  Database   |
      +-------------+       +-------------+
             |
             v
     Interview Intelligence

Camera
  |
  v
face-api.js
  |
  v
Integrity Observations

Microphone
  |
  v
Browser Speech Recognition
  |
  v
Candidate Transcript

AI Question
  |
  v
Browser Speech Synthesis
  |
  v
Candidate

<div align="center">

<img src="assets/recall-logo.svg" width="76" height="76" alt="Recall" />

# Recall

**The memory layer for dementia care.**
Turns photos, voices, and family stories into a living graph your loved one can recall in seconds not hours.

Built on [Cognee](https://github.com/topoteretes/cognee)

</div>

---

## About Recall

55 million people live with dementia, and most slowly lose access to their own life story. That story is not gone. It sits scattered across family photos, voice notes, and the memories of the people who love them.

Recall gives it a home. Caregivers and family upload photos, voice notes, videos, and written stories. Cognee weaves them into a connected memory graph. When a loved one asks "who is Mary?" or "tell me about our holiday", the right memory surfaces in their own words, with the real photo or video attached. Every answer is grounded in something a family member actually uploaded.

## How It Works

1. **Capture** a moment. Add a photo, record a voice note, upload a video, or write a story. Family can contribute from anywhere with an invite code.
2. **Cognee connects it.** Each memory is transcribed, then woven into a living graph that links the people, places, and moments that belong together.
3. **Recall, gently.** Your loved one asks a question, and the right memory comes back in warm, plain language with its photo or video.

## The Memory Pipeline

Every upload passes through the same path:

1. **Capture** the photo, voice note, video, or story from the whole family
2. **Store** the media on Cloudinary, served over a CDN
3. **Transcribe** voice and video into searchable text with Whisper
4. **Graph** the people, places, and moments into one connected memory graph with Cognee
5. **Enrich** the graph so the same person and place link across many memories
6. **Recall** the right nodes for a question and shape them into a gentle answer

## Features

- **Multi-format capture:** photos, voice notes, videos, and written stories in one place
- **Automatic transcription:** every voice and video becomes searchable text with Whisper
- **Memory graph:** Cognee links people, places, and moments into one connected graph
- **Natural-language recall:** ask a question, get a warm answer with the real photo or video inline
- **Memory showcase:** a cinematic slideshow plus voice and video galleries of real uploads
- **Care circle:** invite family with a code, with roles for caregivers, contributors, and patients
- **Patient-friendly view:** large type, calm layout, one question box, no menus
- **Private access:** invite-only, no open registration

## Quick Start

**Prerequisites:** Docker, Node.js 18+, and pnpm.

```bash
# Backend (FastAPI, Postgres, Redis, Celery)
cd backend
cp .env.example .env      # fill in the keys under Setup
docker compose up --build

# Frontend (React, Vite, TailwindCSS)
cd frontend
cp .env.example .env.local  # fill in the keys under Setup
pnpm install
pnpm dev
```

Backend runs on `http://localhost:8001`, frontend on `http://localhost:5173`.

## Setup

`backend/.env`:

```env
DATABASE_URL=postgresql://postgres:postgres@db:5432/recall
REDIS_URL=redis://redis:6379/0
OPENAI_API_KEY=                 # Whisper transcription and answer synthesis
LLM_API_KEY=                    # LLM key Cognee uses (reuse the OpenAI key)
CLOUDINARY_CLOUD_NAME=          # media storage
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
FIREBASE_SERVICE_ACCOUNT_JSON=  # Firebase Admin service account, verifies auth tokens
COGNEE_VECTOR_DB_URL=postgresql://postgres:postgres@db:5432/recall
COGNEE_GRAPH_DB_URL=postgresql://postgres:postgres@db:5432/recall
```

`frontend/.env.local`:

```env
VITE_API_URL=http://localhost:8001
VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
```

## Tech Stack

| Layer | Technology |
|---|---|
| Memory | Cognee (open-source graph-vector memory) |
| Database | PostgreSQL + pgvector |
| Backend | FastAPI (Python) |
| Background jobs | Celery + Redis |
| Transcription | OpenAI Whisper |
| Answer synthesis | OpenAI GPT-4o-mini |
| Media storage | Cloudinary |
| Auth | Firebase |
| Frontend | React 19 + Vite + TypeScript |
| Styling | Tailwind CSS v4 |
| State | TanStack Query + Zustand |
| Motion | GSAP + Three.js |

---

## Recall - Deployed on AWS Cloud

## AWS Infrastructure Plan
![AWS Infrastructure Plan](./deployend/documentation/images/recall.png)

## Tools and Services Used

* **Linux:** Fedora Workstation 44 (local) and Ubuntu 22.04+ (AWS EC2)
* **Scripting:** Bash Scripting & Python
* **AWS Services:** EC2, IAM, Cloudfront, ACM, Route53, VPC, ALB, S3
* **Cloud Automation:** Terraform
* **Server Automation:** Ansible
* **Others:** Nginx, Docker

## Getting Started

1. Rename the `example_recall_config.json` file to `recall_config.json`.
2. Fill in the required configuration fields within the new file.
3. Verify you have set up all prerequisites outlined in the [How to Run Guide](./deployend/documentation/how_to_run.md).
4. Once everything is configured, run the main script:

```bash
python main.py
```
The script will handle the rest of the deployment!

---

<div align="center">

 Made with Cognee 🧠

</div>

# Sentiment Analysis App

## Overview
This is a full-stack sentiment analysis application using **ReactJS (frontend)** and **FastAPI (backend)**. The app allows users to enter a movie review, and it predicts whether the sentiment is **Positive, Neutral, or Negative** using Cohere's AI model.

## Tech Stack
- **Frontend:** ReactJS
- **Backend:** FastAPI (Python)
- **Containerization:** Docker & Docker Compose
- **Deployment:** Cloud VM (AWS, GCP, or Azure)

## Setup Instructions
### 1. Clone the Repository
```
git clone https://github.com/your-repo/sentiment-analysis-app.git
cd sentiment-analysis-app
```

### 2. Build & Run with Docker Compose
```
docker-compose up --build
```
The frontend will be available at **http://localhost:3000**, and the backend API will be running at **http://localhost:8000**.

## API Endpoints
- `POST /classify`: Accepts a review and returns its predicted sentiment.

## Deployment
To deploy on a cloud VM, follow these steps:
1. Install Docker & Docker Compose.
2. Clone the repository.
3. Run `docker-compose up --build`.

## License
This project is open-source and available under the MIT License.
`

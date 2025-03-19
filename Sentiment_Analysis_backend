from fastapi import FastAPI, HTTPException
import cohere
from pydantic import BaseModel
import os
from dotenv import load_dotenv

# Load environment variables
load_dotenv()
COHERE_API_KEY = os.getenv("COHERE_API_KEY")

# Initialize Cohere client
co = cohere.Client(COHERE_API_KEY)

# Initialize FastAPI app
app = FastAPI()

# Request model
class ReviewRequest(BaseModel):
    review: str

@app.post("/classify")
async def classify_review(request: ReviewRequest):
    try:
        response = co.classify(
            model='large',
            inputs=[request.review],
            examples=[
                cohere.ClassifyExample("I absolutely loved this movie, it was fantastic!", "Positive"),
                cohere.ClassifyExample("The plot was dull and boring, I didn't enjoy it at all.", "Negative"),
                cohere.ClassifyExample("The movie was okay, but nothing special.", "Neutral"),
                cohere.ClassifyExample("Great acting and direction, but the pacing was off.", "Positive"),
                cohere.ClassifyExample("I hated the ending, it ruined the whole experience.", "Negative"),
                cohere.ClassifyExample("It was just average, nothing memorable.", "Neutral")
            ]
        )
        return {"review": request.review, "sentiment": response.classifications[0].prediction}
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

# Health check endpoint
@app.get("/")
async def root():
    return {"message": "FastAPI Cohere Sentiment Classifier is running!"}

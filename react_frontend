import { useState } from "react";
import axios from "axios";

export default function SentimentApp() {
  const [review, setReview] = useState("");
  const [sentiment, setSentiment] = useState(null);
  const [loading, setLoading] = useState(false);

  const handleSubmit = async () => {
    if (!review.trim()) return;
    setLoading(true);
    try {
      const response = await axios.post("http://localhost:8000/classify", { review });
      setSentiment(response.data.sentiment);
    } catch (error) {
      console.error("Error fetching sentiment:", error);
      setSentiment("Error analyzing sentiment");
    }
    setLoading(false);
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100 p-6">
      <h1 className="text-2xl font-bold mb-4">Movie Review Sentiment Analyzer</h1>
      <textarea
        className="w-96 h-24 p-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
        placeholder="Enter your movie review..."
        value={review}
        onChange={(e) => setReview(e.target.value)}
      ></textarea>
      <button
        className="mt-4 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600"
        onClick={handleSubmit}
        disabled={loading}
      >
        {loading ? "Analyzing..." : "Analyze Sentiment"}
      </button>
      {sentiment && (
        <p className="mt-4 text-xl font-semibold">Sentiment: {sentiment}</p>
      )}
    </div>
  );
}

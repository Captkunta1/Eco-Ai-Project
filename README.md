# Eco-Ai-Project
/* Project: EcoFlow - AI-Powered Sustainability Tracker */

// Backend - server.js (Node.js + Express)
const express = require("express");
const cors = require("cors");
const app = express();
const PORT = process.env.PORT || 5000;

app.use(cors());
app.use(express.json());

app.get("/api/health", (req, res) => {
    res.send({ status: "Server is running" });
});

app.listen(PORT, () => console.log(`Server running on port ${PORT}`));

// Frontend - App.jsx (React.js)
import React, { useState, useEffect } from "react";
import axios from "axios";

function App() {
    const [message, setMessage] = useState("Loading...");

    useEffect(() => {
        axios.get("http://localhost:5000/api/health")
            .then(response => setMessage(response.data.status))
            .catch(error => setMessage("Error loading API"));
    }, []);

    return (
        <div className="container">
            <h1>EcoFlow Sustainability Tracker</h1>
            <p>{message}</p>
        </div>
    );
}

export default App;

// AI - eco_ai.py (Python + OpenAI API example)
import openai

def get_sustainability_advice():
    openai.api_key = "your-api-key-here"
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "system", "content": "Provide sustainability tips."}]
    )
    return response["choices"][0]["message"]["content"]

if __name__ == "__main__":
    print(get_sustainability_advice())

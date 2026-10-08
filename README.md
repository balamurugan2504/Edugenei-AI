# EduGenie: Google Gemini Powered Learning Assistant

**BCA Final Year Project**

EduGenie is a full-stack learning assistant that uses Google's Gemini API to help students understand subjects, summarize notes, generate quizzes, create flashcards and prepare study plans.

## 1. Main Features

- AI Tutor chat interface
- Explain any topic in simple language
- Summarize study material
- Generate multiple-choice quizzes
- Generate revision flashcards
- Generate a 7-day study plan
- Responsive dashboard for desktop and mobile
- Backend API keeps the Gemini API key out of the browser
- Demo mode works even before a Gemini key is configured
- Health/status endpoint for testing

## 2. Technology Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript |
| Backend | Node.js + Express |
| AI | Google Gemini API |
| SDK | `@google/genai` |
| Configuration | dotenv |
| API support | REST/JSON |

## 3. Project Structure

```text
EduGenie/
├── public/
│   ├── index.html
│   ├── styles.css
│   └── app.js
├── server/
│   └── index.js
├── .env.example
├── .gitignore
├── package.json
└── README.md
```

## 4. Requirements

Install:

- Node.js 18+ (Node.js 22+ recommended)
- A Gemini API key for live AI responses

> This version uses Node.js built-in HTTP/fetch APIs, so there are no third-party npm dependencies to install.

## 5. Installation

Open the project folder in VS Code terminal:

Copy `.env.example` to `.env`.

### Demo mode

The default `.env.example` uses:

```env
DEMO_MODE=true
```

This lets you run and demonstrate the UI without an API key. The demo responses are local placeholders.

### Live Gemini mode

Create a Gemini API key through Google AI Studio, then edit `.env`:

```env
PORT=5000
GEMINI_API_KEY=YOUR_API_KEY_HERE
GEMINI_MODEL=gemini-3.8-flash
DEMO_MODE=false
```

Do not share the key, commit `.env`, or place the key in frontend JavaScript.

## 6. Run the Project

```bash
npm start
```

Open:

```text
http://localhost:5000
```

For development with automatic Node server restart:

```bash
npm run dev
```

## 7. Test the Backend

Open this in a browser:

```text
http://localhost:5000/api/health
```

A successful response looks similar to:

```json
{
  "ok": true,
  "app": "EduGenie",
  "aiProvider": "Demo mode",
  "model": "local-demo",
  "demoMode": true
}
```

## 8. How the Project Works

1. The student opens the EduGenie dashboard.
2. The student selects Explain, Summarize, Quiz, Flashcards or Study Plan.
3. The browser sends the request to `/api/ask`.
4. Express validates the request.
5. In live mode, the server sends the prompt to Google's Gemini API using `@google/genai`.
6. Gemini returns generated text.
7. The server sends JSON back to the browser.
8. The frontend displays the answer in the chat panel.

## 9. Security Notes

The Gemini API key belongs on the server in `.env`. Never put the key in `public/app.js` or any other browser-delivered file. Never upload `.env` to GitHub.

## 10. Suggested Final-Year Report Chapters

1. Introduction
2. Problem Statement
3. Objectives
4. Existing System
5. Proposed System
6. System Requirements
7. System Architecture
8. Module Description
9. Database/API Design
10. Implementation
11. Testing
12. Screenshots
13. Advantages and Limitations
14. Future Enhancements
15. Conclusion
16. References

## 11. Suggested Modules

### Module 1 — User Interface
Dashboard, navigation, responsive design and chat workspace.

### Module 2 — AI Tutor
Natural-language question answering through Gemini.

### Module 3 — Study Tools
Explanation, summarization, quizzes, flashcards and study plans.

### Module 4 — Backend API
Express routes for health checks and AI requests.

### Module 5 — Configuration
Environment variables and safe API-key handling.

## 12. Testing Checklist

- [ ] `npm install` completes without errors
- [ ] `npm start` starts the server
- [ ] Dashboard loads at port 5000
- [ ] `/api/health` returns `ok: true`
- [ ] Demo mode returns an answer
- [ ] Live mode returns a Gemini answer after a valid API key is configured
- [ ] Explain tool works
- [ ] Summarize tool works
- [ ] Quiz tool works
- [ ] Flashcards tool works
- [ ] Study plan tool works
- [ ] Chat can be cleared
- [ ] Mobile layout is usable

## 13. Viva Explanation — Short Version

**What is EduGenie?**
EduGenie is a web-based AI learning assistant designed for college students. It uses Google's Gemini generative AI to provide explanations and study tools.

**Why Gemini?**
Gemini provides natural-language generation that can be integrated into an application through an API.

**Why use a backend?**
The backend keeps the API key private and provides a controlled API between the frontend and Gemini.

**What is the main benefit?**
A student can use one interface to ask questions and create different types of study material instead of using separate tools.

## 14. Reference

Google AI for Developers — Gemini API documentation: https://ai.google.dev/gemini-api/docs

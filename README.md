# PrepMate AI — AI-Powered Job Interview Preparation Platform

A full-stack MERN application that helps candidates prepare for job interviews using Google Gemini AI. Upload your resume, paste the job description, and get a personalized interview report with technical questions, behavioral questions, skill gap analysis, a preparation plan, and an AI-generated tailored resume PDF — all in one place.

## Features

- **AI Interview Report** — Generates a detailed report based on your resume, self-description, and job description using Google Gemini
- **Match Score** — Shows how well your profile matches the job (0–100)
- **Technical Questions** — Role-specific questions with interviewer intent and suggested answers
- **Behavioral Questions** — Soft-skill questions with intent and how to answer them
- **Skill Gap Analysis** — Identifies missing skills with severity (low / medium / high)
- **Day-wise Preparation Plan** — Structured plan with daily focus areas and tasks
- **AI Resume PDF Generator** — Generates a tailored, ATS-friendly resume PDF based on your profile and the job description
- **JWT Authentication** — Secure login/register with token blacklisting on logout
- **Report History** — View all your previously generated interview reports


## Tech Stack

**Frontend**
- React.js (Vite)
- React Router v7
- SCSS
- Context API

**Backend**
- Node.js + Express.js
- MongoDB + Mongoose
- JWT Authentication
- Multer (PDF upload)
- pdf-parse (Resume text extraction)
- Puppeteer (PDF generation)

**AI**
- Google Gemini API (`@google/genai`)
- Zod + zod-to-json-schema (Structured AI responses)



## Project Structure

```
interview-ai/
│
├── Backend/
│   ├── src/
│   │   ├── config/
│   │   │   └── database.js
│   │   ├── controllers/
│   │   │   ├── auth.controller.js
│   │   │   └── interview.controller.js
│   │   ├── middlewares/
│   │   │   ├── auth.middleware.js
│   │   │   └── file.middleware.js
│   │   ├── models/
│   │   │   ├── user.model.js
│   │   │   ├── blacklist.model.js
│   │   │   └── interviewReport.model.js
│   │   ├── routes/
│   │   │   ├── auth.routes.js
│   │   │   └── interview.routes.js
│   │   ├── services/
│   │   │   └── ai.service.js
│   │   └── app.js
│   └── server.js
│
└── Frontend/
    └── src/
        ├── features/
        │   ├── auth/
        │   └── interview/
        ├── App.jsx
        ├── app.routes.jsx
        └── main.jsx
```


## Getting Started Locally

### Prerequisites
- Node.js v18+
- MongoDB Atlas account
- Google Gemini API key ([aistudio.google.com](https://aistudio.google.com))



### Backend Setup

```bash
cd Backend
npm install
```

Create a `.env` file inside the `Backend` folder:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
GOOGLE_GENAI_API_KEY=your_gemini_api_key
```

Start the backend:

```bash
node server.js
```

Server runs on `http://localhost:3000`



### Frontend Setup

```bash
cd Frontend
npm install
```

Create a `.env` file inside the `Frontend` folder:

```env
VITE_API_URL=http://localhost:3000
```

Start the frontend:

```bash
npm run dev
```

Frontend runs on `http://localhost:5173`



## API Endpoints

### Auth Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| POST | `/api/auth/register` | Register new user | Public |
| POST | `/api/auth/login` | Login user | Public |
| GET | `/api/auth/logout` | Logout and blacklist token | Public |
| GET | `/api/auth/get-me` | Get logged-in user details | Private |

### Interview Routes

| Method | Endpoint | Description | Access |
|--------|----------|-------------|--------|
| POST | `/api/interview/` | Generate interview report (upload resume PDF) | Private |
| GET | `/api/interview/` | Get all reports of logged-in user | Private |
| GET | `/api/interview/report/:interviewId` | Get specific report by ID | Private |
| POST | `/api/interview/resume/pdf/:interviewReportId` | Generate tailored resume PDF | Private |


## How It Works

1. User registers/logs in
2. Uploads resume as PDF + enters self-description and job description
3. Backend extracts text from PDF using `pdf-parse`
4. Sends all data to Google Gemini with a structured Zod schema
5. Gemini returns a JSON report with match score, questions, skill gaps, and preparation plan
6. Report is saved to MongoDB and displayed on the frontend
7. User can also generate a tailored resume PDF using Puppeteer

## Future Improvements
1. Voice-based interview interaction
2. Performance analytics dashboard
3. Emotion detection (CV integration)
4. Multi-language support
5. Mobile responsiveness
   
## Learning Outcomes
1. Built a full-stack AI-integrated system
2. Understood API design and frontend-backend communication
3. Implemented authentication and secure routing
4. Integrated LLM APIs for real-time responses
5. Managed file uploads and dynamic data flow

## Author

**Jyotishankar Sahoo**  
B.Tech ECE — NIT Surat (SVNIT)  
[LinkedIn](https://linkedin.com/in/jyotishankar-sahoo-7a03b3257)
If you like this project, consider giving it a ⭐ on GitHub!

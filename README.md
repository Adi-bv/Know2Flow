# Know2Flow

Know2Flow is a full-stack web app focused on skill-based connection and communication. Users can sign up, match with other users, chat in real time, make video calls, view leaderboards, and attempt personalized weekly challenges.


## Features (Brief)
- User authentication (signup/login) with Firebase.
- Match discovery and profile browsing.
- Real-time chat with Socket.IO.
- Video calling with Agora.
- Live caption + translation flow for calls.
- Weekly personalized challenge generation and scoring.
- Global leaderboard.

## Tech Stack
- Frontend: React + Vite
- Backend: Node.js + Express
- Database/Auth: Firebase (Firestore + Auth)
- Real-time: Socket.IO
- Video/RTC + STT: Agora
- AI/Challenge generation: OpenRouter-compatible API key (`CHALLENGE_GEMINI_API_KEY`)

## Project Structure
```text
Know2Flow/
  backend/
  frontend/
```

## Important First Step
Before installing anything, **open the `requirements/`** and install all software listed there.

## Environment Variables
Create the following env files before running.

### Backend `.env`
Create: `backend/.env`

```env
# Firebase Admin SDK (service account style)
FIREBASE_TYPE=service_account
FIREBASE_PROJECT_ID=your_project_id
FIREBASE_PRIVATE_KEY_ID=your_private_key_id
FIREBASE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\n...\n-----END PRIVATE KEY-----\n"
FIREBASE_CLIENT_EMAIL=your_client_email
FIREBASE_CLIENT_ID=your_client_id
FIREBASE_AUTH_URI=https://accounts.google.com/o/oauth2/auth
FIREBASE_TOKEN_URI=https://oauth2.googleapis.com/token
FIREBASE_AUTH_PROVIDER_CERT_URL=https://www.googleapis.com/oauth2/v1/certs
FIREBASE_CLIENT_CERT_URL=your_client_cert_url

# Firebase Web API key (used in login/signup route)
FIREBASE_API_KEY=your_firebase_web_api_key

# Agora
AGORA_APP_ID=your_agora_app_id
AGORA_APP_CERTIFICATE=your_agora_app_certificate
AGORA_CUSTOMER_ID=your_agora_customer_id
AGORA_CUSTOMER_SECRET=your_agora_customer_secret

# Challenge/AI
CHALLENGE_GEMINI_API_KEY=your_openrouter_or_model_provider_key

# Optional (used in pinecone.js if that module is wired in future)
PINECONE_API_KEY=your_pinecone_api_key
PINECONE_INDEX_NAME=users-skills-2
GEMINI_API_KEY=your_gemini_api_key

# App mode
NODE_ENV=development
```

### Frontend `.env`
Create: `frontend/.env`

```env
VITE_FIREBASE_API_KEY=your_firebase_api_key
VITE_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
VITE_FIREBASE_PROJECT_ID=your_project_id
VITE_FIREBASE_STORAGE_BUCKET=your_project.appspot.com
VITE_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
VITE_FIREBASE_APP_ID=your_app_id
VITE_AGORA_APP_ID=your_agora_app_id
```

## Setup on a New PC (Start to End)
1. Install all required software from `requirements/` first.
2. Clone this repository.
3. Open two terminals at project root (`Know2Flow/`).
4. In terminal 1, install backend dependencies:
   ```bash
   cd backend
   npm install
   ```
5. In terminal 2, install frontend dependencies:
   ```bash
   cd frontend
   npm install
   ```
6. Create env files exactly as shown above:
   - `backend/.env`
   - `frontend/.env`
7. Start backend (terminal 1):
   ```bash
   cd backend
   npm run dev
   ```
   Backend runs on: `http://localhost:5000`
8. Start frontend (terminal 2):
   ```bash
   cd frontend
   npm run dev
   ```
   Frontend runs on: `http://localhost:5173`
9. Open `http://localhost:5173` in browser.
10. Sign up/login and test core flows:
    - profile + matches
    - chat
    - video call
    - challenge + leaderboard

## Useful Scripts
### Backend
- `npm run dev` -> start with nodemon

### Frontend
- `npm run dev` -> start Vite dev server

## Notes
- CORS is currently configured for `http://localhost:5173` in backend.
- Backend and frontend API/socket URLs are hardcoded to `http://localhost:5000` in current frontend code.
- If you change ports/domains, update both backend CORS and frontend fetch/socket URLs.

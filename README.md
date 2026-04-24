# Mood & Munch — Context-Aware Food Recommendation App

Mood & Munch is a smart food recommendation application that analyzes a user's real-time physical, emotional, and environmental state to recommend nutritionally appropriate meals from multiple global cuisines.

## Architecture

This is a monorepo containing three microservices:

1.  **Frontend (`client/`)**: React + Vite application. Handles UI, Context gathering (Location/Mood/Hunger), and Firebase Auth.
2.  **Backend (`server/`)**: Node.js + Express. Orchestrates API calls (Google Weather, Google Fit, Gemini AI) and handles business logic.
3.  **ML Service (`ml-service/`)**: Python Flask. Preference engine that learns user's cuisine preferences over time.

## Quick Start (Demo Mode)

The application comes with a built-in "Demo Mode" which allows you to test the full UI flow and logic without configuring any Google/Firebase API keys. It uses mocked responses that perfectly simulate the production environment.

### 1. Start the Backend (Port 3001)
```bash
cd server
npm install
npm run dev
```

### 2. Start the Frontend (Port 5173)
```bash
cd client
npm install
npm run dev
```

### 3. Start the ML Service (Port 5000)
*Requires Python 3.8+*
```bash
cd ml-service
pip install -r requirements.txt
python app.py
```

## Production Configuration

To disable Demo Mode and use live data, update the following files:

**`client/.env`**:
*   Change `VITE_DEMO_MODE=false`
*   Add all `VITE_FIREBASE_*` variables for your project.

**`server/.env`**:
*   Change `DEMO_MODE=false`
*   Add `GEMINI_API_KEY`
*   Add `GOOGLE_MAPS_API_KEY` (with Weather API enabled)
*   Add `FIREBASE_PROJECT_ID`, `FIREBASE_CLIENT_EMAIL`, and `FIREBASE_PRIVATE_KEY` for Admin SDK.

## Key Features
*   **Context-Aware**: Considers time of day, weather, physical activity, mood, and hunger.
*   **Nutritional AI**: Uses Gemini 2.5 Flash to generate scientifically grounded meal recommendations.
*   **Glassmorphism UI**: Beautiful, dark-themed responsive UI with smooth animations.
*   **Global Cuisines**: Ensures diversity (Indian, Chinese, Continental + dynamically selected others).
*   **Actionable Advice**: Provides "Avoid Lists" and Hydration tips based on the exact context.

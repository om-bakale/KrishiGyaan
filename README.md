# KrishiGyaan - Om

KrishiGyaan is an AI-powered agriculture support platform built for Indian farmers. It brings crop advisory, weather-aware planning, government scheme discovery, crop and plant disease scanning, soil guidance, multilingual voice support, and secure farmer registration into one web dashboard.

## Problem Statement

Farmers often need to move between many disconnected sources for weather, crop disease help, government schemes, soil advice, and expert guidance. This creates delays, confusion, and missed benefits, especially for farmers who prefer local languages or voice-based interaction.

KrishiGyaan solves this by giving farmers a single AI-assisted dashboard that understands their profile, crop, land, location, and language preference.

## Key Features

- **Farmer Registration and Login**
  - Secure farmer profile creation with MongoDB storage.
  - Phone number and password based login.
  - Form validation for mobile number, age, land size, Aadhaar last digits, password, and required profile fields.

- **KrishiBaba AI Assistant**
  - Uses Groq as the primary AI provider.
  - Supports a fallback Groq key to reduce presentation/demo failure risk.
  - Answers farming, schemes, crop, soil, weather, and advisory questions.

- **Government Scheme Support**
  - Matches farmer profile data with relevant schemes.
  - Generates scheme-specific application letters, forms, affidavits, checklists, grievance letters, and follow-up letters.
  - Supports draft language selection.

- **Crop and Plant Disease Detection**
  - Crop disease scanning through Crop Kindwise API.
  - Plant health assessment through Plant.id API.
  - KrishiBaba provides farmer-friendly low-cost treatment guidance.

- **Weather and Crop Advisory**
  - Uses Open-Meteo forecast data.
  - Provides short-term sowing, irrigation, spraying, and harvest guidance.
  - Includes 30-day crop growth outlook where seasonal data is available.

- **Soil Health Guidance**
  - Uses farmer profile and optional soil photo signals.
  - Produces soil score, improvement advice, and crop suitability guidance.

- **Multilingual Experience**
  - Supports English, Hindi, Bhojpuri, Gujarati, Marathi, Kannada, Tamil, Telugu, Punjabi, and Haryanvi.
  - Uses predefined local language translations for static and dashboard UI.
  - Location-based language detection and manual language selection.

- **Voice Accessibility**
  - Text-to-speech for clicked lines/headings/content.
  - Speech-to-text microphone support for AI chat and scheme doubt input.
  - Global mute/unmute audio control.

- **Vercel Deployment Ready**
  - Static frontend served from `frontend/`.
  - Serverless API routes served from `api/`.
  - `vercel.json` rewrites configured for production.

## Tech Stack

| Layer | Technology |
| --- | --- |
| Frontend | HTML, CSS, Vanilla JavaScript |
| Backend API | Node.js serverless functions |
| Local Dev Server | Node.js HTTP server |
| Database | MongoDB Atlas |
| AI | Groq API |
| Crop Disease API | Crop Kindwise |
| Plant Health API | Plant.id |
| Weather Data | Open-Meteo |
| Deployment | Vercel |

## Project Structure

```text
KrishiGyaan/
├── api/
│   ├── ai.js
│   ├── crop-health.js
│   ├── plant-health.js
│   ├── _utils.js
│   └── auth/
│       ├── _mongo.js
│       ├── register.js
│       ├── login.js
│       └── forgot-password.js
├── backend/
│   └── server.js
├── frontend/
│   ├── index.html
│   ├── register.html
│   ├── login.html
│   ├── dashboard.html
│   ├── app.js
│   ├── dashboard.js
│   ├── shared.js
│   ├── locales.js
│   └── styles.css
├── env.example
├── package.json
├── package-lock.json
└── vercel.json
```

## Environment Variables

Create a local `.env` file based on `env.example`.

```env
PORT=5173
GROQ_API_KEY=your_primary_groq_api_key
GROQ_API_KEY2=your_fallback_groq_api_key
GROQ_MODEL=llama-3.1-8b-instant
CROP_KINDWISE_API_KEY=your_crop_kindwise_api_key
PLANT_ID_API_KEY=your_plant_id_api_key
MONGODB_URI=your_mongodb_connection_string
MONGODB_DB=krishigyaan
```
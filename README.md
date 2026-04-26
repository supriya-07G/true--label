# True Label — Wellness Discovery

Scan food and medicine labels for personalized AI-powered safety analysis.

# Trust Label: AI-Powered Health Safety Scanner

Trust Label is a modern, privacy-focused web application designed to help users make informed decisions about the food and medicine they consume. By leveraging advanced multimodal AI reasoning, the app analyzes product labels against a user's unique health profile—including chronic conditions, allergies, and current medications—to provide instant safety analysis and localized summaries.

## 🌟 Key Features

- **Multimodal Label Scanning**: Uses high-fidelity OCR and vision reasoning to "read" product labels from camera photos or manual text input.
- **Personalized Safety Engine**: Cross-references ingredients with user-defined health data to identify allergens, drug interactions, and condition conflicts.
- **Global Regulatory Checks**: Identifies ingredients banned or restricted by major regulatory bodies (FDA, EU, CDSCO, etc.) across different countries.
- **Multilingual Support**: Fully localized interface and AI analysis in **English**, **Telugu (తెలుగు)**, and **Hindi (हिंदी)**.
- **Privacy-by-Design**: No backend database. All sensitive medical data and scan history are stored locally on the user's device using browser `LocalStorage`.
- **Emergency Escalation**: High-risk detections trigger distinct visual/audio alerts and provide quick-access emergency contact and sharing options.

## 🏗️ Architecture

The project follows a **Serverless Frontend-Direct** architecture. Logic is centralized in the client to ensure maximum privacy and low-latency interactions.

### System Flow
1. **User Profile**: User inputs health data which is persisted in `LocalStorage`.
2. **Analysis Request**: The app constructs a multimodal payload containing the label (image or text) and the user's health context.
3. **AI Reasoning**: The Gemini 2.5 Flash model processes the request using clinical-grade reasoning to identify risks.
4. **Structured Response**: Results are returned as a strictly typed JSON object for predictable UI rendering.
5. **Localization**: The AI performs on-the-fly translation of medical findings into the user's preferred language.

## 🛠️ Tech Stack

- **Framework**: React 19 (ES6 Modules)
- **Styling**: Tailwind CSS (Utility-first responsive design)
- **AI Integration**: `@google/genai` SDK
- **Model**: Gemini 2.5 Flash (for high-speed multimodal reasoning)
- **Icons**: Lucide React
- **Persistence**: Browser Web Storage API

## 🚀 Getting Started

### Prerequisites
- A modern web browser (Chrome, Safari, or Edge recommended for Camera API support).
- An API Key for the Gemini API.

### Installation
1. Clone the repository.
2. Ensure you have the `process.env.API_KEY` configured in your environment.
3. Serve the `index.html` using a local development server (e.g., Live Server, Vite, or a simple python server).

```bash
# Example using a simple python server
python3 -m http.server 8000
```

## 🔒 Privacy & Security

Trust Label is designed with a "Zero-Knowledge" approach to user data:
- **No Cloud Storage**: We do not store your medical history on any remote servers.
- **Local Persistence**: Data stays in your browser's `LocalStorage`. Clearing your browser data or clicking "Reset" in settings permanently removes all info.
- **Stateless AI**: Health context is sent to the AI model only during a scan and is not used for model training or retained after the session.

## ⚠️ Medical Disclaimer

Trust Label provides information based on AI analysis of provided labels. It is **not** a substitute for professional medical advice, diagnosis, or treatment. Always consult with a qualified healthcare provider or pharmacist before starting new medications or changing your diet, especially if you have known health conditions or allergies.


## Local Development

**Prerequisites:** Node.js 18+

1. Install dependencies:
   ```
   npm install
   ```

2. Copy the example env file and add your Gemini API key:
   ```
   cp .env.example .env
   ```
   Then edit `.env` and replace `your_gemini_api_key_here` with your real key from [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)

3. Run the app:
   ```
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000)

## Deploy to Vercel

1. Push this project to a GitHub repository.

2. Go to [vercel.com](https://vercel.com), click **Add New Project**, and import your repo.

3. In the Vercel project settings, go to **Environment Variables** and add:
   - **Name:** `GEMINI_API_KEY`
   - **Value:** your Gemini API key

4. Click **Deploy**. Vercel will use `vercel.json` for the build config automatically.

> **Note:** The Gemini API key is embedded in the client-side bundle at build time (standard for Vite SPAs without a backend). Keep your key usage monitored in [Google AI Studio](https://aistudio.google.com).

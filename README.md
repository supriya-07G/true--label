# True Label — Wellness Discovery

Scan food and medicine labels for personalized AI-powered safety analysis.

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

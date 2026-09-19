# StudyPilot AI

StudyPilot is a cross-device PWA for AI tutoring, subject explanations, exam-style practice, PDF/image study tools, focus sessions, saved work and optional Pro subscriptions.

## Enable AI answers

Deploy this repository on Netlify and add these environment variables in Netlify Site configuration:

- `OPENAI_API_KEY` — your secret OpenAI API key
- `OPENAI_MODEL` — optional model override (default: `gpt-5.6-luna`)
- `AI_DAILY_IP_LIMIT` — optional, default 120
- `AI_BURST_LIMIT` — optional, default 30 per 10 minutes

Never put the secret API key in browser-side files.

## Netlify AI backend

All AI features call `/.netlify/functions/ai`. The backend uses the OpenAI Responses API and keeps the API key server-side.

After deployment, open `/.netlify/functions/ai` on the live site. It should return JSON with `configured: true` after `OPENAI_API_KEY` is configured and the site has been redeployed.

## Reliability fix

This build fixes the JavaScript startup problem that could stop all CTA buttons after page load, improves AI error handling, and refreshes the PWA cache so older broken JavaScript is replaced.

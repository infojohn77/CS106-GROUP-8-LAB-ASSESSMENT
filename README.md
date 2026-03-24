# The 8th Wardrobe — Vercel Deployment Guide

## Project Structure

```
the8thwardrobe/
├── api/
│   └── chat.js          ← Serverless function (Anthropic API proxy)
├── public/
│   ├── index.html       ← Main website
│   ├── clothe1.jpg      ← (add your images here)
│   ├── clothe3.jpg
│   ├── clothe5.jpg
│   ├── clothe7.jpg
│   ├── shoe1.jpg
│   ├── shoe2.jpg
│   ├── wo1.jpg
│   ├── wo4.jpg
│   ├── wo5.jpg
│   └── trustees/
│       ├── shegun.jpg
│       ├── john.jpg
│       ├── adewumi.jpg
│       ├── david.jpg
│       ├── chisom.jpg
│       ├── Adewale.jpg
│       ├── Devine.jpg
│       ├── purpose.jpg
│       ├── michael.jpg
│       ├── joshua.jpg
│       ├── gbolahan.jpg
│       ├── Hafsat.jpg
│       └── faith2.jpg
└── vercel.json          ← Vercel routing config
```

## Deployment Steps

### 1. Add your images
Place all product images and trustee photos into the correct folders inside `public/` as shown above.

### 2. Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/the8thwardrobe.git
git push -u origin main
```

### 3. Deploy on Vercel
1. Go to [vercel.com](https://vercel.com) and sign in
2. Click **"Add New Project"** → Import your GitHub repository
3. Leave all build settings as default (no framework needed)
4. Click **Deploy**

### 4. Set the API Key (IMPORTANT)
The AI chatbox requires your Anthropic API key as an environment variable:

1. In your Vercel project dashboard, go to **Settings → Environment Variables**
2. Add a new variable:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-...` (your Anthropic API key)
3. Click **Save**, then **Redeploy** the project

> ⚠️ Never put your API key directly in the HTML or JavaScript files — it would be exposed publicly. The `api/chat.js` serverless function keeps it safe on the server.

## What Was Changed From the Original

| Issue | Fix |
|---|---|
| API key exposed in browser JS | Moved to secure `/api/chat.js` serverless proxy |
| `>>` HTML typo in Trustees heading | Fixed |
| Duplicate product `data-product` IDs | Each product now has a unique ID |
| `faith2` missing file extension | Fixed to `faith2.jpg` |
| Minor spelling fixes (Appoitnment, Multiouting) | Fixed |
| Footer year said 2025 | Updated to 2026 |

# 🕵️‍♀️ JobGuard AI — Is This Job Legit?

An AI-powered job scam detector. Paste in a job posting and get an instant safety score, a breakdown of risk factors, and a plain-language explanation of any red flags — before you apply.

## Why

Job scams are getting harder to spot: fake recruiters, too-good-to-be-true salaries, requests for personal info or upfront payments. JobGuard AI runs the listing through Claude and returns a structured risk report in seconds, so you can make a quicker, more informed call.

## Features

- **Safety score (0–100)** with a clear risk level — Low, Suspicious, or High
- **Risk breakdown** across categories like company credibility, salary claims, contact info, and urgency language
- **Suspicious signals** flagged with plain-language explanations
- **Company info tab** with AI-inferred confidence and presence signals
- **Scan history** to revisit past analyses
- Clean, dark-themed UI built from scratch

## Tech stack

- React + Vite
- Anthropic API (Claude) for the analysis
- No backend — runs entirely client-side, using your own API key

## Getting started

```bash
git clone https://github.com/your-username/jobguard-ai.git
cd jobguard-ai
npm install
npm run dev
```

Open the local URL Vite gives you, add your [Anthropic API key](https://console.anthropic.com/settings/keys) in the app, and paste in a job listing to try it out.

Your API key is only kept in memory for the session and is never stored or sent anywhere except directly to the Anthropic API.

## Project structure

```
src/
├── App.jsx                 View routing & state
├── lib/
│   ├── theme.js             Color tokens & helpers
│   └── analyze.js           Anthropic API call + prompt schema
└── components/
    ├── Landing.jsx           Hero + paste box
    ├── Loading.jsx
    ├── AppShell.jsx          Sidebar + top bar
    ├── HistoryView.jsx
    ├── ResultView.jsx        Tab routing
    └── tabs/                 Overview, Detailed, Company, Raw
```

## Disclaimer

This is a demo/prototype project. The "Company Info" tab is based on AI inference from the listing text, not real domain/whois data — always independently verify a company before applying or sharing personal information.

## License

MIT

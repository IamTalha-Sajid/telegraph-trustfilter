# TrustFilter — Frontend

React/Vite frontend for TrustFilter. Submit a phone number, SMS message, or both — the UI shows a live terminal feed of the analysis pipeline and then displays the scam verdict with cryptographic proof.

## Setup

```bash
cp .env.example .env   # optional — leave blank to use Vite proxy
npm install
npm run dev            # http://localhost:5173
```

Requires the TrustFilter API running on port 3006 (see `../api/`).

## Environment variables

| Variable | Description |
|---|---|
| `VITE_API_BASE_URL` | Override API base URL for production (e.g. `https://api.trustfilter.xyz`). Leave blank in dev — Vite proxies `/api` to `http://localhost:3006`. |

## Stack

- React 18 + React Router
- Vite
- Lucide React icons
- No wallet / Solana UI — payments are handled server-side

# TrustFilter — API

Express API that analyzes phone numbers and SMS messages for scam patterns using the Telegraph Groq LLM subnet, with x402 Solana micro-payments as cryptographic proof of each call.

## Setup

```bash
cp .env.example .env   # fill in SOLANA_PRIVATE_KEY
npm install
npm run dev            # http://localhost:3006
```

## Environment variables

| Variable | Default | Description |
|---|---|---|
| `PORT` | `3006` | Port the API listens on |
| `TELEGRAPH_BASE_URL` | `http://54.252.48.30:7044` | Telegraph dispatcher base URL |
| `GROQ_SUBNET_PATH` | `/subnet-dispatcher/v1/102/chat` | Groq LLM subnet path |
| `SOLANA_PRIVATE_KEY` | — | Base58 private key for x402 payments |
| `SOLANA_NETWORK` | `devnet` | `devnet` or `mainnet` |
| `FRONTEND_ORIGIN` | `http://localhost:5174` | Allowed CORS origin |

## Endpoint

### `POST /api/analyze`

**Body** (at least one field required):
```json
{
  "phone": "+1-800-123-4567",
  "message": "Congratulations! You've won a $1000 gift card. Click here to claim."
}
```

**Response:**
```json
{
  "verdict": "scam",
  "confidence": 0.95,
  "summary": "Multiple high-confidence scam indicators detected.",
  "reasons": ["Unsolicited prize claim", "Urgency language present"],
  "redFlags": ["You've won", "Click here to claim"],
  "txHash": "5KtY3...abc"
}
```

Verdict is one of: `scam` · `suspicious` · `likely_safe`

### `GET /health`

Returns `{ ok: true }`.

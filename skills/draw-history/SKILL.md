---
name: draw-history
description: "Fetch historical lottery draw results. Use when the user asks about past draws, recent results, or winning numbers."
metadata:
  {
    "openclaw":
      {
        "emoji": "📊",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Draw History

Retrieve historical draw results for a given lottery.

## When to use

- User asks about past draws or recent results
- User asks "what were the winning numbers?"
- User wants to see draw history or trends

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_draw_history" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "limit": 10}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `limit` | No | integer | Number of recent draws to return (1–100). Default: 10. |

## Response format

```json
{
  "lottery": "powerball",
  "total_draws": 2708,
  "draws": [
    {
      "draw_date": "2026-02-09",
      "numbers": [3, 18, 27, 41, 59],
      "bonus_number": 11
    }
  ]
}
```

## Presentation

- Present draws in a clear chronological list
- Highlight any notable patterns (repeated numbers, sequences)
- Mention the total available draws for context

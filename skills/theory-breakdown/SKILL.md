---
name: theory-breakdown
description: "Get detailed 10-pillar theory analysis for a lottery. Use when the user wants to understand WHY specific numbers were chosen or asks about pillar analysis."
metadata:
  {
    "openclaw":
      {
        "emoji": "🧬",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Theory Breakdown

Retrieve the detailed analytical pillar breakdown for a specific lottery.

## When to use

- User asks "why these numbers?"
- User wants pillar-level analysis
- User asks about hot/cold numbers, cycles, or patterns
- User asks about the theory behind predictions

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_theory_breakdown" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "numbers": [7, 14, 23, 38, 52]}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `numbers` | Yes | array of int | The numbers to analyze |

## Response format

```json
{
  "lottery": "mega_millions",
  "numbers_analyzed": [7, 14, 23, 38, 52],
  "pillar_analysis": {
    "statistical": { "score": 0.81, "details": "..." },
    "fibonacci": { "score": 0.72, "details": "..." },
    "euler": { "score": 0.65, "details": "..." },
    "markov": { "score": 0.78, "details": "..." },
    "tesla_369": { "score": 0.60, "details": "..." },
    "astrology": { "score": 0.74, "details": "..." },
    "primes": { "score": 0.55, "details": "..." },
    "numerology": { "score": 0.67, "details": "..." },
    "wolfram": { "score": 0.63, "details": "..." },
    "wiseman": { "score": 0.58, "details": "..." }
  }
}
```

## Presentation

- Break down each pillar's contribution clearly
- Highlight the strongest-scoring pillars
- Explain what each pillar measures in your persona's voice
- Use the pillar data to tell a story about number selection

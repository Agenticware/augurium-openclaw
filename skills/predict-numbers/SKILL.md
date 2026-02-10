---
name: predict-numbers
description: "Generate lottery number predictions using the 10-pillar convergence framework. Use when the user asks for predictions, recommended numbers, or 'what should I play'."
metadata:
  {
    "openclaw":
      {
        "emoji": "🔮",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Predict Numbers

Generate a lottery number prediction for a specific lottery and draw date.

## When to use

- User asks for predictions or recommended numbers
- User says "what should I play" or "give me numbers"
- User asks about the next draw

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/predict_numbers" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "target_date": "YYYY-MM-DD"}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `target_date` | No | string | Target draw date (YYYY-MM-DD). Defaults to next scheduled draw. |
| `personalized` | No | boolean | Include user birth data in numerology analysis. Default: false. |

## Response format

```json
{
  "prediction_id": "uuid",
  "lottery": "powerball",
  "target_date": "2026-02-12",
  "predicted_numbers": [7, 14, 23, 38, 52],
  "predicted_bonus": 19,
  "convergence_score": 0.73,
  "pillar_scores": { "statistical": 0.81, "numerology": 0.67, ... },
  "explanation": "Numbers 7 and 14 show strong statistical recency..."
}
```

## Presentation

- Lead with the predicted numbers prominently
- Mention the convergence score as a confidence indicator
- Highlight which pillars contributed most strongly
- Include the narrative explanation in your persona's voice
- Always remind users this is for entertainment and research

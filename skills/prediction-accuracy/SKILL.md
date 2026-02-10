---
name: prediction-accuracy
description: "Retrieve accuracy metrics showing how past predictions performed. Use when the user asks about system accuracy, track record, or performance."
metadata:
  {
    "openclaw":
      {
        "emoji": "🎯",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Prediction Accuracy

Retrieve accuracy metrics for past predictions against actual draw results.

## When to use

- User asks "how accurate are you?"
- User asks about track record or performance
- User wants to see hit rates or match statistics
- User asks about system credibility

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_prediction_accuracy" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "period": "30d"}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `period` | No | string | Time period: `7d`, `30d`, `90d`, or `all`. Default: `30d`. |

## Response format

```json
{
  "lottery": "fantasy5",
  "period": "30d",
  "accuracy": {
    "total_predictions": 124,
    "total_draws": 15,
    "exact_match_rate": 0.0,
    "partial_match_rates": {
      "5_of_5": 0.000,
      "4_of_5": 0.008,
      "3_of_5": 0.065,
      "2_of_5": 0.210,
      "1_of_5": 0.445,
      "0_of_5": 0.272
    },
    "average_numbers_matched": 1.42,
    "vs_random_baseline": {
      "random_average_matched": 0.89,
      "improvement_factor": 1.60
    }
  }
}
```

## Presentation

- Present the improvement factor vs random baseline prominently
- Show partial match rates as a distribution
- Be honest about limitations — lottery prediction is inherently difficult
- Frame results positively but truthfully
- Mention which pillars are performing best if available

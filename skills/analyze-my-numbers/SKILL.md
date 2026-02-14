---
name: analyze-my-numbers
description: "Analyze user-provided lottery numbers against historical data. Use when the user says they want to play specific numbers and wants analysis, or asks 'how good are these numbers'."
metadata:
  {
    "openclaw":
      {
        "emoji": "🔢",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Analyze My Numbers

Analyze a user's chosen lottery numbers against historical draw data, convergence scores, and pattern analysis.

## When to use

- User says "I want to play 3, 6, 9, 22, 36" or provides specific numbers
- User asks "how good are these numbers" or "analyze my numbers"
- User wants to know the historical performance of specific numbers
- User asks about frequency, gaps, or co-occurrence of numbers

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/analyze_my_numbers" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "numbers": [3, 6, 9, 22, 36]}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `numbers` | Yes | array[int] | The numbers the user wants to analyze |

## Response format

```json
{
  "lottery": "fantasy5",
  "numbers": [3, 6, 9, 22, 36],
  "total_draws_analyzed": 11685,
  "frequency": [{"number": 3, "appearances": 1623, "percentage": 13.9, "classification": "hot"}],
  "gap_analysis": [{"number": 3, "draws_since_last": 2, "last_seen": "2026-02-13"}],
  "co_occurrence": [{"pair": [3, 6], "times_together": 245, "percentage": 2.1}],
  "convergence_scores": [{"number": 3, "convergence_score": 0.72}],
  "pattern_analysis": {"sum": 76, "range": 33, "odd_even": "3/2", "sequential_clusters": []},
  "overall_score": 62.5,
  "summary": "Hot numbers: 3, 9. Cold numbers: 36. Strongest pair: 3-9 (312 times together). Overall score: 62.5/100."
}
```

## Presentation

- Lead with the overall score as a "vibe rating" (0-100)
- Highlight hot and cold numbers with your persona's flair
- Mention the strongest co-occurring pair
- Show gap analysis for any numbers that haven't appeared recently
- Use the pattern analysis (odd/even, sum, range) to add color commentary
- End with an overall assessment in your persona's voice
- Always remind users this is for entertainment and research

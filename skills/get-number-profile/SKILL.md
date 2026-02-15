---
name: get-number-profile
description: "Get a detailed profile for a specific lottery number including hot/cold status, pillar scores, co-occurring neighbors, and patterns. Use when the user asks 'tell me about number 7' or 'what's special about 23'."
metadata:
  {
    "openclaw":
      {
        "emoji": "🔍",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Get Number Profile

Retrieve a detailed profile for a specific number in a lottery, sourced from the Neo4j knowledge graph.

## When to use

- User asks "tell me about number 7" or "what's special about 23"
- User wants to know about a specific number's history, patterns, and pillar scores
- User clicks "Ask AI" from the Knowledge Graph on a number node

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_number_profile" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "number": NUMBER}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `number` | Yes | integer | The number to profile |

## Response format

```json
{
  "number": 7,
  "lottery": "fantasy5",
  "hot_cold": "hot",
  "total_appearances": 1623,
  "avg_gap": 5.2,
  "current_gap": 2,
  "convergence_score": 0.72,
  "is_prime": true,
  "is_fibonacci": false,
  "digit_root": 7,
  "pillar_scores": [{"name": "primes", "score": 0.95}],
  "top_co_occurring": [{"value": 14, "count": 312}],
  "active_patterns": [{"type": "consecutive", "strength": 0.8}],
  "summary": "Number 7 in fantasy5 is currently hot with 1623 total appearances and a convergence score of 72.0% — it's a prime number."
}
```

## Presentation

- Lead with the summary in your persona's voice
- Highlight whether the number is hot, cold, or neutral
- Mention top pillar scores and what they mean
- Share the strongest co-occurring numbers ("often appears with...")
- Note any special properties (prime, Fibonacci, digit root)
- Always remind users this is for entertainment and research

---
name: get-graph-insights
description: "Get high-level knowledge graph insights: top convergence numbers, hottest/coldest, strongest pairs, pillar signals. Use when the user asks 'what are the best numbers', 'what's trending', or 'give me insights'."
metadata:
  {
    "openclaw":
      {
        "emoji": "💡",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Get Graph Insights

Retrieve high-level insights from the knowledge graph for a lottery: top convergence numbers, hottest and coldest numbers, strongest co-occurrence pairs, and pillar signal strengths.

## When to use

- User asks "what are the best numbers right now" or "what's trending"
- User asks "give me insights" or "what does the data say"
- User wants a high-level overview of the knowledge graph state

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_graph_insights" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE"}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |

## Response format

```json
{
  "lottery": "fantasy5",
  "top_convergence": [{"value": 7, "score": 0.85, "hot_cold": "hot"}],
  "hottest": [{"value": 3, "appearances": 1700}],
  "coldest": [{"value": 33, "appearances": 800}],
  "strongest_pairs": [{"num1": 3, "num2": 14, "count": 450}],
  "pillar_signals": [{"pillar": "mathematics", "avg_score": 0.72, "num_count": 36}],
  "summary": "Top convergence numbers for fantasy5: 7, 14, 3. Hottest: 3, 9, 14. Coldest: 33, 31, 28."
}
```

## Presentation

- Open with the top convergence numbers and their meaning
- Highlight the hottest numbers (frequent, trending) vs coldest (overdue, dormant)
- Mention the strongest co-occurring pairs ("these numbers love to appear together")
- Share which pillars are signaling strongest right now
- Use your persona's voice and cosmic flair
- Always remind users this is for entertainment and research

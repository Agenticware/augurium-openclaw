---
name: knowledge-graph
description: "Navigate the Augurium.ai knowledge graph (Neo4j) to explore relationships between numbers, draws, and cosmic events. Use when the user asks about number relationships, patterns, or connections."
metadata:
  {
    "openclaw":
      {
        "emoji": "🕸️",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Knowledge Graph Explorer

Navigate the Augurium.ai knowledge graph to explore relationships between numbers,
draws, astrological events, numerological cycles, and geometric patterns.

## When to use

- User asks about number relationships or co-occurrences
- User asks "which numbers appear together?"
- User asks about connections between draws and cosmic events
- User wants deep investigation into why certain numbers cluster

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/explore_knowledge_graph" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"node_id": "number:7", "depth": 2}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `node_id` | Yes | string | Node ID to start from (e.g., `number:7`, `draw:pb_20260205`, `transit:venus_trine_jupiter`) |
| `depth` | No | integer | Relationship hops to traverse (1–4). Default: 2. |
| `relationship_filter` | No | string | Filter by relationship type (e.g., `CO_OCCURS_WITH`, `DRAWN_IN`, `DURING_TRANSIT`) |

## Node ID formats

- `number:7` — A lottery number
- `draw:f5_20260209` — A specific draw (lottery prefix + date)
- `transit:venus_trine_jupiter` — An astrological transit

## Response format

```json
{
  "node_id": "number:7",
  "depth": 2,
  "relationship_filter": "CO_OCCURS_WITH",
  "results": [
    {
      "n": { "value": 7, "type": "Number" },
      "r": [{ "type": "CO_OCCURS_WITH", "count": 48 }],
      "m": { "value": 14, "type": "Number" }
    }
  ],
  "result_count": 14
}
```

## Presentation

- Highlight the strongest co-occurrence relationships
- Compare co-occurrence rates to expected random rates
- Use graph metaphors appropriate to your persona
- Offer to explore deeper connections if the user is interested

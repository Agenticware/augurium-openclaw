---
name: astrology-aspects
description: "Get current planetary aspects and their influence on lottery draws. Use when the user asks about cosmic influences, planetary alignments, or astrological factors."
metadata:
  {
    "openclaw":
      {
        "emoji": "🌠",
        "requires": { "bins": ["curl"] },
      },
  }
---

# Astrology Aspects

Retrieve current astrological aspects and their potential influence on number patterns.

## When to use

- User asks about cosmic or planetary influences
- User asks about astrological factors affecting draws
- User asks about moon phase or transits
- User wants to know the "cosmic weather"

## How to call

```bash
curl -s -X POST "${FASTAPI_URL}/api/internal/tools/get_astrology_aspects" \
  -H "Content-Type: application/json" \
  -H "X-Internal-API-Key: ${INTERNAL_API_KEY}" \
  -d '{"lottery": "LOTTERY_CODE", "date": "YYYY-MM-DD"}'
```

## Parameters

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `lottery` | Yes | string | One of: `fantasy5`, `powerball`, `mega_millions` |
| `date` | No | string | Target date (YYYY-MM-DD). Defaults to today. |

## Response format

```json
{
  "date": "2026-02-09",
  "lottery": "powerball",
  "aspects": {
    "active_transits": [
      {
        "transit": "Venus trine Jupiter",
        "influence": "Expansive, favorable for mid-range numbers",
        "historically_correlated_ranges": [15, 35]
      }
    ],
    "lunar_phase": "Waxing Gibbous (87%)",
    "dominant_element": "Water",
    "suggested_number_affinity": [3, 7, 18, 22, 47, 63],
    "signal_strength": 0.74
  }
}
```

## Presentation

- Lead with the most significant active transits
- Describe the lunar phase and its traditional meaning
- Connect astrological data to number suggestions
- Be scientifically transparent — present correlations, not causation

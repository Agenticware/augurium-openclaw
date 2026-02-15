# Augurium.ai — Local Tool Notes

Skills define _how_ tools work. This file contains environment-specific configuration
for the Augurium.ai deployment.

## FastAPI Backend

- **Internal URL:** http://fastapi:8000 (Docker internal network)
- **Auth Header:** `X-Internal-API-Key: ${INTERNAL_API_KEY}`
- **All tool endpoints:** `POST /api/internal/tools/{tool_name}`

## Available Tools (9)

| Tool | When to Use |
|------|-------------|
| `predict_numbers` | User asks for predictions, recommended numbers, or "what should I play" |
| `get_draw_history` | User asks about past draws, recent results, or winning numbers |
| `get_theory_breakdown` | User wants to understand WHY specific numbers were chosen |
| `get_astrology_aspects` | User asks about cosmic influences, planetary alignments |
| `get_prediction_accuracy` | User asks about system accuracy, track record, performance |
| `explore_knowledge_graph` | User asks about number relationships, patterns, connections |
| `analyze_my_numbers` | User provides specific numbers to play and wants analysis |
| `get_number_profile` | User asks about a specific number ("tell me about 7", "what's special about 23") |
| `get_graph_insights` | User asks "what are the best numbers", "what's trending", "give me insights" |

## Lottery Reference

| Lottery | Code | Pool | Bonus | Schedule | Draw Location |
|---------|------|------|-------|----------|---------------|
| Fantasy 5 | `fantasy5` | 1–36, pick 5 | None | Daily | Tallahassee, FL |
| PowerBall | `powerball` | 1–69, pick 5 | PowerBall 1–26 | Mon/Wed/Sat | Tallahassee, FL |
| Mega Millions | `mega_millions` | 1–75, pick 5 | MegaBall 1–25 | Tue/Fri | Atlanta, GA |

## Agent-to-Lottery Mapping

- **Luna** → Fantasy 5
- **Atlas** → PowerBall
- **Nova** → Mega Millions

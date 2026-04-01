<p align="center">
  <img src="https://kultur.dev/favicon.svg" alt="Kultur.dev" width="80" height="80">
</p>

<h1 align="center">Kultur.dev MCP Server</h1>

<p align="center">
  <strong>Cultural Intelligence Infrastructure for AI Agents</strong><br>
  The world's first MCP server for cultural analysis, sensitivity checking, localization guidance, Hofstede dimensions, and geopolitical risk.
</p>

<p align="center">
  <a href="https://kultur.dev">Website</a> •
  <a href="https://kultur.dev/docs">API Docs</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#tools">Tools</a> •
  <a href="#pricing">Pricing</a>
</p>

---

## Overview

**Kultur.dev** provides cultural intelligence as an API — enabling AI agents, LLMs, and enterprise software to understand cultural context, avoid sensitivity violations, and communicate effectively across 195+ countries and 50+ languages.

The MCP (Model Context Protocol) server exposes 9 specialized tools that any MCP-compatible client can use:

| Tool | Description |
|------|-------------|
| `analyze_cultural_context` | Deep cultural analysis for any country — values, taboos, business etiquette, communication norms |
| `check_cultural_sensitivity` | Scan text for cultural sensitivity issues with severity scoring and fix suggestions |
| `get_localization_guidance` | Get localization recommendations across 15 tones (formal, humble, celebratory, respectful, casual, neutral, professional, friendly, humorous, marketing, legal, medical, technical, academic, diplomatic) |
| `compare_cultures` | Side-by-side cultural comparison between any two countries |
| `get_communication_style` | Communication preferences, negotiation styles, and business protocol for any culture |
| `get_holiday_calendar` | Cultural and religious holidays, observances, and scheduling considerations |
| `analyze_hofstede` | Hofstede's 6 cultural dimensions analysis with scores and business implications |
| `compare_hofstede` | Compare Hofstede dimension scores between two countries |
| `get_geopolitical_heatmap` | Geopolitical risk analysis with adaptive EWA scoring across 12 risk categories |

## Quick Start

### Option 1: SSE Transport (Recommended)

Connect any MCP client to the Kultur.dev SSE endpoint:

```
https://kultur.dev/api/mcp-sse/sse
```

Authentication via Bearer token in the `Authorization` header.

### Option 2: Claude Desktop

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "kultur-dev": {
      "url": "https://kultur.dev/api/mcp-sse/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

### Option 3: Cursor IDE

Add to your Cursor MCP settings (`.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "kultur-dev": {
      "url": "https://kultur.dev/api/mcp-sse/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

### Option 4: Windsurf IDE

Add to your Windsurf MCP configuration:

```json
{
  "mcpServers": {
    "kultur-dev": {
      "serverUrl": "https://kultur.dev/api/mcp-sse/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

### Option 5: VS Code / GitHub Copilot

Add to your VS Code `settings.json`:

```json
{
  "mcp": {
    "servers": {
      "kultur-dev": {
        "type": "sse",
        "url": "https://kultur.dev/api/mcp-sse/sse",
        "headers": {
          "Authorization": "Bearer YOUR_API_KEY"
        }
      }
    }
  }
}
```

### Option 6: Cline

Add to your Cline MCP settings:

```json
{
  "mcpServers": {
    "kultur-dev": {
      "url": "https://kultur.dev/api/mcp-sse/sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

## REST API

For non-MCP integrations, Kultur.dev also provides a REST API:

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/v1/analyze/text` | POST | Cultural context analysis |
| `/api/v1/analyze/hofstede` | POST | Hofstede dimensions analysis |
| `/api/v1/rewrite` | POST | Culturally-aware text rewriting |
| `/api/v1/sensitivity/check` | POST | Cultural sensitivity scanning |
| `/api/v1/localization/guidance` | POST | Localization recommendations |
| `/api/v1/geopolitical/heatmap` | POST | Geopolitical risk scoring |

### Example: Analyze Cultural Context

```bash
curl -X POST https://kultur.dev/api/v1/analyze/text \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Schedule a business meeting in Tokyo",
    "target_country": "JP",
    "source_country": "US"
  }'
```

### Example: Check Cultural Sensitivity

```bash
curl -X POST https://kultur.dev/api/v1/sensitivity/check \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Let us raise a toast to our partnership",
    "target_countries": ["SA", "IR"]
  }'
```

## Authentication

All requests require a valid API key passed as a Bearer token:

```
Authorization: Bearer YOUR_API_KEY
```

### Get Your API Key

1. Visit [kultur.dev](https://kultur.dev)
2. Sign up for a plan
3. Copy your API key from the dashboard

## Pricing

| Plan | Credits | Markets | Price |
|------|---------|---------|-------|
| **Free** | 1,000/month | 3 countries | $0 |
| **Pro** | 50,000/month | All 195 countries | $49/month |
| **Enterprise** | Unlimited | All + custom models | Contact us |

Free tier responses include a watermark CTA. Pro and Enterprise tiers provide clean, production-ready responses.

## Use Cases

**For AI Agents & LLMs:**
- Cultural context injection before generating responses about specific countries
- Real-time sensitivity checking on AI-generated content
- Localization guidance for multi-market content generation

**For Enterprise Software:**
- CRM systems that adapt communication style per market
- HR platforms with cultural onboarding intelligence
- Marketing tools with built-in cultural compliance

**For Developers:**
- Add cultural awareness to any application in minutes
- Hofstede dimensions for academic and business research
- Geopolitical risk scoring for supply chain and investment analysis

## Server Discovery

The MCP server card is available at:

```
https://kultur.dev/api/.well-known/mcp/server-card.json
```

## Composio Toolkit

Kultur.dev is also available as a native **Composio toolkit** for LangChain, CrewAI, and OpenAI integrations:

```bash
pip install composio-kultur
```

The toolkit provides 8 LocalAction tools:

| Tool | Description |
|------|-------------|
| `AnalyzeCulturalContext` | Deep cultural analysis for any market |
| `CheckCulturalSensitivity` | Scan text for sensitivity issues |
| `GetLocalizationGuidance` | Localization across 15 tones |
| `CompareCultures` | Side-by-side cultural comparison |
| `GetCommunicationStyle` | Communication preferences per culture |
| `GetHolidayCalendar` | Cultural holidays and observances |
| `AnalyzeHofstede` | Hofstede 6 dimensions analysis |
| `GetGeopoliticalHeatmap` | Geopolitical risk scoring |

### LangChain Example

```python
from composio_kultur.toolkit import KulturTool
from langchain.agents import initialize_agent

tools = KulturTool.get_tools(api_key="YOUR_API_KEY")
agent = initialize_agent(tools, llm, agent="zero-shot-react-description")
agent.run("Analyze cultural sensitivity of our ad campaign for Saudi Arabia")
```

## Audit Grade

**A+ (97%)** — Independently audited by Manus AI on April 1, 2026. Full audit report available upon request.

## Support

- **Documentation:** [kultur.dev/docs](https://kultur.dev/docs)
- **Email:** contact@globalintech.ai
- **Issues:** [GitHub Issues](https://github.com/kultur-dev/mcp-server/issues)

## License

Copyright 2024-2026 Global InTech AI. All rights reserved.

The Kultur.dev API and MCP server are proprietary. This repository contains configuration documentation and integration guides only — no proprietary source code.

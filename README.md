<p align="center">
  <a href="https://kultur.dev">
    <img src="https://raw.githubusercontent.com/kultur-dev/mcp-server/main/kultur-logo-light-bg.png" alt="Kultur.dev" width="280" />
  </a>
</p>

<h3 align="center">Cultural Intelligence Infrastructure for AI Agents</h3>

<p align="center">
  The multimodal cultural intelligence layer every AI agent and global company needs.<br/>
  Analyze text, images, and video across 200+ markets before you ship, post, or launch.
</p>

<p align="center">
  <a href="https://kultur.dev">Website</a> •
  <a href="https://kultur.dev/docs">Docs</a> •
  <a href="https://kultur.dev/api/openapi-spec.json">OpenAPI Spec</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#tools">Tools</a> •
  <a href="#pricing">Pricing</a>
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/@kultur-dev/mcp-server"><img src="https://img.shields.io/npm/v/@kultur-dev/mcp-server?label=npm&color=blue" alt="npm" /></a>
  <a href="https://pypi.org/project/kultur-mcp/"><img src="https://img.shields.io/pypi/v/kultur-mcp?label=pypi&color=blue" alt="PyPI" /></a>
  <a href="https://github.com/kultur-dev/mcp-server/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License" /></a>
  <a href="https://smithery.ai/server/@kultur-dev/mcp-server"><img src="https://smithery.ai/badge/@kultur-dev/mcp-server" alt="Smithery" /></a>
</p>

---

## Why Kultur.dev?

Every AI agent operating globally is flying blind without cultural intelligence. A thumbs-up gesture that's offensive in the Middle East. A color palette that signals death in East Asia. A marketing slogan that's a slur in Brazil. These aren't edge cases. They're the daily reality of operating globally without cultural awareness.

**Kultur.dev is the world's first multimodal cultural intelligence infrastructure.** It gives AI agents and global enterprises the ability to analyze text, images, and video for cultural risks, sensitivity, and localization across 200+ markets, before content goes live.

### What Makes It Different

Kultur.dev goes beyond text. It analyzes images for visual taboos (colors, symbols, gestures) and video content for cultural compliance across regions. It covers 200+ markets with deep, verified cultural intelligence, not surface-level summaries.

Localization comes with 15 tone styles (formal, humble, celebratory, diplomatic, marketing, medical, legal, and more). Reports are branded, boardroom-ready PDF documents, not raw JSON. Risk scoring is real-time with actionable recommendations before content ships.

The platform includes Hofstede cultural dimensions with business implications and cross-country comparison, plus geopolitical risk analysis with adaptive EWA scoring across 12 risk categories.

---

## Overview

Kultur.dev provides cultural intelligence as an API, enabling AI agents, LLMs, and enterprise software to understand cultural context, avoid sensitivity violations, and communicate effectively across 200+ markets and 50+ languages.

The MCP (Model Context Protocol) server exposes **9 specialized tools** plus **multimodal and streaming endpoints** that any MCP-compatible client can use:

### MCP Tools

| Tool | Description |
|------|-------------|
| `analyze_cultural_context` | Deep cultural analysis for any country including values, taboos, business etiquette, communication norms |
| `check_cultural_sensitivity` | Scan text for cultural sensitivity issues with severity scoring and fix suggestions |
| `get_localization_guidance` | Localization recommendations across 15 tones (formal, humble, celebratory, respectful, casual, neutral, professional, friendly, humorous, marketing, legal, medical, technical, academic, diplomatic) |
| `compare_cultures` | Side-by-side cultural comparison between any two countries |
| `get_communication_style` | Communication preferences, negotiation styles, and business protocol for any culture |
| `get_holiday_calendar` | Cultural and religious holidays, observances, and scheduling considerations |
| `analyze_hofstede` | Hofstede's 6 cultural dimensions analysis with scores and business implications |
| `compare_hofstede` | Compare Hofstede dimension scores between two countries |
| `get_geopolitical_heatmap` | Geopolitical risk analysis with adaptive EWA scoring across 12 risk categories |

### Multimodal & Streaming Endpoints

| Endpoint | Description |
|----------|-------------|
| `WSS /api/v1/streaming/analyze` | **Real-time Streaming:** Analyze video frames in real-time via WebSocket connection for live broadcasts and conferencing |
| `POST /api/v1/analyze/image` | Analyze images for cultural sensitivity including visual taboos, symbols, colors, and gestures |
| `POST /api/v1/analyze/video` | Analyze video content for cultural compliance across target markets |
| `POST /api/v1/upload/image` | Upload images for cultural analysis |
| `POST /api/v1/upload/video` | Upload video for cultural analysis |

### Report Generation

| Endpoint | Description |
|----------|-------------|
| `POST /api/v1/reports/generate` | Generate branded, boardroom-ready PDF cultural audit reports |

---

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

### Option 7: npm

```bash
npx @kultur-dev/mcp-server
```

### Option 8: pip

```bash
pip install kultur-mcp
```

---

## REST & Streaming API

For non-MCP integrations, Kultur.dev provides a comprehensive REST and WebSocket API:

### Text Analysis

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/v1/analyze/text` | POST | Cultural context analysis |
| `/api/v1/analyze/hofstede` | POST | Hofstede dimensions analysis |
| `/api/v1/analyze/hofstede/compare` | POST | Compare Hofstede scores between countries |
| `/api/v1/rewrite` | POST | Culturally-aware text rewriting |
| `/api/v1/sensitivity/check` | POST | Cultural sensitivity scanning |
| `/api/v1/localization/guidance` | POST | Localization recommendations |
| `/api/v1/geopolitical/heatmap` | POST | Geopolitical risk scoring |

### Multimodal & Streaming Analysis

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/v1/streaming/analyze` | WSS | **Real-time video frame analysis via WebSocket** |
| `/api/v1/analyze/image` | POST | Analyze images for cultural sensitivity |
| `/api/v1/analyze/video` | POST | Analyze video for cultural compliance |
| `/api/v1/upload/image` | POST | Upload image for analysis |
| `/api/v1/upload/video` | POST | Upload video for analysis |

### Reports

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/v1/reports/generate` | POST | Generate branded PDF cultural audit reports |

### Example: Real-time Streaming (WebSocket)

```javascript
const socket = new WebSocket('wss://kultur.dev/api/v1/streaming/analyze');

socket.onopen = () => {
  socket.send(JSON.stringify({
    "auth_token": "YOUR_API_KEY",
    "target_country": "SA",
    "frame_data": "base64_encoded_frame"
  }));
};

socket.onmessage = (event) => {
  const analysis = JSON.parse(event.data);
  console.log('Real-time Cultural Risk:', analysis.risk_score);
};
```

---

## Authentication

All requests require a valid API key passed as a Bearer token:

```
Authorization: Bearer YOUR_API_KEY
```

### Get Your API Key

1. Visit [kultur.dev](https://kultur.dev)
2. Sign up for a plan
3. Copy your API key from the dashboard

---

## Pricing

| Plan | Credits | Markets | Price |
|------|---------|---------|-------|
| **Free** | 1,000/month | 3 countries | $0 |
| **Pro** | 10,000/month | All 200+ markets | $49/month |
| **Enterprise** | Unlimited | All + custom models | Contact us |

Free tier includes full access to all tools including multimodal analysis. Pro and Enterprise tiers provide clean, production-ready responses and access to **Real-time Streaming** endpoints.

---

## Use Cases

**For Podcasters & Broadcasters:** Real-time cultural monitoring of live video feeds to ensure global brand safety. Instant alerts for visual taboos or sensitive gestures during live streaming.

**For AI Agents & LLMs:** Cultural context injection before generating responses about specific countries. Real-time sensitivity checking on AI-generated content (text, images, and video). Localization guidance for multi-market content generation. Visual content screening before publishing to international audiences.

**For Global Enterprises:** CRM systems that adapt communication style per market. Marketing teams launching campaigns across culturally diverse regions. E-commerce platforms expanding internationally with culturally appropriate imagery. Compliance teams ensuring brand safety across all regions. HR platforms with cultural onboarding intelligence.

**For Developers:** Add cultural awareness to any application in minutes. Hofstede dimensions for academic and business research. Geopolitical risk scoring for supply chain and investment analysis. Multimodal content screening pipelines.

---

## Who Needs Kultur.dev

Every AI agent operating across borders. Every global marketing team. Every e-commerce platform expanding internationally. Every content platform serving diverse audiences. Every localization team that needs more than translation. They need cultural adaptation. Every compliance team responsible for brand safety across regions.

The cost of a cultural mistake is measured in millions. The cost of preventing one is an API call.

---

## Server Discovery

The MCP server card is available at:

```
https://kultur.dev/.well-known/mcp/server-card.json
```

OpenAPI specification:

```
https://kultur.dev/api/openapi-spec.json
```

---

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

---

## Support

**Documentation:** [kultur.dev/docs](https://kultur.dev/docs) | **Email:** contact@kultur.dev | **Issues:** [GitHub Issues](https://github.com/kultur-dev/mcp-server/issues)

## License

MIT License. See [LICENSE](LICENSE) for details.

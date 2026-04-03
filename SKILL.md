# Kultur.dev MCP Server Skill

## Description

Kultur.dev is the world's first multimodal cultural intelligence infrastructure for AI agents. This MCP server provides 9 specialized tools plus image and video analysis endpoints for cultural risk assessment, sensitivity checking, localization guidance, Hofstede cultural dimensions, geopolitical risk scoring, and branded PDF report generation, covering 200+ markets and 50+ languages.

Unlike text-only solutions, Kultur.dev analyzes images for visual taboos (colors, symbols, gestures) and video content for cultural compliance across regions. It generates boardroom-ready PDF cultural audit reports, not raw JSON.

## Connection

**Transport:** SSE (Server-Sent Events)
**Endpoint:** `https://kultur.dev/api/mcp-sse/sse`
**Authentication:** Bearer token via `Authorization` header

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `KULTUR_API_KEY` | Yes | Your Kultur.dev API key. Get one free at [kultur.dev](https://kultur.dev) |

## Tools

### analyze_cultural_context
Performs deep cultural analysis for a target country, including values, taboos, business etiquette, and communication norms.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `text` | string | yes | The text or scenario to analyze |
| `target_country` | string | yes | ISO 3166-1 alpha-2 country code (e.g., "JP", "DE", "BR") |
| `source_country` | string | no | Source country for cross-cultural comparison |

### check_cultural_sensitivity
Scans text for potential cultural sensitivity issues, returning severity scores and suggested fixes.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `text` | string | yes | The text to check for sensitivity issues |
| `target_countries` | array of strings | yes | ISO country codes to check against |

### get_localization_guidance
Provides localization recommendations for adapting content to a target market across 15 tones: formal, humble, celebratory, respectful, casual, neutral, professional, friendly, humorous, marketing, legal, medical, technical, academic, and diplomatic.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `text` | string | yes | The text to localize |
| `target_country` | string | yes | ISO country code |
| `tone` | string | no | One of: formal, humble, celebratory, respectful, casual, neutral, professional, friendly, humorous, marketing, legal, medical, technical, academic, diplomatic |

### compare_cultures
Side-by-side cultural comparison between two countries covering communication styles, business practices, social norms, and values.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country_a` | string | yes | First ISO country code |
| `country_b` | string | yes | Second ISO country code |

### get_communication_style
Returns communication preferences, negotiation styles, meeting etiquette, and business protocol for a specific culture.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country` | string | yes | ISO country code |

### get_holiday_calendar
Returns cultural and religious holidays, national observances, and scheduling considerations for a country.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country` | string | yes | ISO country code |
| `year` | integer | no | Calendar year (defaults to current year) |

### analyze_hofstede
Analyzes Hofstede's 6 cultural dimensions (Power Distance, Individualism, Masculinity, Uncertainty Avoidance, Long-Term Orientation, Indulgence) with scores and business implications.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country` | string | yes | ISO country code |

### compare_hofstede
Compares Hofstede dimension scores between two countries with gap analysis and practical implications.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country_a` | string | yes | First ISO country code |
| `country_b` | string | yes | Second ISO country code |

### get_geopolitical_heatmap
Provides geopolitical risk analysis using an adaptive Exponentially Weighted Average (EWA) scoring framework across 12 risk categories including political stability, economic risk, security threats, and regulatory environment.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country` | string | yes | ISO country code |
| `categories` | array of strings | no | Specific risk categories to analyze |

## Multimodal Endpoints

In addition to the 9 MCP tools above, Kultur.dev provides multimodal analysis via REST API:

| Endpoint | Description |
|----------|-------------|
| `POST /api/v1/analyze/image` | Analyze images for cultural sensitivity including visual taboos, symbols, colors, gestures |
| `POST /api/v1/analyze/video` | Analyze video content for cultural compliance across target markets |
| `POST /api/v1/reports/generate` | Generate branded, boardroom-ready PDF cultural audit reports |

## Example Usage

When connected to an MCP client like Claude Desktop, Cursor, or Windsurf, you can use natural language:

> "Analyze the cultural context for expanding our SaaS product into Japan"

> "Check if this marketing copy is culturally appropriate for Saudi Arabia and Iran"

> "Compare the business cultures of Germany and Brazil"

> "What are the Hofstede dimensions for South Korea?"

> "What's the geopolitical risk profile for Nigeria?"

> "Analyze this campaign image for cultural sensitivity in the Middle East"

> "Generate a PDF cultural audit report for our product launch in India"

## Pricing

The Free plan includes 1,000 credits/month covering 3 countries. Pro ($49/month) unlocks all 200+ markets with 10,000 credits. Enterprise plans offer unlimited access with custom models.

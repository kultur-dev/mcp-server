# Kultur.dev MCP Server Skill

## Description

Kultur.dev is the world's cultural intelligence infrastructure layer for AI agents. This MCP server provides 9 tools for cultural analysis, sensitivity checking, localization guidance, Hofstede cultural dimensions, and geopolitical risk assessment across 195+ countries and 50+ languages.

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

**Parameters:**
- `text` (string, required): The text or scenario to analyze
- `target_country` (string, required): ISO 3166-1 alpha-2 country code (e.g., "JP", "DE", "BR")
- `source_country` (string, optional): Source country for cross-cultural comparison

### check_cultural_sensitivity

Scans text for potential cultural sensitivity issues, returning severity scores and suggested fixes.

**Parameters:**
- `text` (string, required): The text to check for sensitivity issues
- `target_countries` (array of strings, required): ISO country codes to check against

### get_localization_guidance

Provides localization recommendations for adapting content to a target market across 9 tones: formal, casual, marketing, legal, medical, technical, academic, diplomatic, and humorous.

**Parameters:**
- `text` (string, required): The text to localize
- `target_country` (string, required): ISO country code
- `tone` (string, optional): One of: formal, casual, marketing, legal, medical, technical, academic, diplomatic, humorous

### compare_cultures

Side-by-side cultural comparison between two countries covering communication styles, business practices, social norms, and values.

**Parameters:**
- `country_a` (string, required): First ISO country code
- `country_b` (string, required): Second ISO country code

### get_communication_style

Returns communication preferences, negotiation styles, meeting etiquette, and business protocol for a specific culture.

**Parameters:**
- `country` (string, required): ISO country code

### get_holiday_calendar

Returns cultural and religious holidays, national observances, and scheduling considerations for a country.

**Parameters:**
- `country` (string, required): ISO country code
- `year` (integer, optional): Calendar year (defaults to current year)

### analyze_hofstede

Analyzes Hofstede's 6 cultural dimensions (Power Distance, Individualism, Masculinity, Uncertainty Avoidance, Long-Term Orientation, Indulgence) with scores and business implications.

**Parameters:**
- `country` (string, required): ISO country code

### compare_hofstede

Compares Hofstede dimension scores between two countries with gap analysis and practical implications.

**Parameters:**
- `country_a` (string, required): First ISO country code
- `country_b` (string, required): Second ISO country code

### get_geopolitical_heatmap

Provides geopolitical risk analysis using an adaptive Exponentially Weighted Average (EWA) scoring framework across 12 risk categories including political stability, economic risk, security threats, and regulatory environment.

**Parameters:**
- `country` (string, required): ISO country code
- `categories` (array of strings, optional): Specific risk categories to analyze

## Example Usage

When connected to an MCP client like Claude Desktop, Cursor, or Windsurf, you can use natural language:

> "Analyze the cultural context for expanding our SaaS product into Japan"

> "Check if this marketing copy is culturally appropriate for Saudi Arabia and Iran"

> "Compare the business cultures of Germany and Brazil"

> "What are the Hofstede dimensions for South Korea?"

> "What's the geopolitical risk profile for Nigeria?"

## Pricing

The Free plan includes 1,000 credits/month covering 3 countries. Pro ($49/month) unlocks all 195 countries with 50,000 credits. Enterprise plans offer unlimited access with custom models.

# Kultur.dev MCP Server Skill

## Description

Kultur.dev is the world's first multimodal cultural intelligence infrastructure for AI agents. This MCP server provides 9 specialized tools plus image, video, and real-time WebSocket streaming analysis endpoints for cultural risk assessment, sensitivity checking, localization guidance, Hofstede cultural dimensions, geopolitical risk scoring, and branded PDF report generation, covering 200+ markets and 50+ languages.

Unlike text-only solutions, Kultur.dev analyzes images for visual taboos (colors, symbols, gestures) and video content for cultural compliance across regions. It supports real-time WebSocket streaming for live video analysis (ideal for podcasters and live broadcasters) and generates boardroom-ready PDF cultural audit reports.

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
| `target_country` | string | yes | ISO country code |

### get_holiday_calendar

Returns cultural and religious holidays, observances, and scheduling considerations for a specific country and year.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `target_country` | string | yes | ISO country code |
| `year` | integer | no | Year to check (default: current year) |

### analyze_hofstede

Analyzes Hofstede's 6 cultural dimensions for a country, providing scores and business implications.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `target_country` | string | yes | ISO country code |

### compare_hofstede

Compares Hofstede dimension scores between two countries with analysis of cultural distance.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `country_a` | string | yes | First ISO country code |
| `country_b` | string | yes | Second ISO country code |

### get_geopolitical_heatmap

Returns geopolitical risk analysis with adaptive EWA scoring across 12 risk categories for a target region.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `region` | string | yes | Target region or country code |

## Streaming & Multimodal Endpoints

### WebSocket Streaming Analysis

Analyze video frames in real-time via WebSocket connection. Ideal for live video feeds, podcast moderation, or real-time broadcast analysis.

| Endpoint | Method | Credits |
|----------|--------|---------|
| `WSS /api/v1/streaming/analyze` | WebSocket | 5 credits/call |

### Image & Video Analysis

| Endpoint | Method | Credits |
|----------|--------|---------|
| `/api/v1/analyze/image` | POST | 5 credits/call |
| `/api/v1/analyze/video` | POST | 20 credits/call |

## Reports

### PDF Report Generation

Generate branded, boardroom-ready PDF cultural audit reports.

| Endpoint | Method | Credits |
|----------|--------|---------|
| `/api/v1/reports/generate` | POST | 1 credit/call |

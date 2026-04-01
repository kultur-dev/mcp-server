# Zapier Integration Guide

## Using Kultur.dev with Zapier Webhooks

Kultur.dev can be integrated into any Zapier workflow using the **Webhooks by Zapier** action.

### Step 1: Add a Webhook Action

In your Zap, add a new action and select **Webhooks by Zapier** with the event type **Custom Request**.

### Step 2: Configure the Request

| Field | Value |
|-------|-------|
| Method | POST |
| URL | `https://kultur.dev/api/v1/analyze/text` |
| Headers | `Authorization: Bearer YOUR_API_KEY` and `Content-Type: application/json` |
| Data | `{"text": "your text here", "target_country": "JP"}` |

### Available Endpoints

Use any of the Kultur.dev REST endpoints in your Zapier webhooks. Refer to the main README for the full endpoint list.

---
title: Getting Started
deprecated: false
hidden: false
metadata:
  robots: index
---
# Getting Started with SignalBridge

Welcome to SignalBridge, a fictional messaging API for sending messages and tracking delivery status.

## 1. Authenticate

SignalBridge uses bearer token authentication. Include your API token in the `Authorization` header.

```bash
Authorization: Bearer YOUR_API_TOKEN
```

## 2. Send your first message

Submit a POST request to `/messages`:

```bash
curl -X POST https://api.signalbridge.example/v1/messages \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "to": "+12155550123",
    "body": "Your appointment is confirmed."
  }'
```

A successful request returns `202 Accepted`:

```json
{
  "messageId": "msg_12345",
  "status": "queued"
}
```

This means your message has been accepted for processing, not necessarily delivered.

## 3. Check message status

Use the returned message ID:

```bash
curl https://api.signalbridge.example/v1/messages/msg_12345 \
  -H "Authorization: Bearer YOUR_API_TOKEN"
```

Possible statuses include `queued`, `sent`, `delivered`, and `failed`.

## 4. Troubleshooting

- **400:** Check your request fields and formatting.
- **401:** Verify your bearer token.
- **429:** Reduce request frequency and implement backoff.
- **503:** The service is temporarily unavailable.

## Next steps

Explore the API Reference for complete endpoint definitions, parameters, and response schemas.

_Note: SignalBridge is a demonstration API. These requests will not reach a working server._

<br />

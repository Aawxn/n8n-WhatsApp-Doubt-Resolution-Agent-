# Development Challenges

## 1. WhatsApp Webhook Registration

Initially the webhook was not registered correctly because the production URL had not been activated.

Solution:
- Activated workflow
- Registered production webhook

---

## 2. Temporary Access Tokens

Meta temporary access tokens expired every 24 hours.

Solution:
- Generated permanent System User access token.

---

## 3. Base64 Conversion

Gemini Vision rejected uploaded images due to incorrect Base64 encoding.

Solution:
- Added JavaScript Code Node
- Converted binary image to valid Base64
- Corrected JSON payload

---

## 4. AI Workflow Design

Routing Gemini Vision output into another AI Agent caused conversational summarization instead of educational responses.

Solution:
- Created independent image reasoning pipeline.

---

## 5. WhatsApp Formatting

Gemini initially generated markdown-heavy responses.

Solution:
- Prompt engineered concise mobile-friendly educational responses.
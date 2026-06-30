# System Architecture

The system is divided into two independent AI pipelines.

## Text Pipeline

User
↓
WhatsApp Cloud API
↓
n8n Workflow
↓
AI Agent
↓
Simple Memory
↓
Gemini Chat Model
↓
WhatsApp Response

---

## Image Pipeline

User
↓
WhatsApp Cloud API
↓
Download Media
↓
Base64 Conversion
↓
Gemini Vision
↓
Format Response
↓
WhatsApp Response

---

## Why Separate Pipelines?

During development, image responses were initially routed through the conversational AI Agent.

This produced undesirable meta-responses such as:

"Thanks for sharing this image..."

instead of answering the academic question.

The final architecture therefore processes images directly using Gemini Vision while retaining conversational memory only for text interactions.
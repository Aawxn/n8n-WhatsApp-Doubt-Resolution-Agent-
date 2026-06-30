# Setup & Deployment Guide

This guide explains how to set up the n8n workflow, configure WhatsApp Cloud API, and integrate Gemini.

## Prerequisites

1. **Meta Developer Account**: Access to [Meta App Dashboard](https://developers.facebook.com/).
2. **n8n Instance**: An active n8n instance (Cloud or self-hosted).
3. **Google Gemini API Key**: An API key from [Google AI Studio](https://aistudio.google.com/).

---

## Step 1: Set Up Meta WhatsApp Cloud API

1. Go to the Meta App Dashboard and click **Create App** (Select type: **Other** -> **Business**).
2. Under "Add products to your app", locate **WhatsApp** and click **Set up**.
3. Under WhatsApp settings:
   - Make note of your **Temporary Access Token** (generate a permanent one later via system users in Business Manager).
   - Find your **Phone Number ID** and **WhatsApp Business Account ID**.
4. Go to **WhatsApp** -> **Configuration** in the sidebar.
   - You will configure the **Webhook URL** and **Verify Token** here after setting up n8n.

---

## Step 2: Import the n8n Workflow

1. Open your n8n workspace.
2. Create a new workflow, click the three dots in the top right, and select **Import from File**.
3. Select the [workflow.json](../workflow.json) file from this repository.
4. Set up the nodes with your credentials:
   - **Gemini Pro API Key**: Replace the query parameter `YOUR_GEMINI_API_KEY` in the Gemini HTTP Request node URL.
   - **WhatsApp Bearer Token**: In the HTTP Request nodes (both the metadata URL retrieval and binary image download), set the header `Authorization` to `Bearer YOUR_WHATSAPP_TOKEN`.

---

## Step 3: Configure Webhooks

1. Save the workflow in n8n.
2. Copy the **Production URL** or **Test URL** from the n8n WhatsApp Trigger node.
3. Return to the Meta App Dashboard -> **WhatsApp** -> **Configuration**.
4. Click **Edit** under Webhooks:
   - Paste the n8n Webhook URL.
   - Enter your chosen **Verify Token** (must match what you set in Meta).
5. Click **Verify and Save**.
6. Under Webhook fields, click **Manage** and subscribe to **messages**.

---

## Step 4: Active and Test

1. Toggle the n8n workflow switch to **Active**.
2. Add a test phone number in the Meta developer panel.
3. Send a text or an image containing an academic query to your test WhatsApp number.
4. Verify n8n execution log to see the request passing through the active pipeline and generating responses.
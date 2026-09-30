# 🤖 AI-Powered Full Stack Appointment Booking Agent

An automated, intelligent doctor appointment booking workflow built using **n8n**, **LangChain**, **Telegram Bot API**, **Google Sheets**, and **Stripe**. 

This system acts as a smart AI assistant for clinics and medical shops, capable of dynamic slot management, patient registration, payment link generation, appointment rescheduling, cancellation, and automated refunds.

---

## 🌟 Key Features

- 🤖 **AI Assistant (n8n + LangChain + OpenRouter/GPT-4o)**: Interactive conversational flow to guide users through booking step-by-step.
- 📱 **Multi-Channel Interaction**: Integrated with **Telegram** (and extensible to WhatsApp via Webhooks).
- 📅 **Dynamic Slot & Date Management**:
  - Automatically calculates available slots for the next 7 days based on real-time system context.
  - Excludes fully booked slots, past time slots, and clinic holiday/break schedules configured in Google Sheets.
- 👨‍👩‍👧 **Patient Management**: Supports multiple patient profiles under a single contact number.
- 💳 **Integrated Payments & Refunds**:
  - **Stripe Checkout**: Automatically generates payment links for online orders.
  - **Automated Refund Processing**: Automatically processes Stripe refunds upon appointment cancellation.
  - **Cash on Clinic Option**: Offers offline payment options.
- 📊 **Google Sheets as Database**: Real-time synchronization across 3 sheets (`Patients`, `Appointments`, and `Config`).

---

## 📐 System Architecture & Workflow Overview

The architecture consists of **3 primary workflow pipelines**:

```text
 ┌────────────────┐       ┌────────────────┐       ┌─────────────────┐
 │ Telegram User  │ ────> │  n8n AI Agent  │ ────> │  Google Sheets  │
 └────────────────┘       └────────────────┘       └─────────────────┘
                                   │                        │
                                   ▼                        ▼
                          ┌────────────────┐       ┌─────────────────┐
                          │ Stripe Gateway │ <──── │ Payment Webhook │
                          └────────────────┘       └─────────────────┘

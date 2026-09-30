<div align="center">

# 🤖 Full-Stack AI Appointment Booking Agent

**An Autonomous, Multi-Channel AI Assistant Powered by n8n, LangChain, Telegram & Stripe**

[![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-FF6D5A?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![LangChain](https://img.shields.io/badge/LangChain-AI_Agent_Framework-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white)](https://www.langchain.com/)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o_Mini-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com/)
[![Telegram](https://img.shields.io/badge/Telegram-Bot_API-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://core.telegram.org/bots)
[![Stripe](https://img.shields.io/badge/Stripe-Payments_&_Refunds-635BFF?style=for-the-badge&logo=stripe&logoColor=white)](https://stripe.com/)
[![Google Sheets](https://img.shields.io/badge/Google_Sheets-Database-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)](https://workspace.google.com/)

</div>

---

## 📌 Executive Summary

The **AI Appointment Booking Agent** is an end-to-end automated system designed for clinics, medical shops, and service businesses. Built on **n8n** and powered by **LangChain (GPT-4o-mini)**, it automates patient registration, date/time slot validation, dynamic payment link generation via **Stripe**, and automated instant refunds upon cancellation—all managed in real-time through **Telegram** and backed by **Google Sheets**.

---

## 🔥 Key Features & Capabilities

| Feature | Description |
| :--- | :--- |
| 🤖 **Conversational AI Agent** | Stateful multi-turn conversation memory (`BufferWindowMemory`) via LangChain to guide users seamlessly. |
| 📅 **Dynamic Slot Management** | Generates real-time available time slots for 7 rolling days. Excludes fully booked slots, past hours, and holiday schedules. |
| 👨‍👩‍👧 **Multi-Patient Profiles** | Linked to a single messaging account—allowing users to manage bookings for multiple family members. |
| 💳 **Integrated Stripe Payments** | Automatically creates dynamic checkout links for online payments (`$50.00`) or allows "Cash at Clinic". |
| 🔄 **Instant Automated Refunds** | Detects booking cancellations in real time and automatically triggers full refunds via the Stripe API. |
| 📊 **Serverless Cloud Database** | Uses 3 separate Google Sheet layers (`Patients`, `Booking`, `Config`) for lightweight, structured storage. |

---

## 🏗️ System Architecture & Workflow Pipeline

The project is structured into **3 core automated workflow pipelines**:

```text
                                  +-----------------------+
                                  |   Telegram / Webhook  |
                                  +-----------+-----------+
                                              |
                                              v
                                  +-----------------------+
                                  | n8n AI Agent Engine   |
                                  | (LangChain Memory)    |
                                  +-----------+-----------+
                                              |
                     +------------------------+------------------------+
                     |                                                 |
                     v                                                 v
        +-------------------------+                       +-------------------------+
        |  Google Sheets Database |                       |  Stripe Payment Gateway |
        | (Patients, Booking, Conf|                       |  (Checkout & Refunds)   |
        +-------------------------+                       +-------------------------+

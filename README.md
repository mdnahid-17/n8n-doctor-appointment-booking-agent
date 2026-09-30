🤖 Full Stack AI Appointment Booking Agent

An intelligent, full-stack AI conversational agent built with n8n, OpenAI/LangChain, Telegram/WhatsApp, Google Sheets, and Stripe. This solution automates doctor/clinic appointment bookings, patient registration, dynamic slot scheduling, automated payment collection, and instant payment refunds on booking cancellations.

✨ Features

💬 Interactive Chat Interface: Seamless integration with Telegram (and expandable to WhatsApp) using n8n workflows.

🤖 Context-Aware AI Agent: Powered by LangChain and GPT-4o-Mini with persistent memory to guide users step-by-step.

📋 Patient Management: Register new patients or select existing profiles attached to a user ID.

📅 Dynamic Slot Management:

Automatically calculates upcoming 7 days.

Excludes fully booked slots, past time slots, and blocked ranges set in configuration.

💳 Payment Processing: Integrated Stripe Checkout API for online payments with automatic payment confirmation & receipt sending.

🔄 Reschedule & Cancel Flow: Allows patients to view, reschedule, or cancel existing appointments.

💸 Automated Refunds: Triggers automatic Stripe refunds when an online-paid appointment is cancelled.

📊 Google Sheets as Backend Database: Lightweight and structured DB architecture utilizing Sheets for Patients, Appointments, and Config settings.

🏗 System Architecture & Workflow

The architecture is split into three main n8n workflow engines:

Conversational Engine (Core AI Agent):
Handles user interaction, state management, slot availability calculations, patient registration, and appointment record creation.

Payment Engine (Stripe Integration):
Monitors new bookings requiring online payment, generates dynamic Stripe Checkout URLs, sends payment buttons to Telegram/WhatsApp, and updates booking status upon successful webhook completion.

Refund Engine (Automation):
Listens for cancellation updates in Google Sheets, checks if a Stripe Payment Intent exists, triggers the Stripe Refund API, and notifies the user.

📊 Database Schema (Google Sheets)

The project uses a Google Spreadsheet with three primary sheets:

1. Patients

Column Name

Type

Description

patient_id

String

Unique Identifier (PAT-XXXXXX)

User ID

String

Telegram/WhatsApp Chat ID

What's up number

String

Contact phone number

Name

String

Patient full name

Age

Number

Patient age

Gender

String

Gender (Male/Female/Other)

2. Booking (Appointments)

Column Name

Type

Description

Appoinment_id

String

Unique Booking ID (APT-XXXXXX)

Patience_id

String

Reference to Patient User ID

Date & Time

String

Booking timestamp (YYYY-MM-DD HH:MM)

Payment Method

String

Stripe or Cash at Clinic

Payment Status

String

Paid, Not paid, Pending, or Refund

Status

String

Confirmed, Cancelled, Rescheduled, or Refund

Payment Stripe Details

String

Stripe Payment Intent ID

3. Config

Key

Value Example

Description

working_hours

10:00-18:00

Daily operational clinic hours

not_available

2026-10-05 10:00 to 12:00

Custom blocked slots

🛠️ Prerequisites & Setup

Requirements

n8n (Self-hosted or Cloud instance)

OpenAI / OpenRouter API Key (for gpt-4o-mini model)

Telegram Bot Token (via @BotFather)

Google Cloud Console setup with Google Sheets API access

Stripe Account (API Keys & Webhook secrets)

Installation Guide

Clone the Repository:

git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name


Import Workflow into n8n:

Open your n8n dashboard.

Click Workflows > Import from File.

Select the Full_Stack_Apoinment_Booking_Agent_GitHub_Safe.json file.

Configure Credentials in n8n:

Add Telegram API credential.

Add OpenRouter/OpenAI credential.

Add Google Sheets OAuth2 credential.

Add Stripe API Key / Header Authentication.

Setup Google Spreadsheet:

Create a Google Sheet containing three tabs: Patients, Booking, and Config.

Update the Spreadsheet ID in the Google Sheets nodes within n8n.

Activate the Workflows:

Enable the triggers (Telegram Trigger, Google Sheets Triggers, Stripe Trigger).

Save and set the workflow to Active.

🛠️ Built With

n8n - Workflow Automation Platform

LangChain / AI Agent - Conversational Logic & Tool Calling

Google Sheets API - Lightweight Database

Stripe API - Payment Gateway & Automated Refunds

Telegram Bot API - User Interface

📝 License

This project is open-source and available under the MIT License.

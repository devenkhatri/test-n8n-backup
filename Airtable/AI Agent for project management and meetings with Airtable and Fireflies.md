# Workflow Analysis for AI-powered Meeting Transcript Processor with Automated Task Creation, Client Notification, and Follow-up Scheduling

## Description
When a meeting ends, Fireflies sends a webhook; the workflow pulls the transcript, uses GPT‑4o to decide if it’s a project meeting, then automatically creates tasks in Airtable, emails each participant their action items, and schedules a Google Meet if a follow‑up call is needed.

## Input Details
Triggered by a POST webhook containing a meetingId, which is used to fetch the meeting transcript from Fireflies.

## Process Summary
1. The webhook receives the meetingId and the Get Meeting Content node queries Fireflies GraphQL API to retrieve transcript details. 2. The AI Agent sends the transcript to OpenAI GPT‑4o with a system prompt that instructs it to create tasks, notify clients, and schedule calls as needed. 3. If tasks are generated, the Create Tasks tool invokes a sub‑workflow that splits the task array and creates each task as a new record in an Airtable table. 4. The Notify Client About Tasks tool emails each participant (except the user) the meeting summary and their specific action items. 5. If a follow‑up call is required, the Create Event tool adds a Google Calendar event with a Meet link using the AI‑provided details.

## Output Details
Creates task records in Airtable, sends participant emails, and optionally adds Google Calendar events.

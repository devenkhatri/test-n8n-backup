# Workflow Analysis for AI‑Driven Meeting Transcript Processor: Auto‑Create Airtable Tasks, Email Clients, and Schedule Follow‑up Calls

## Description
This workflow listens for completed meeting notifications from Fireflies, pulls the transcript, uses GPT‑4o to analyze it, automatically creates project tasks in Airtable, emails participants their action items, and sets up Google Meet events when a follow‑up call is required.

## Input Details
Triggered by a POST webhook from Fireflies that provides a meetingId, which is used to fetch the meeting transcript via Fireflies GraphQL API.

## Process Summary
The webhook receives the meeting ID and the Get Meeting Content node queries Fireflies for the transcript, participants and summary. The AI Agent node feeds this data to an OpenAI GPT‑4o model with a system prompt that instructs it to detect project‑related meetings and invoke tools. If the meeting is about a project, the agent calls the “Create Tasks” tool, which runs a sub‑workflow that splits the task list and creates individual records in Airtable. The agent also calls the “Notify Client About Tasks” Gmail tool to email each participant (except the user) their summary and personal action items. When the transcript indicates a required follow‑up call, the agent uses the “Create Event” Google Calendar tool to schedule a Google Meet with the provided details.

## Output Details
Creates task records in Airtable, sends email notifications via Gmail, and optionally adds a Google Calendar event.

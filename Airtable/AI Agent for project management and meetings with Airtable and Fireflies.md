# Workflow Analysis for AI‑Driven Meeting Transcript Processor with Airtable Tasks, Email Notifications, and Calendar Events

## Description
When a Fireflies meeting finishes, this workflow automatically pulls the transcript, lets an AI decide if it concerns a project, creates actionable tasks in Airtable, emails each participant their personal action items, and schedules follow‑up calls in Google Calendar when needed.

## Input Details
Triggered by a POST webhook from Fireflies that supplies a meetingId for the completed meeting.

## Process Summary
The webhook receives the meetingId and a GraphQL request fetches the transcript, participants and a bullet‑point summary; the transcript is sent to an AI Agent (GPT‑4o) which, based on its system prompt, determines if the meeting is project‑related and then calls three tool nodes – Create Tasks, Notify Client About Tasks, and Create Event; the Create Tasks tool launches a sub‑workflow that splits the task list and creates each task as a record in Airtable; the Notify Client tool emails each participant their specific tasks and the meeting summary; the Create Event tool adds a Google Meet event when a follow‑up call is required.

## Output Details
Creates task records in Airtable, sends summary emails via Gmail, and optionally adds Google Calendar events.

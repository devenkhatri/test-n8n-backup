# Workflow Analysis for AI-Powered Meeting Transcript Processor with Airtable Tasks, Email Notifications, and Google Calendar Events

## Description
When a meeting finishes, this workflow automatically pulls the transcript from Fireflies, uses an AI agent to understand the discussion, creates actionable tasks in Airtable, emails each participant their specific tasks, and schedules follow‑up calls in Google Calendar if required.

## Input Details
A POST webhook from Fireflies supplies the meetingId, which triggers the workflow.

## Process Summary
1) The webhook triggers an HTTP request that fetches the meeting transcript, title, participants and summary from Fireflies via GraphQL. 2) The AI Agent receives this data, evaluates whether the meeting is project‑related, and decides which tools to invoke. 3) If tasks are needed, the Agent calls the "Create Tasks" tool, which runs a sub‑workflow that splits the task list and creates records in Airtable. 4) The Agent then uses the "Notify Client About Tasks" tool to email each participant (excluding the user) their personal action items along with the meeting summary. 5) If the transcript indicates a follow‑up call, the Agent invokes the "Create Event" tool to add a Google Meet event to the calendar.

## Output Details
The workflow creates task entries in Airtable, sends personalized task summary emails via Gmail, and optionally adds a Google Calendar event.

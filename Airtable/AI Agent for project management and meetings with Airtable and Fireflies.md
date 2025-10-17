# Workflow Analysis for $input.first().json.output.title

## Description
$input.first().json.output.description

## Input Details
Triggered by a POST webhook that supplies a meetingId, which is used to fetch the transcript from Fireflies.

## Process Summary
The webhook receives the meetingId and passes it to the Get Meeting Content node, which queries Fireflies GraphQL API for the transcript, participants and summary. The transcript data is fed to the AI Agent node, which uses GPT‑4o with a system prompt that instructs it to detect project‑related meetings and decide which tools to invoke. If the meeting is about a project, the AI calls the “Create Tasks” tool, triggering a sub‑workflow that splits each task item and creates a record in the specified Airtable base. The AI then calls the “Notify Client About Tasks” Gmail tool to email each participant (except the user) a summary and their personal action items. If the transcript indicates a required follow‑up call, the AI calls the “Create Event” Google Calendar tool to schedule a Google Meet with the appropriate details.

## Output Details
Creates task records in Airtable, sends task summary emails via Gmail, and optionally adds a Google Calendar event with a Meet link.

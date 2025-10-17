# Workflow Analysis

## Input Details
A POST webhook receives a Fireflies meeting ID, which is used to fetch the meeting transcript via the Fireflies GraphQL API.

## Process Summary
1. The webhook triggers the workflow and passes the meeting ID to a GraphQL request that retrieves the transcript, title, participants and a bullet‑point summary. 2. An AI Agent (GPT‑4o) analyses the transcript; if the title contains "project" it calls three AI‑tools: "Create Tasks" to generate structured task objects, "Notify Client About Tasks" to email each participant their action items, and "Create Event" to schedule a follow‑up Google Meet when required. 3. The "Create Tasks" tool invokes a sub‑workflow that splits the task list and creates a record for each task in an Airtable base. 4. The Gmail tool sends the summary and participant‑specific tasks to each participant (excluding the user). 5. If a follow‑up call is indicated, the Google Calendar tool creates a calendar event with a Meet link.

## Output Details
The workflow creates task records in Airtable, sends email notifications to participants, and optionally adds a Google Calendar event for a follow‑up meeting.

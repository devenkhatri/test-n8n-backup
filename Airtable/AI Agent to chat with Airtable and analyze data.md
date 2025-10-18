# Workflow Analysis for Airtable AI Chat and Data Analysis Agent

## Description
This workflow enables an AI agent to interact conversationally with Airtable data. Users can retrieve information, execute mathematical functions for data analysis, and optionally generate maps for geographic data visualization, reducing the need for manual navigation and complex queries.

## Input Details
The workflow is triggered by an incoming chat message, receiving user queries for data interaction.

## Process Summary
First, the AI agent receives a chat message, processes it through an OpenAI chat model and uses a window buffer memory to retain context. Based on the user's request, it dynamically calls sub-workflows (tools) to either fetch a list of Airtable bases, get a base's table schema, search for records with optional filtering and sorting, or process data with code for mathematical functions and image generation. If a filter description is provided for record search, it is sent to OpenAI to generate a search filter. Finally, for code-based data processing, it interacts with the OpenAI Assistant API to create a thread, send messages, run the assistant, and retrieve responses, including downloading any generated image files.

## Output Details
The workflow produces structured data or text responses from Airtable, analyzed data from code processing, or image links for generated maps, returning these results directly to the user who initiated the chat message.

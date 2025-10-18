# Workflow Analysis for AI-Powered Job Application Workflow

## Description
This workflow automates a two-step job application process using AI to extract and pre-fill candidate information, streamlining the submission and data capture for HR teams.

## Input Details
The workflow is triggered by an applicant submitting a form with their name, a resume file (PDF), and an acknowledgment of terms in the "Step 1 of 2 - Upload CV" form.

## Process Summary
First, the workflow extracts text from the uploaded PDF resume. It then classifies the document to ensure it is a CV; if not, the applicant is prompted to re-upload. Subsequently, an AI model extracts relevant information from the CV based on a provided job description and structures it. This extracted data, along with the original PDF, is then saved to an Airtable database. Following this, the applicant is redirected to a second application form with the extracted details pre-filled. Finally, upon submission of the second form, the updated applicant information is saved to Airtable.

## Output Details
The workflow stores extracted applicant data and the uploaded resume in Airtable and presents a success message to the applicant upon completion of the application process.

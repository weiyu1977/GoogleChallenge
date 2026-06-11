# Demo Video Script

Target length: 2-3 minutes.

## 0:00 - 0:20 Problem

"People visiting the United States often do not know which visitor medical insurance to buy. The risks are especially confusing for parents, seniors, road trips, hospital visits, car accidents, and pre-existing condition wording."

Show:

- Home page
- Trip/risk profile area

## 0:20 - 0:55 Recommendation Flow

"The advisor collects trip length, age, health signals, medical risk, and preferences, then recommends what to compare before buying."

Show:

- Generate recommendation
- Plan comparison
- provider directory
- buying checklist

## 0:55 - 1:35 Policy Analysis

"After purchase, the user uploads the policy PDF. Gemini reads the PDF, and our reusable document workflow module converts raw model output into a structured PolicyAnalysisReport."

Show:

- Upload policy PDF
- Structured report sections
- claim preparation
- manual review
- deadlines

## 1:35 - 2:05 LLM Workflow Module

"The key technical component is the llm-document-workflow module. It manages prompt, schema, provider adapters, JSON extraction, schema validation, repair, markdown fallback, and diagnostics. This makes the component reusable in other projects."

Show:

- LLM admin page
- Prompt Studio
- Workflow Test Console
- diagnostics

## 2:05 - 2:30 Trust And Operations

"The app includes authentication, privacy consent, audit logs, upload checks, policy history, and a path to deploy on Google Cloud Run. Gemini is connected through a provider adapter, so the project can run with a Gemini API key now and can switch to Vertex AI service identity later."

Show:

- account/login
- policy history
- admin diagnostics

## Closing

"This project helps U.S. visitors and families make safer insurance decisions before travel and understand their policy after purchase."

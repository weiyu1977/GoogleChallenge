# Architecture Diagram

Submission image:

```text
https://github.com/weiyu1977/GoogleChallenge/blob/main/docs/architecture-diagram.svg
```

Submission markdown:

```text
https://github.com/weiyu1977/GoogleChallenge/blob/main/docs/ARCHITECTURE_DIAGRAM.md
```

```mermaid
flowchart TB
  User["Visitor / Family Member"] --> Web["Static Web Client"]
  Web --> API["Node.js Express API"]

  API --> Auth["Auth, Consent, Sessions, Audit"]
  API --> Records["User Records / Policy History / Tasks"]
  API --> Maps["Medical Facility Search<br/>Google Maps iframe + NPI/CMS APIs"]
  API --> Aid["Financial Assistance Content / Templates"]

  API --> Workflow["llm-document-workflow Module"]
  Workflow --> Prompt["Prompt Store<br/>workflow + questions + schema + repair prompt"]
  Workflow --> Provider["Provider Adapter Registry"]
  Provider --> Gemini["Gemini Provider<br/>API key or Vertex AI ADC<br/>PDF Understanding"]
  Workflow --> Normalizer["Output Normalizer<br/>JSON extraction + schema validation + repair + fallback"]
  Normalizer --> Report["PolicyAnalysisReport<br/>structured normalized result"]
  Report --> Web

  API --> SQLite["SQLite Dev DB"]
  API -. production .-> CloudSQL["Cloud SQL MySQL 8"]
  API -. production .-> Storage["Cloud Storage Uploads"]
  API -. production .-> SecretManager["Secret Manager"]

  subgraph "Google Cloud Demo Target"
    CloudRun["Cloud Run"]
    Vertex["Optional Vertex AI Gemini"]
    CloudSQL
    Storage
    SecretManager
  end

  CloudRun --> API
  Gemini --> Vertex
```

## Key Design Points

- The frontend never displays raw model output as the primary user-facing report.
- Gemini handles PDF/scanned PDF understanding through a provider adapter. The default path can use a Gemini API key without requiring a Google Cloud project; Vertex AI ADC is an optional deployment mode.
- `llm-document-workflow` standardizes LLM output into `PolicyAnalysisReport`.
- Diagnostics and raw output are kept for admin/debug views.
- The module is reusable beyond insurance: contracts, bills, receipts, immigration documents, and other PDF workflows.

# Google Cloud Deployment Plan

Recommended quick deployment target: **Cloud Run**.

Why Cloud Run:

- Fastest path for a Node.js Express app.
- Supports build from source with Google Cloud buildpacks.
- Scales to zero for low-cost demo usage.
- Works well with either a project-scoped Gemini API key or Vertex AI from service identity.
- Can later connect to Cloud SQL for MySQL 8.

Official starting point:

- Cloud Run Node.js quickstart: https://cloud.google.com/run/docs/quickstarts/build-and-deploy/deploy-nodejs-service
- Cloud Run source deployment: https://cloud.google.com/run/docs/deploying-source-code
- Cloud SQL MySQL: https://cloud.google.com/sql/docs/mysql
- Cloud Run to Cloud SQL: https://cloud.google.com/sql/docs/mysql/connect-run

## Quick Demo Deployment

Prerequisites:

- Google Cloud project selected.
- Billing enabled.
- Cloud Run API enabled.
- Cloud Build API enabled.
- A Gemini API key stored in the project configuration, or Vertex AI API enabled if using ADC/service identity.

From project root:

```powershell
gcloud config set project YOUR_PROJECT_ID
gcloud services enable run.googleapis.com cloudbuild.googleapis.com
gcloud run deploy visitor-insurance-advisor --source . --region us-central1 --allow-unauthenticated
```

If you choose Vertex AI ADC instead of a Gemini API key, also enable Vertex AI:

```powershell
gcloud services enable aiplatform.googleapis.com
```

After deployment:

```powershell
gcloud run services describe visitor-insurance-advisor --region us-central1 --format="value(status.url)"
```

Use the returned URL as the contest **Testing access** link.

## Required Environment Variables

For a quick public demo:

```text
PORT=8080
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
GEMINI_MODEL=gemini-2.5-flash
PRIVACY_VERSION=2026-06-09.p0
```

Cloud Run automatically injects `PORT`. Set the others in Cloud Run environment variables or the project admin integration settings.

For optional Vertex AI ADC mode, configure:

```text
GOOGLE_CLOUD_PROJECT=YOUR_PROJECT_ID
VERTEX_AI_LOCATION=us-central1
GEMINI_MODEL=gemini-2.5-flash
```

## Service Account Permissions

The Cloud Run runtime service account needs:

- Vertex AI User, only if using Vertex AI ADC mode
- Cloud SQL Client, if Cloud SQL is used
- Secret Manager Secret Accessor, if secrets are moved to Secret Manager

## SQLite Caveat

The current prototype uses SQLite in the app filesystem. On Cloud Run, filesystem writes are ephemeral. This is acceptable only for a short contest demo.

For a stronger demo:

- Use Cloud SQL MySQL 8 for durable accounts and records.
- Move project secrets to Secret Manager.
- Store uploads in Cloud Storage.

## Recommended Contest Demo Setup

Minimum:

```text
Cloud Run + current SQLite prototype + Gemini API key
```

Better:

```text
Cloud Run + Cloud SQL MySQL 8 + Cloud Storage uploads + Secret Manager + Gemini API key or Vertex AI Gemini
```

## Smoke Test After Deploy

1. Open `/api/health`.
2. Create or use demo account.
3. Open Policy Analysis.
4. Upload sample PDF.
5. Confirm structured report appears.
6. Open LLM Admin as admin.
7. Run Workflow Test Console.
8. Confirm diagnostics show parse method and provider metadata.

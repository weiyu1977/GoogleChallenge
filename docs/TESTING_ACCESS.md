# Testing Access

Use this for the Devpost **Testing access: link/demo/test build, with login if private** field.

## Demo URL

```text
https://insurance-advisor-demo-172581874702.us-central1.run.app
```

Health check:

```text
https://insurance-advisor-demo-172581874702.us-central1.run.app/api/health
```

Expected health response:

```json
{
  "ok": true,
  "service": "visitor-insurance-advisor"
}
```

## Demo Accounts

User account:

```text
Email: contest-demo@example.com
Password: ContestDemo!2026
Role: user
```

Admin account:

```text
Email: contest-admin@example.com
Password: ContestDemo!2026
Role: admin
```

## Suggested Judge Test Script

1. Open the demo URL.
2. Log in as `contest-demo@example.com`.
3. Generate an insurance recommendation.
4. Open Policy Analysis and test the upload/text analysis flow.
5. Open Policy History and Personal Center.
6. Log out, then log in as `contest-admin@example.com`.
7. Open LLM Management.
8. Review workflow config, prompt studio, provider configuration, and diagnostics.
9. Open Integration/Admin screens and confirm provider adapter monitoring is visible.

## Demo Notes

- The demo is deployed on Google Cloud Run.
- The app is public, but user-specific functions require login.
- The demo uses SQLite in the Cloud Run instance filesystem with `min-instances=1` for judging stability.
- Data is contest/demo data only and may be reset if the Cloud Run instance is replaced.
- Gemini features are wired through the LLM provider adapter. If no Gemini API key is configured in the project, the app still demonstrates recommendation, policy workflow UI, prompt management, records, maps, and financial assistance flows; real model calls can be configured by an admin in the integrations panel.

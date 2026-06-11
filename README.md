# Google Challenge Submission: InsuranceAdvisor

InsuranceAdvisor helps U.S. visitors and their families decide what visitor medical insurance to compare before travel, then understand the policy after purchase.

## Submission Links

- Code: https://github.com/weiyu1977/InsuranceAdvisor
- Video: https://github.com/weiyu1977/GoogleChallenge/raw/main/videos/insurance-advisor-demo.mp4
- Testing access: https://insurance-advisor-demo-172581874702.us-central1.run.app
- Architecture diagram: [docs/architecture-diagram.svg](docs/architecture-diagram.svg)
- Video script: [docs/VIDEO_SCRIPT.md](docs/VIDEO_SCRIPT.md)
- Devpost-ready fields: [docs/DEVPOST_SUBMISSION.md](docs/DEVPOST_SUBMISSION.md)

## Demo Accounts

User:

```text
Email: contest-demo@example.com
Password: ContestDemo!2026
```

Admin:

```text
Email: contest-admin@example.com
Password: ContestDemo!2026
```

## Notes

- The live demo is deployed on Google Cloud Run.
- The contest demo uses SQLite in the Cloud Run instance filesystem with `min-instances=1`; it is suitable for judging access, not durable production data.
- Gemini is integrated through a provider adapter. The app can use a Gemini API key now and can switch to Vertex AI ADC/service identity later.

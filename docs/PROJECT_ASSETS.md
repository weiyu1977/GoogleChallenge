# Project Assets For Google Contest Submission

Use this file to track the required submission links.

## 1. Code

Repository:

```text
https://github.com/weiyu1977/InsuranceAdvisor
```

Recommended before submission:

- Push latest code.
- Confirm README explains setup.
- Confirm `.gcloudignore` excludes private data.
- Confirm no secrets are committed.

## 2. Video

Suggested format: 2-3 minutes.

Video link:

```text
https://github.com/weiyu1977/GoogleChallenge/raw/main/videos/insurance-advisor-demo.mp4
```

Ready-to-record script:

```text
https://github.com/weiyu1977/GoogleChallenge/blob/main/docs/VIDEO_SCRIPT.md
```

Video outline:

1. Problem: visitors to the U.S. do not know which medical insurance to buy.
2. Recommendation workflow: profile -> risk factors -> plan comparison.
3. Policy analysis: upload PDF -> Gemini reads policy -> structured report.
4. LLM workflow module: prompt/schema/provider/normalizer/reused in other projects.
5. Healthcare map and financial assistance content.
6. Trust: privacy, audit, diagnostics, manual review flags.

## 3. Architecture Diagram

Architecture document:

```text
https://github.com/weiyu1977/GoogleChallenge/blob/main/docs/ARCHITECTURE_DIAGRAM.md
```

Architecture image:

```text
https://github.com/weiyu1977/GoogleChallenge/blob/main/docs/architecture-diagram.svg
```

When submitting, use either:

- Link to the GitHub markdown file.
- Export the Mermaid diagram to PNG and upload it.

## 4. Testing Access

Demo URL:

```text
https://insurance-advisor-demo-172581874702.us-central1.run.app
```

Demo user account:

```text
Email: contest-demo@example.com
Password: ContestDemo!2026
Role: user
```

Admin test access:

```text
Email: contest-admin@example.com
Password: ContestDemo!2026
Role: admin
```

These are contest-only demo accounts. The Cloud Run demo uses SQLite on `/tmp` with `min-instances=1`; it is suitable for judging access, not durable production data.

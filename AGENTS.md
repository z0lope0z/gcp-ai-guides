# Agent guidance: Google Cloud PMLE study guides

Static site of standalone, interactive HTML study guides for the Google Cloud
Professional Machine Learning Engineer certification. Every guide is one
self-contained `.html` file; there's no build step, framework or package manager.

- Follow [FORMAT_PROMPT.md](FORMAT_PROMPT.md) for structure, styling, callout
  classes, data shapes, writing style, content policy and validation.
- The exam guide dated June 1, 2026 defines scope and section weights. If Google
  publishes a newer exam guide, update section names, weights and objective
  numbers in every guide, `index.html` and `README.md` together.
- Use current product names (Gemini Enterprise Agent Platform, Managed Service for
  Apache Airflow, Sensitive Data Protection) and mention old names where learners
  will meet them.
- Before creating a guide, check whether the topic belongs as a section in an
  existing one. New guides go into both `index.html` and `README.md`.
- Never copy exam or practice-test questions verbatim and never label content
  with question numbers. Never commit secrets or identifying details; use
  placeholders such as `PROJECT_ID` and `BUCKET`.

# Agent guidance: Google Cloud AI study guides

Static site (https://gcp-ai.emano.ph) of standalone, interactive HTML study
guides for Google Cloud AI and machine learning certifications, starting with the
Professional Machine Learning Engineer (PMLE) exam. Every guide is one
self-contained `.html` file; there's no build step, framework or package manager.

- Follow [FORMAT_PROMPT.md](FORMAT_PROMPT.md) for structure, styling, callout
  classes, data shapes, writing style, content policy and validation.
- For PMLE, the exam guide dated June 1, 2026 defines scope and section weights. If Google
  publishes a newer exam guide, update section names, weights and objective
  numbers in every guide, `index.html` and `README.md` together.
- Use current product names (Gemini Enterprise Agent Platform, Managed Service for
  Apache Airflow, Sensitive Data Protection) and mention old names where learners
  will meet them.
- Before creating a guide, check whether the topic belongs as a section in an
  existing one. New guides go into both `index.html` (under their certification's
  heading) and `README.md`.
- Never copy exam or practice-test questions verbatim and never label content
  with question numbers. Never commit secrets or identifying details; use
  placeholders such as `PROJECT_ID` and `BUCKET`.

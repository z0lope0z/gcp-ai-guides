# Google Cloud AI study guides

Interactive, self-contained HTML study guides for Google Cloud AI and machine
learning certifications, published at <https://gcp-ai.emano.ph>. Open
`index.html` in a browser; there's no build step.

## Professional Machine Learning Engineer (PMLE)

Twelve topic guides covering the exam guide dated June 1, 2026. Each has a
hands-on lab, scenarios, a searchable reference, flashcards, common gotchas and
a practice quiz; most also have a chooser, sample outputs and a calculator.

Start here:

- [Exam overview and strategy](pmle-exam-overview.html): scope, where study
  time pays off, the 2026 renames and how to read scenario questions.

ML fundamentals (deep dives):

- [ML fundamentals 1: data, features and class imbalance](ml-data-features-imbalance.html)
- [ML fundamentals 2: bias-variance and evaluation metrics](ml-model-evaluation.html)
  (ROC AUC vs PR AUC, thresholds, calibration)

Generative AI on Google Cloud (deep dives):

- [Gemini, Model Garden and Agent Platform](gcp-genai-stack.html)
- [RAG and its failure modes](rag-failure-modes.html)
- [LLM and agent evaluation](llm-evaluation.html)

Exam sections:

- [Section 1: BigQuery ML, AutoML and AI APIs](bigquery-ml-automl-apis.html)
- [Section 2: data, Feature Store, notebooks, experiments](data-notebooks-experiments.html)
- [Section 3: training, tuning and hardware](training-tuning-hardware.html)
- [Section 4: serving and scaling](serving-scaling.html)
- [Section 5: pipelines and MLOps](pipelines-mlops.html)
- [Section 6: security, responsible AI and monitoring](responsible-ai-monitoring.html)

The earlier single-page guide, `pmle-mastery.html`, now redirects to the
matching topic guide.

## Format

Guides follow [FORMAT_PROMPT.md](FORMAT_PROMPT.md), the formatting prompt derived
from the NVIDIA NCP-AII study guides. Use it to add guides here, for example for
other Google Cloud certifications.

## Note on product names

In 2026 Google renamed Vertex AI to Gemini Enterprise Agent Platform and Cloud
Composer to Managed Service for Apache Airflow. The guides use the new names and
map them to the old ones you'll still see in courses and code.

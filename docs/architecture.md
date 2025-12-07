LoPAS-CHD Architecture (Draft)

This document describes the internal processing model
used by LoPAS-CHD Evaluator.

It is implementation-independent,
but shows the recommended architecture design
for external developers.

1. Layer Overview

CHD Evaluator consists of 4 conceptual layers:

Raw Text
   ↓
Ingestion Layer
   ↓
Semantic Layer
   ↓
Indicator Layer
   ↓
Response Layer

2. Ingestion Layer

Responsibilities:

language detection

tokenization

segmentation

safety filter

minimal normalization

Output:

{
  "lang": "ja",
  "tokens": [...],
  "sentences": [...],
}

3. Semantic Layer

Responsibilities:

topic detection

concept extraction

dependency relations

clustering

summary

narrative mode

Output:

{
  "clusters": [...],
  "dependencies": [...],
  "topics": [...]
}

4. Indicator Layer

Each LoPAS indicator receives a semantic bundle
and returns a score (0.00–1.00).

Conceptual pseudocode:

for indicator in Indicators:
    score[indicator] = indicator.evaluate(semantic)


Indicators work independently.

5. Response Layer

Responsible for:

normalization

rounding

JSON schema

minimal metadata

Output example:

{
  "version": "1.0.0",
  "scores": {...},
  "raw": {...}
}

6. Plugin Architecture

CHD MAY accept external plugins:

domain evaluators

specific indicators

enterprise-grade scoring

medical ethics

socio-economic analysis

research modes

locality or culture analysis

7. Edge-First Design

CHD is designed for edge-first deployment:

Cloudflare Workers

wasm

local inference

offline mode

minimal resources

privacy-friendly

low cost

8. Cloud Execution

Recommended:

Cloudflare

Vercel

Fly.io

FastAPI

Serverless

Docker

No vendor lock-in.

9. Privacy by Design

CHD does not require storing raw text:

streaming in

scoring

discard input

output only normalized scores

Optional:

anonymization

no persistent logs

10. Future Expansion

real-time stream scoring

wasm evaluator

edge micro-clusters

sovereign deployments

independent CHD agents

fully local LoPAS nodes

# LoPAS CHD API (Draft Specification) This document describes the minimal interface required for external systems (AI agents, analysis tools, cloud platforms, LLM chains, etc.) to interact with LoPAS-CHD Protocol. --- # 1. Overview LoPAS-CHD exposes a simple evaluation interface: - input: free text (any language) - output: LoPAS indicator scores (normalized 0.00–1.00) - optional: context metadata Goal: Evaluate cognitive quality and structural state of thinking. --- # 2. Endpoint POST /v1/eval **Request JSON**
json
{
  "text": "your text here",
  "options": {
    "language": "auto | ja | en",
    "include_raw": true
  }
}

Response JSON
{
  "DoQ": 0.72,
  "CCI": 0.63,
  "RDI": 0.58,
  "HRI": 0.44,
  "TRS": 0.71,
  "SCI": 0.52,
  "RVI": 0.66,
  "AHI": 0.41
}
3. Extended Response
{
  "scores": { ... },
  "raw": {
    "tokens": 321,
    "topic_clusters": [...],
    "error_flags": [...],
    "meta": {...}
  }
}
4. Health Check
GET /v1/health


Response:

{ "status": "ok" }

5. Authentication

None (as open protocol).
Individual deployments MAY add API keys.

6. Rate Limiting

Not defined in protocol.
Each implementation MAY set own policy.

7. Error Response
{
  "error": "invalid request",
  "hint": "text field required"
}

8. Versioning

Semantic versioning:

v1.0.0

Future Extensions

batch evaluation

streaming evaluation

embedding-based scoring

plug-in systems

local edge nodes

wasm implementation

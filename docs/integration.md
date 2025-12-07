# LoPAS-CHD Integration Guide (v0.1 Draft)

This document describes how external systems can integrate the
LoPAS-CHD Protocol, regardless of platform, language or vendor.

> LoPAS-CHD は「プロダクト」ではなく「接続仕様」です。
> Implementation is free.

---

# 1. Required

Any client must:

- POST text to `/v1/eval`
- accept JSON
- handle normalized scores (0–1)
- optional raw fields

That is all.
Everything else is optional.

---

# 2. Minimal Client (curl)

```bash
curl -X POST \
  https://your-lopas-node.com/v1/eval \
  -H "Content-Type: application/json" \
  -d '{
    "text": "こんにちは",
    "options": { "language": "auto" }
  }'
3. Local Node (recommended)
LoPAS-CHD is designed to run locally, ideally on

edge device

local machine

private cloud

wasm container

Reason:

privacy

safety

cost

sovereignty

4. Integration Patterns
Pattern A: LLM Agent
send generated text

evaluate DoQ, CCI, SCI, TRS

update “thinking mode”

loop until thresholds reached

Pattern B: Retrieval-Augmented LLM
evaluate retrieved passages

remove low-quality segments

re-rank documents by TRS or CCI

Pattern C: Cloud Agent
request → LoPAS → policy decision → action

use SCI/RVI to prevent collapse decisions

5. Example: Cloudflare Worker (pseudo)
ts
コードをコピーする
export default {
 async fetch(req, env) {
   const body = await req.json()
   const scores = await env.LOPAS.fetch("POST", body)
   return new Response(JSON.stringify(scores))
 }
}
6. Example: Local Script (Python)
python
コードをコピーする
import requests

payload = {
  "text": "example",
  "options": {"language": "en"}
}

res = requests.post("http://localhost:8787/v1/eval", json=payload)
print(res.json())
7. Example: LLM Chain (Pseudo)
sql
コードをコピーする
user → LLM → LoPAS → LLM → user
Rules:

LLM must NOT finalize until LoPAS returns “Ok phase”

“hallucination suppression” is optional

CHD encourages controlled divergence

8. Recommended Usage
Iterative loop
lua
コードをコピーする
input → LLM → LoPAS → revise prompt → LLM → output
Real-time monitoring
detect collapse trajectories (SCI↑)

detect meaning-loss (TRS↓)

detect coercion or dogma (CCI↓)

9. Safety Principle
LoPAS is not a censorship engine.
LoPAS is a thinking stabilizer.

no political alignment requirement

no ideology filtering

no persuasion

no morality scoring

It only measures structure and cognitive resilience.

10. License
MIT
Free for any system, any platform.

11. Contributions
Pull requests welcome.
New examples welcome.
Adapters welcome.
Node implementations welcome.

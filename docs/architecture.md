LoPAS-CHD Architecture (Draft v1)

This document describes the minimal system architecture required to implement the LoPAS-CHD Protocol.
It is a reference design, not a required software implementation.

1. Layered Architecture

LoPAS-CHD consists of four conceptual layers:

┌─────────────────────────┐
│ L4: Agent & Application │  ← AI agents / dashboards / eval tools
├─────────────────────────┤
│ L3: Protocol Interface  │  ← /v1/eval  /v1/health
├─────────────────────────┤
│ L2: Cognitive Scoring   │  ← DoQ / CCI / RDI / HRI / TRS / SCI …
├─────────────────────────┤
│ L1: Controlled Hallucination Design
└─────────────────────────┘

2. Data Flow Overview
Text Input
   ↓
Preprocess (language detection / tokenization)
   ↓
Cognitive Scoring (Indicators)
   ↓
CHD Adjustment (hallucination control)
   ↓
Normalization (0.00–1.00)
   ↓
JSON Output

3. Module Components
Text Intake

Language auto-detection

Tokenization

Context attachment (optional)

Indicator Engine

DoQ (Density of Questions)

CCI (Connectivity)

RDI (Reasoning divergence)

HRI (Hypothesis reframing)

TRS (Resonant value)

SCI (collapse probability)

RVI (restoration value)

AHI (altruism harvest)

CDI, NSRI (optional)

CHD Layer

Controlled Hallucination Design

Safety framing

Scaling

Interpretive stability

Anti-drift heuristics

4. Implementation Freedom

LoPAS-CHD does not define:

programming language

hosting method

database choice

local vs cloud

GPU vs no-GPU

Any implementation is valid if:

JSON format matches

indicator normalization follows protocol

5. Local / Edge Support

LoPAS-CHD is designed for local evaluation, including:

Edge devices

WASM

Mobile inference

On-prem LLMs

Cloud is optional.

6. Agent Integration

LoPAS-CHD is compatible with:

OpenAI Assistants

Claude Tools

Gemini Functions

MCP Servers

Agent frameworks

Agents simply call /v1/eval.

7. Minimal Requirements

Accept text input

Output JSON indicators

Expose /v1/health

Normalize 0–1

MUST preserve meaning context

Everything else is implementation detail.

8. Version Note

Architecture v1.0
Protocol v1.0
Indicators v1.0

Pull Requests Welcome

This is a living document.

Contributions:

diagrams

local implementations

wasm versions

multi-modal extensions

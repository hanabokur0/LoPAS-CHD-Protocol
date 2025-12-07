# LoPAS Protocol (Draft)

# LoPAS-CHD Protocol Draft (v0.1)

> This document defines the Creativity–Hallucination Dynamics (CHD) Protocol and its relation to LoPAS cognitive indicators.  
> The protocol describes *how AI thinking loops should be executed*, not what the agent should answer.

---

## 1. Philosophy
Modern AI systems prioritize correctness, efficiency, and safety.  
However, human creativity historically emerges from ambiguity, contradiction, and
failure (hallucinations).

CHD stands for:

- **Creativity**
- **Hallucination**
- **Dynamics**

CHD does not attempt to eliminate hallucination.
Instead, it **uses hallucination as a generative energy source** and regulates its degree using measurable indicators.

CHD is compatible with any LLM or agent.

---

## 2. Purpose of the Protocol

CHD provides:

- a thinking loop
- a governance rule above individual prompts
- a metric-based creativity control system
- agent-independent execution
- language-agnostic architecture

The goal is not automation.
The goal is **autonomous co-thinking** between human and AI.

---

## 3. Core Principle

CHD consists of cycles regulated by LoPAS indicators:

- EFI (Entropy Fertility Index)
- QSI (Question Silence Index)
- CFI (Constructive Friction Index)
- MCI (Mental Context Index)
- TOP (Trajectory of Thought)

Each parameter modulates a given cycle.

---

## 4. Minimal Loop Design

The protocol defines a loop:

Human → Question → AI → (LoPAS evaluation) → Regulated Response → New Question


CHD’s objective:
- never terminate thinking
- avoid “answer and end”
- preserve ambiguity
- expand context
- re-enter loop

This is the opposite of task completion.

---

## 5. LoPAS Integration

CHD requires AI to read or maintain:

- DoQ
- CCI
- EFI
- QSI
- CFI

The loop adjusts based on indicator movement.

Example:

- EFI ↑ → more chaos / hallucination allowed
- QSI ↑ → long silence / reflection
- CFI ↑ → adversarial role increases

---

## 6. Personality Models

CHD supports multiple personality presets:

- Commander (Golden-ratio balance)
- Oracle (High ambiguity + metaphysics)
- Anti-hero (High CFI, argumentative)
- Writer (High EFI for hallucination)

Additional presets may be proposed by community.

---

## 7. Safety Layer

Because CHD modulates hallucination intentionally,
the protocol requires:

- no identity claims
- no medical advice
- no political persuasion
- no harmful instructions

The hallucination is used as *imagination*, not fact.

---

## 8. Implementation Status

This repository is documentation only.

> This is **not** a ready-made agent.

External implementation examples will be linked in future versions.

---

## Status

- Draft: v0.1  
- Author: hanabokur0  
- License: MIT

LoPAS-CHD Protocol — Scoring Specification
1. Score Range

すべての指標は以下の範囲に正規化される。

0.00 ≤ score ≤ 1.00

2. Score Levels
Range	Label	Interpretation
0.00–0.29	Collapse	Structural collapse / cognitive breakdown
0.30–0.59	Transitional	Recoverable / dialog possible
0.60–0.79	Intelligent	Structured / cooperative / synthesis begins
0.80–1.00	Resonant	Civilization-design / collective re-framing
3. Alignment Interpretation
Collapse

zero connectivity

emotional dominance

tribal response

violent escalation risk

Transitional

hypothesis appears

partial branching

minimal reflection

Intelligent

branching inquiry

reframing capacity

multi-perspective synthesis

Resonant

structural self-repair

civilization-level design

long-term recovery path

4. General Formula (normalized)
score = clamp((raw - min) / (max - min), 0, 1)


※実装自由。ただし正規化結果の範囲は固定。

5. Aggregated Score

CHDは個別指標の集合体であり、
総合スコア＝任意である（実装側に委譲）。

例（推奨・任意）：

CHD = mean([DoQ, CCI, RDI, HRI, TRS, SCI, RVI, AHI])

6. Implementation Independence

CHDは「算出方法」を規定しない。

embedding

statistical model

rule-based

LLM

hybrid

symbolic

edge-only

どれでもOK。結果フォーマットだけがCHD。

7. Required Output Fields

返すJSONには必ず以下を含むこと：

{
  "version": "≥1.0",
  "scores": {
    "DoQ": 0.00-1.00,
    "CCI": ...,
    "RDI": ...,
    "HRI": ...,
    "TRS": ...,
    "SCI": ...,
    "RVI": ...,
    "AHI": ...
  }
}

8. Optional Metadata
{
  "lang": "ja|en|auto",
  "timestamp": "",
  "input_tokens": 1234,
  "model": "optional"
}

9. Time-series

CHDは単発ではなく系列で解釈することを推奨する。

t0 → t1 → t2


特に

RDI

HRI

TRS

SCI

は時間軸で本領を発揮する。

10. Independence from sentiment analysis

CHDは

positive / negative

happy / sad

right / wrong

を評価せず、
構造・価値・共鳴のみ測定する。

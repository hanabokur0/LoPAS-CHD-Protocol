LoPAS-CHD — WASM / Edge Target (Draft)

LoPAS-CHD Protocol is designed to be compiled to
WebAssembly (WASM) and executed on edge runtimes.

1. Design Goal

zero-install

low latency

low memory footprint

cross-platform

browser-compatible

serverless ready

offline-capable

2. Recommended Runtimes

Suggested targets:

Cloudflare Workers (WASM-native)

Deno Deploy

Fastly Compute

Vercel Edge

Wasmer

Wasmtime

Browser WebAssembly

No vendor lock-in required.

3. Minimal Requirements

no persistent storage required

no heavyweight model loading

core logic < 200 KB compiled

no GPU dependency

uses text-only inference

language auto-detection included

4. Why WASM

Because LoPAS-CHD is intended to run as a local thinking companion
and not only as a remote SaaS.

Expected benefits:

local privacy

local cost reduction

local sovereignty

latency < 20ms

deployable anywhere

5. Browser Mode

CHD MAY be embedded inside:

Chrome extensions

Edge extensions

Firefox extensions

local file analyzers

chat UI wrappers

knowledge assistants

6. Future

Planned optional builds:

WASM SIMD optimization

on-device ML tiny models

streaming tokenizer

“LoPAS Local Agent Mode”

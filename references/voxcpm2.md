# VoxCPM2 — Olympus Reference Evaluation

## Upstream

- Repository: https://github.com/OpenBMB/VoxCPM
- Model: https://huggingface.co/openbmb/VoxCPM2
- Documentation: https://voxcpm.readthedocs.io/
- License: Apache-2.0

## What it is

VoxCPM2 is an open-source tokenizer-free text-to-speech system from OpenBMB. It uses continuous speech representations rather than discrete speech-token conversion and is designed for natural multilingual synthesis, voice design, controllable voice cloning, and high-fidelity continuation-style cloning.

## Why Olympus saved it

Olympus needs a durable local voice service that does not depend on a specific cloud account or per-character commercial TTS provider. VoxCPM2 is a strong candidate because it can run locally, supports commercial use under Apache-2.0, supports short-reference voice cloning, and can preserve timbre while allowing style, pace, and emotion control.

This is especially relevant to:

- Hestia / Olympus voice output
- Patrol Playback narration
- Daily Operations / Foreman's Toolbox narration
- PM Videos and other automated video pipelines
- batch narration where cloud TTS costs or account limits become a bottleneck

## Current upstream capabilities worth evaluating

- 2B-parameter VoxCPM2 model
- 30 supported languages
- 48 kHz output
- tokenizer-free diffusion autoregressive architecture
- voice design from natural-language descriptions
- controllable voice cloning from a short reference clip
- "ultimate cloning" using reference audio plus its transcript
- context-aware prosody
- streaming inference
- CLI, Python API, and local web demo
- production serving paths through Nano-vLLM-VoxCPM and vLLM-Omni
- OpenAI-compatible speech-serving option through vLLM-Omni

## Olympus integration concept

Preferred architecture if testing succeeds:

`Olympus / Hestia / video agents -> Olympus Voice Service -> VoxCPM2 -> WAV/streamed audio`

The voice service should expose a stable internal interface such as:

- text
- voice/profile name
- reference audio
- optional reference transcript
- style/emotion instructions
- speed/cadence controls
- output format

The underlying TTS engine should remain replaceable so Olympus can compare VoxCPM2 with ElevenLabs or other engines without changing every consumer.

## First bench test

Use Alan's existing clean voice reference and render the same short script through:

1. existing ElevenLabs clone
2. VoxCPM2 controllable cloning
3. VoxCPM2 ultimate cloning if the reference transcript is available

Compare:

- voice similarity
- cadence
- breathing / pauses
- emotional naturalness
- pronunciation
- artifacts
- generation speed
- VRAM/RAM use
- setup complexity
- repeatability
- cost per minute

The Bodhi "Stinky Sock" script is a useful A/B test because an ElevenLabs render already exists and the script contains rapid changes in tone, pauses, emphasis, and comic delivery.

## Security and operating constraints

- Reference only until tested in an isolated Olympus sandbox.
- Do not expose the local service directly to the public internet.
- Keep it behind the approved Olympus secure gateway/front door if later deployed as a service.
- Do not commit private voice samples, API keys, credentials, or model-provider secrets to GitHub.
- Store voice references in approved private storage, not in this public reference repository.
- Do not allow agents to clone third-party voices without appropriate authorization.

## Cost implications

- No VoxCPM2 usage fee of its own; code and weights are Apache-2.0.
- Local cost is compute/electricity/storage.
- Could reduce or eliminate recurring commercial TTS usage for supported workloads if quality is sufficient.

## Components worth studying/reusing

- tokenizer-free TTS architecture
- controllable cloning workflow
- prompt-audio + prompt-text continuation workflow
- batch generation CLI
- streaming interface
- Nano-vLLM serving path
- vLLM-Omni OpenAI-compatible speech API

## Components / risks to evaluate before adoption

- real VRAM requirements on Olympus hardware
- long-form stability
- English pronunciation edge cases
- latency under concurrent agent workloads
- model download/storage size
- GPU scheduling contention with video generation and other local models
- safety controls around voice cloning

## Status

**Prototype candidate — high priority.**

Do not integrate into live Olympus until an isolated A/B test against the current voice workflow is complete and the service boundaries are defined.

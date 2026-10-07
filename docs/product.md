# RelayCart AI: product scope

## Status

Design baseline approved. Implementation has not started; no functioning features, pipelines, releases or deployments are claimed.

## Purpose

An independently deployed inference service producing bounded, evidence-grounded incident explanations.

## Planned stack

TypeScript, Hono and Cloudflare Workers AI

## Engineering contract

- This repository owns its source, checks, documentation and releases.
- Public interfaces are versioned and tested.
- The development harness is optional tooling, not a runtime dependency.
- Examples and demonstration data are synthetic.
- Architecture decisions and exact local commands will be documented
  as their implementation checkpoints pass.

## Approved design baseline

- TypeScript/Hono owns bounded read-only inference, provider adapters, prompt versions and validated explanation output.
- RAG uses authorized evidence retrieved by the API; initial structured retrieval does not require embeddings or a vector database.
- The AI service has no database credentials or business-write tools; service identity and evidence references are verified.
- Cloud Workers/Workers AI and self-hosted Node OCI entry points are separately tested; fake inference is the normal CI path and local Ollama is optional.
- Budgeted real-model evaluations cover grounding, insufficient evidence and prompt injection; fake results are not labelled live model validation.

## Required engineering evidence

Each component has applicable automated checks: unit, integration, functional/contract and security tests; dependency/container/IaC scanning and secret detection where relevant. Main builds, deployments, scheduled regressions and availability observations are distinct. Build/candidate numbers increment automatically; stable semantic versions are calculated from reviewed changes and promoted through the release-readiness gate. Retain immutable artifacts, sanitized evidence and compatible rollback instructions. These are requirements, not implementation claims.

Use the portable harness during development once its core is usable; record any bypasses and feedback. The application does not import the harness at runtime.

## Design references

- [Harness release scope](https://github.com/aenns/portable-ai-harness/blob/96cc799/docs/release-scope.md)
- [Harness architecture](https://github.com/aenns/portable-ai-harness/blob/40476cf/docs/architecture.md)
- [Harness configuration and commands](https://github.com/aenns/portable-ai-harness/blob/99d47a1/docs/configuration-and-commands.md)
- [RelayCart system architecture, revision 4](https://github.com/aenns/relaycart-docs/blob/f5cf12d/docs/architecture/system.md)

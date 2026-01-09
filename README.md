# code-provenance

An open-source project that adds verifiable provenance into the developer workflow. 

It enables IDEs, CI systems and reviewers to understand how code was produced, including whether it was AI assisted, without modifying source code or enforcing policy. 

## V1.0

This repository contains the VS Code extension (provenance.ai) that generates signed provenance sidecars for source files on save.

## Why code provenance?

AI-assisted development is becoming routine, but once code is committed, the context of *how* it was produced is lost. Reviewers, security teams, and organisations are left to guess whether code was human-written, AI-assisted, or a mix of both. Most existing approaches try to **detect** AI-generated code or **enforce** policy, which is brittle, adversarial, and poorly aligned with real developer workflows.

provenance.ai takes a different approach by introducing **verifiable, cryptographically signed provenance** at the moment code is written. It attaches AI-related context as a sidecar, not inline metadata, keeping source code clean and policy-agnostic. This enables developers, reviewers, and platform teams to understand *how* code was produced—without surveillance, enforcement, or workflow disruption—creating a neutral foundation for trust, auditability, and future governance.

**Overview**

1. On file save, the extension computes a canonical and an advisory semantic hash
2. Builds a C2PA-compatible provenance manifest describing the edit context
3. Sends hashes + metadata to a signer API, which signs using Ed25519 keys in an HSM/KMS
4. Writes a signed <file>.c2pa.json sidecar provenance file alongside the source file
5. Enables CI/PR verification of provenance and signatures

## Contributors
Ideated by Sumitha Rachel Kurien. Implementation and ongoing development are collaborative.
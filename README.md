# Eidolon

<div align="center">

**Post-quantum cryptographic vault with a holographic key**

*Sovereign local identity · passwordless authentication · no server, no account, no recovery email*

[![License: CC BY-ND 4.0](https://img.shields.io/badge/license-CC%20BY--ND%204.0-lightgrey.svg)](./LICENSE)
[![Status](https://img.shields.io/badge/status-pre--audit-orange.svg)](#status)
[![Post-Quantum](https://img.shields.io/badge/crypto-post--quantum-blueviolet.svg)](#cryptographic-guarantees)
[![No Telemetry](https://img.shields.io/badge/telemetry-none-success.svg)](#design-values)
[![No Token Sale](https://img.shields.io/badge/token--sale-none-success.svg)](#design-values)

🇫🇷 *[Version française disponible](./READMEfr.md)*

</div>

---

## What is Eidolon?

Eidolon is a local cryptographic vault built around a simple idea:

> **Possession of a key should be enough to prove an identity** — without a central server, without a password, without an account to recover.

The key is not a single file. It is a **holographic object** composed of two complementary fragments that, combined, produce a verifiable identity with high entropy and resistance to quantum attacks.

Around this key, Eidolon provides:

- **authentication without shared secret** — prove who you are without revealing your key
- **a unique identity per device**, non-transferable without explicit intent
- **a cryptographic visual signature** (avatar) derived directly from the key's mathematical structure
- **a runtime economy** that reflects the vault's activity and vitality
- **an optional blockchain layer** for HD wallets, document anchoring, and NFT avatars — all rooted in the same key

---

## The problem we are solving

Today's identity infrastructure leaks at every seam:

- **Passwords** are forgotten, reused, phished, or leaked. The average user juggles dozens of them and can't remember any.
- **Password managers** concentrate your entire digital life behind one master password — a single point of failure.
- **Identity providers** ("Sign in with...") can revoke your access at any time and observe your entire activity.
- **Seed phrases** turn your identity into 12 words written on paper — irretrievable if lost, dangerous if found.
- **Hardware tokens** require trust in a vendor, physical access to a specific object, and cannot be copied or backed up.
- **Quantum computers**, when practical, will retroactively break most of today's deployed cryptography.

Eidolon proposes an orthogonal model: **your identity is a mathematical object you physically possess**, split across two cryptographic fragments, quantum-resistant, locally verifiable, and never shared with anyone — not even to authenticate.

---

## The holographic metaphor

A physical hologram encodes a 3D scene across the entire photographic plate. Cut the plate in half and each half still contains the full scene — but with less resolution and requiring the correct illumination to reveal.

Eidolon's key follows the same principle, mathematically:

- **information is distributed**, not concentrated in one place
- **two complementary fragments** are required to reconstruct the full identity
- **a specific "illumination"** (the cryptographic protocol) is required to reveal the content
- **the visual avatar** is not a picture of the key — it *is* the key, rendered in three dimensions

This distribution is what makes the key resilient against partial compromise, robust against observation, and mathematically rich enough to serve as the root of a trust system.

---

## Founding principles

| Principle | Consequence |
|-----------|-------------|
| **Local-first** | No server holds your key or your identity |
| **Zero-knowledge** | Prove what you know without revealing it |
| **Post-quantum** | Resistant to known quantum algorithms |
| **Dual-fragment** | Two distinct files are required to unlock a vault |
| **Machine-bound** | An identity is tied to a device, by design |
| **File-based state** | No database — every byte of state is inspectable |
| **Offline by default** | Core operations require no network access |
| **No telemetry** | Eidolon does not phone home, ever |

---

## How Eidolon differs

Eidolon is not a competitor to existing tools — it occupies a different corner of the design space.

| Existing tool | What it does well | What Eidolon does differently |
|---------------|-------------------|-------------------------------|
| **Password managers** | Store secrets you already have | You have no passwords to store — your key *is* your identity |
| **FIDO2 / Passkeys** | Strong auth tied to a service | Sovereign identity independent of any service |
| **Seed phrases** | Portable backup for crypto wallets | Two cryptographic files, not 12 memorizable words |
| **Hardware tokens** | Physical possession = auth | Any device can be your vault — no vendor dependency |
| **SSO / OAuth** | Convenient cross-service login | No provider can revoke you or observe you |

Eidolon is **complementary** to most of these. It does not try to replace them — it aims to become the root layer *beneath* applications that today rely on passwords, email recovery, or centralized providers.

---

## Cryptographic guarantees

Without disclosing the internal implementation, the vault guarantees the following properties:

| Property | Guarantee |
|----------|-----------|
| **Quantum resistance** | Cryptographic output is based on post-quantum primitives |
| **Side-channel resistance** | Sensitive operations run in constant time |
| **File integrity** | Every persisted artifact is cryptographically authenticated |
| **Metadata protection** | Non-sensitive metadata is masked at rest |
| **Non-forgeability** | Cryptographic signatures prevent identity spoofing |
| **Optional recovery** | K-of-N secret sharing can be enabled at creation time |
| **Deterministic generation** | Same inputs always produce the same key, verifiably |

The internal pipeline, parameter choices, algorithm families, entropy sources, and quality tests are **not disclosed at this stage** and will be progressively published after formal external audit (see [roadmap](#roadmap)).

---

## Architecture at a glance

Eidolon is organized into four complementary subsystems:

1. **Cryptographic pipeline** — holographic key generation and core primitives
2. **Vault identity and persistence** — registration, device binding, local encrypted state
3. **Holographic resources** — cryptographic avatar, runtime economy, visual signature
4. **Blockchain integration** — HD wallets across multiple chains, avatar inscriptions

See [`ARCHITECTURE.md`](./ARCHITECTURE.md) for the conceptual description of each subsystem, plus the animated gallery of the holographic viewer.

---

## Use cases

Eidolon is designed as a **root identity layer**. It does not ship a single application — it enables a class of applications that would be awkward or impossible with today's identity infrastructure.

**End-user scenarios:**
- Log in to a service without ever creating an account or password
- Sign a document in a way that is verifiable offline, forever, even against a quantum adversary
- Prove you are the same person across services — without linking the services to each other
- Manage cryptocurrency wallets with a single root of trust shared with the rest of your identity
- Exchange end-to-end encrypted messages with a contact whose vault you have verified once

**Developer / integrator scenarios:**
- Replace the "email + password + recovery" flow with a vault-based passwordless login
- Issue cryptographically anchored credentials that the user controls, not you
- Add a post-quantum authentication layer to an existing service without rewriting its auth logic
- Build a decentralized application where users own their identity without needing a blockchain

The **first real client** of this model is **Cipher**, an end-to-end encrypted messenger developed in parallel, which uses Eidolon for passwordless authentication.

---

## Frequently asked questions

**What happens if I lose one of the two fragments?**
Without a recovery share set up in advance, loss is permanent. This is a deliberate design choice: sovereignty implies full responsibility. Optional K-of-N secret sharing is available at creation time for users who want a fallback.

**Can I move my identity to a new computer?**
Yes, via an explicit *revocation-and-rebirth* flow. There is no silent transfer — moving a vault is an intentional cryptographic act, verifiable from both machines.

**Does Eidolon need internet to work?**
No. Key generation, authentication, signing, and vault operations are fully offline. Network is only used when you explicitly ask for it (e.g., interacting with a blockchain or a third-party service).

**Is my data sent anywhere?**
No. Eidolon does not phone home, does not collect telemetry, and does not perform "background sync" or "cloud backup" without your explicit action. Your vault lives on your device, full stop.

**Why isn't the code open source yet?**
Publishing cryptographic code before external audit is irresponsible. An attacker can study your weaknesses faster than a volunteer community can find and report them. Our roadmap commits to full audit in Phase 4, followed by progressive code disclosure.

**Is there a token sale, ICO, or airdrop?**
No. Eidolon has no fundraising token, no ICO, and no airdrop campaign. The internal PSNX allocation system is an *in-system* mechanism for founding vaults — it is not a financial instrument offered to the public.

**When will it be production-ready?**
When Phase 1 is stabilized and the Phase 2 SDK is available. No fixed date is communicated — quality and correctness take precedence over schedule.

**How is it different from a blockchain wallet?**
A blockchain wallet holds keys for a specific chain. Eidolon holds an *identity* that can optionally drive wallets on any chain — and also serves for authentication, signing, messaging, and more. The blockchain is a downstream use case, not the primary purpose.

**Who is behind Eidolon?**
Eidolon is currently developed solo, pre-community phase. The project deliberately avoids rushing into community/governance structures until the cryptographic core is audited and stable.

---

## Design values

| Value | In practice |
|-------|-------------|
| **Audit before open-source** | Working system and docs come first; code opens only after formal audit |
| **No premature tokenization** | No ICO, no airdrop, no speculative vehicle attached to the project |
| **Longevity over velocity** | Designed to still work in 30 years, not to win a hackathon |
| **Your data stays yours** | No silent backups, no "convenience" uploads, no third-party analytics |
| **Truthful badges** | The README reports the project's real state, including what it is *not* yet |
| **Sovereignty implies responsibility** | Recovery is opt-in, not automatic |

---

## Status

**Eidolon is under active development, pre-external security audit.** This repository is a **public showcase** — documentation and visual material only. Source code, exact parameters, and implementation details are not published at this stage.

### Roadmap

| Phase | Goal | Status |
|-------|------|--------|
| **Phase 1** | Product stabilization — identity, authentication, runtime economy | In progress |
| **Phase 2** | "Eidolon Connect" SDK — reusable auth layer for third-party apps | Specification |
| **Phase 3** | Multi-platform distribution — desktop, mobile, browser extension | Design |
| **Phase 4** | Open protocol — formal spec, external audit, standardization submission | Planned |

---

## About this repository

**What is in this repository:**
- The project vision and conceptual architecture (`README.md`, `ARCHITECTURE.md`)
- An animated gallery of the holographic avatar's visual layers (`assets/*.webm`)
- The license governing use of this documentation (`LICENSE`)

**What is NOT in this repository:**
- The source code of the cryptographic pipeline
- Exact algorithm families, parameters, or test vectors
- File format specifications
- The list of primitives used, their order of application, or their tuning
- The material catalog, polyhedron choices, or economy constants
- Any test suite or internal documentation

These items will be **progressively disclosed after Phase 4 audit**, together with the formal protocol specification.

---

## Contact

For any serious inquiry — partnership, audit, integration, research collaboration — **open a public issue** describing the context. Source code access requests will be evaluated on a case-by-case basis.

This repository does not accept pull requests at this stage, as there is no source to modify.

---

## License

This repository — documentation, descriptions, and visual material — is published under [**CC BY-ND 4.0**](./LICENSE) (attribution required, no derivatives).

The Eidolon system itself — source code, algorithms, specifications, implementations — remains **proprietary, all rights reserved**. No license to the code is granted by the publication of this showcase.

---

<div align="center">

*Eidolon — your identity, your key, your sovereignty.*

</div>

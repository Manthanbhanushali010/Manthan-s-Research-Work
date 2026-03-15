# Manthan Bhanushali — Research Papers & Technical Projects

> AI Systems Engineer | Blockchain Researcher | Full-Stack Developer  
> London, United Kingdom | manthanbhanushali7@gmail.com

This repository contains eight peer-quality research papers and technical 
reports produced across eight distinct technical domains between 2024 and 2026. 
Each paper is accompanied by a working prototype. All research was conducted 
independently or as part of competitive hackathons and academic submissions.

**DOI:** [10.5281/zenodo.XXXXXXX](https://zenodo.org) ← replace with your real DOI after Zenodo generates it

---

## What Is This Repository?

Most researchers publish papers in journals. I build things first, then write 
about what I built. Every paper in this repository has a working prototype 
behind it — real code, real deployments, real results. The papers document 
the architecture, the design decisions, the threat models, and the honest 
limitations of each system.

The eight projects span: confidential computing, blockchain oracle verification, 
agricultural AI, environmental carbon markets, defense technology, autonomous 
welfare agents, auction intelligence, and accessibility AI. Different domains, 
same underlying discipline: build systems that are secure, explainable, and 
honest about what they can and cannot do.

---

## Papers at a Glance

| # | Paper | Domain | Venue | Year |
|---|-------|--------|-------|------|
| 1 | [AgroAI: Decentralised Agricultural Intelligence Platform](#1-agroai) | Blockchain + AI | IEEE-Style Research Paper | 2024 |
| 2 | [PaperClip: Decentralised Confidential Compute Marketplace](#2-paperclip) | Confidential Computing | arXiv Preprint | 2026 |
| 3 | [Watt Witness: Trustless Energy Verification](#3-watt-witness) | Blockchain + IoT | Chainlink Chromion Hackathon | 2026 |
| 4 | [EcoClaw Nexus: Multi-Agent Environmental Verification](#4-ecoclaw-nexus) | Carbon Markets + AI | UK AI Agent Hackathon, Imperial College London | 2026 |
| 5 | [EDTH-LORA: LoRa Positioning for Drone Swarms](#5-edth-lora) | Defense Technology | European Defense Tech Hackathon | 2026 |
| 6 | [FoodGuard UK: Autonomous Food Inflation Early-Warning Agent](#6-foodguard-uk) | Autonomous Agents + Blockchain | Encode x Neo Hackathon | 2025 |
| 7 | [BidSmart: AI-Powered Auction Intelligence Platform](#7-bidsmart) | Multi-Agent AI | EpiMinds UK Hackathon (Anthropic + Lovable) | 2026 |
| 8 | [SignBridge: Multi-Agent Sign Language Mediation](#8-signbridge) | Accessibility AI | Epiminds Stockholm Technical Report | 2026 |

---

## Paper Summaries

### 1. AgroAI
**Full Title:** AgroAI: A Decentralised Agricultural Intelligence Platform Integrating 
AI-Assisted Crop Disease Detection, Blockchain Verification, and Tokenized Incentive Mechanisms

**What it is:** A blockchain platform for smallholder farmers that combines 
AI-powered crop disease detection with smart contract reward mechanisms. A 
farmer uploads a photo of a diseased crop, receives a diagnosis, and is 
automatically rewarded with AGRO tokens verified on-chain.

**Why it matters:** Over 70% of food in sub-Saharan Africa and South Asia is 
produced by smallholder farmers who have no access to expert diagnostics. A 
delayed disease diagnosis can destroy 10–80% of a season's yield.

**Key technical contributions:**
- All five Chainlink services integrated (Functions, VRF, Automation, Data Feeds, CCIP)
- Two production Solidity smart contracts with ERC-20 token economics
- Five oracle verification scripts: multi-source photo verification, market 
  intelligence, community alerting, insurance verification, treatment tracking
- TensorFlow CNN with 95% accuracy across 39+ disease classes

**Stack:** Solidity, Python (Flask), TensorFlow, Chainlink, IPFS, React.js, MetaMask  
**Repository:** [github.com/Manthanbhanushali010/agroai](https://github.com/Manthanbhanushali010/agroai)

---

### 2. PaperClip
**Full Title:** PaperClip: A Decentralised Confidential Compute Marketplace for 
Privacy-Preserving Artificial Intelligence Workloads

**What it is:** A marketplace where anyone can run AI workloads on someone 
else's hardware — without the hardware owner ever seeing the data. Think of it 
as Airbnb for GPU compute, except the host is cryptographically prevented from 
seeing what's running on their machine.

**Why it matters:** Hospitals, banks, and biotech firms need powerful compute 
but cannot hand their sensitive data to cloud providers who also serve 
competitors. This solves that problem using hardware-enforced privacy.

**Key technical contributions:**
- Formal cryptographic model: ECIES with attestation-bound key establishment 
  (ECDH-ES + AES-256-GCM)
- Security proof under four adversary classes: malicious infrastructure 
  provider, network attacker, compromised API gateway, hardware-level attacker
- Full Intel SGX enclave runtime in C with hardware key generation and workload encryption
- AMD SEV-SNP VM-granularity confidential computing architecture
- NVIDIA H100 GPU confidential computing integration
- Multi-criteria distributed job scheduler (price, latency, reputation, TEE type)
- Complete economic marketplace model with staking, slashing, and Sybil resistance

**Stack:** React.js, Node.js/Express, PostgreSQL, Redis, Intel SGX (C), AMD SEV-SNP  
**Paper:** arXiv Preprint — available in this repository

---

### 3. Watt Witness
**Full Title:** Watt Witness: Trustless Energy Verification Using Hardware Security 
Modules, Edge Computing, Decentralised Oracle Execution, and EVM Smart Contracts

**What it is:** A system that proves — cryptographically — how much renewable 
energy a solar installation actually produced. The measurement is signed at the 
device level by a hardware security chip, batched through a Chainlink oracle, 
and recorded permanently on a blockchain.

**Why it matters:** Renewable energy certificates and carbon credits are only 
as trustworthy as the measurements behind them. Currently those measurements 
are just numbers in a spreadsheet someone typed. This system makes them 
cryptographically verifiable.

**Key technical contributions:**
- ATECC608A hardware security module (HSM) for device-level ECDSA signing
- 256-byte compressed Merkle commitment batch protocol (48 + 3n bytes per n readings)
  — fits 69 readings per oracle callback, reducing gas costs by ~37%
- Per-installation Solidity smart contract deployment via factory pattern
- On-chain batch decompression and PowerReading event emission
- Formal threat model: device-layer, backend, oracle, and hardware adversaries
- Complete listener service reconciling on-chain events back to database

**Stack:** ESP32 firmware (C++), Raspberry Pi (Python/FastAPI), Solidity/Foundry, 
Chainlink Functions, Avalanche Fuji, React/TypeScript, Rust  
**Deployed on:** Avalanche Fuji Testnet

---

### 4. EcoClaw Nexus
**Full Title:** EcoClaw Nexus: A Multi-Agent AI Architecture for Automated 
Environmental Verification in Carbon Markets and Climate Finance Infrastructure

**What it is:** A multi-agent AI system that automates the verification of 
carbon credits — a process that currently takes 12–18 months and costs up to 
50% of a project's total budget. EcoClaw does it in under 2 seconds.

**Why it matters:** The voluntary carbon market lost 29% of its transaction 
value in 2024 because buyers don't trust the verification process. One-third 
of existing carbon credits failed independent benchmark assessments in the same year.

**Key technical contributions:**
- Three specialised agents: Satellite Agent (Sentinel-2 NDVI analysis), 
  Weather Risk Agent (drought scoring), Validator Agent (cross-signal consistency)
- Structured Environmental Evidence Bundle (EEB) — typed, schema-validated, 
  machine-readable verification artifact
- Empirically validated on real Greater London Sentinel-2 data: NDVI delta 
  −0.036, drought risk score 7.15 (LOW tier, HIGH confidence)
- Proposed API-first "Stripe for carbon verification" commercial architecture

**Stack:** Python (FastAPI, Pydantic), Sentinel-2 satellite data, multi-agent orchestration  
**Venue:** UK AI Agent Hackathon, Imperial College London, 2026

---

### 5. EDTH-LORA
**Full Title:** EDTH-LORA: Inter-Node LoRa Positioning System for Drone Swarms

**What it is:** A GPS-independent positioning system for drone swarms using 
cheap commodity radio hardware (£30 LoRa modules). When GPS is jammed in a 
conflict zone, drones using this system can still maintain formation using 
radio signals and onboard sensors.

**Why it matters:** In modern conflict zones (most visibly Ukraine), GPS 
jamming and spoofing is routine. A drone swarm that loses GPS loses all 
positional awareness. This system eliminates that single point of failure 
using hardware that costs tens of dollars per node.

**Key technical contributions:**
- Seven-layer system architecture: LoRa comms → RSSI-to-distance → 
  trilateration → IMU dead-reckoning → Extended Kalman Filter → TDMA protocol → dashboard
- Full EKF implementation: state vector [pos_x, pos_y, vel_x, vel_y], 
  process noise Q, measurement noise R, per-packet sequential update
- RMSE 1.8m (EKF-fused) vs 3.2m (RSSI-only) — validated in simulation
- TDMA collision-avoidance protocol (100ms cycles, 10ms guard time)
- Hardware integration: Ebyte E22-900T22S (SX1262), ArduPilot H7 flight controller
- Rust WebSocket server + Next.js 3D live dashboard

**Stack:** Python (NumPy/SciPy), Rust, Next.js, PlatformIO/Arduino (ESP32), 
ArduPilot, Raspberry Pi  
**Venue:** European Defense Tech Hackathon, London, February 2026

---

### 6. FoodGuard UK
**Full Title:** FoodGuard UK: An Autonomous Early-Warning Agent for Food Inflation 
Using SpoonOS Orchestration and Neo Blockchain Execution

**What it is:** An autonomous AI agent that monitors food supply signals, 
computes a risk score, decides on a policy response, and — if the situation 
is critical — automatically issues welfare vouchers on a blockchain. All of 
this happens without human intervention, but every decision is fully auditable.

**Why it matters:** Government responses to food inflation are typically 
4–6 weeks behind the first warning signals. By the time policy is enacted, 
households have already reduced food purchasing. This system compresses that 
response from weeks to minutes.

**Key technical contributions:**
- Complete autonomous pipeline: signal ingestion → FoodRiskTool weighted 
  heuristic → SpoonOS ToolCallAgent LLM → conditional Neo N3 voucher execution
- Neo N3 VoucherContract.cs with IssueVoucher() and RedeemVoucher() 
  methods and immutable on-chain audit trail
- Deterministic risk scoring with four signal weights and four policy tiers
- Architecture extends to eight welfare domains: MindGuard (mental health), 
  RentGuard (housing), WattGuard (energy poverty), NutriGuard (child nutrition), 
  FloodGuard, CareGuard, AquaGuard

**Stack:** Python (SpoonOS, FastAPI), React/TypeScript, Neo N3 (C#), Vite, 
Tailwind CSS, Framer Motion  
**Venue:** Encode x Neo Hackathon 2025 — SpoonOS Main Track & Neo Sponsor Track

---

### 7. BidSmart
**Full Title:** BidSmart: AI-Powered Auction Intelligence Platform

**What it is:** A multi-agent AI system that tells you exactly what to bid 
at auction, when to bid, and when to walk away — with a confidence score and 
full reasoning trace. Built for collectors, resellers, and auction professionals 
across eBay, Heritage Auctions, LiveAuctioneers, and more.

**Why it matters:** 120 million people participate in online auctions globally. 
The vast majority bid blind — guessing at value, overbidding emotionally, and 
losing money. BidSmart gives individuals access to the same data-driven 
decision-making that professional dealers use.

**Key technical contributions:**
- Four-agent multi-agent system: Data Extraction, Market Research, 
  Price Prediction, Strategy — all powered by Anthropic Claude API
- Agent Communication Log providing real-time transparency into every 
  reasoning step (no black box)
- Supabase PostgreSQL backend with authentication, prediction history, 
  bulk analysis (up to 50 URLs), and tax/profit tracker
- Live deployed platform with photo recognition (Claude multimodal API)

**Stack:** React/TypeScript, Anthropic Claude API, Supabase, Lovable Cloud  
**Live Platform:** [bid-smart-strategies.lovable.app](https://bid-smart-strategies.lovable.app)  
**Venue:** EpiMinds UK Hackathon (Anthropic + Lovable sponsored), December 2025

---

### 8. SignBridge
**Full Title:** SignBridge: A Lucy-Inspired Multi-Agent Framework for Real-Time 
Cross-Cultural Sign Language Mediation

**What it is:** A browser-based system enabling real-time two-way communication 
between Deaf and hearing people across three different sign languages (ASL, BSL, 
ISL) — with no server, no installation, and no specialist hardware required. 
Just a webcam and a microphone.

**Why it matters:** 466 million people worldwide live with disabling hearing 
loss. A Deaf person from India relocating to London faces systematic 
communication barriers because ISL and BSL are as mutually unintelligible as 
Japanese and Spanish. No existing AI tool addresses cross-sign-language 
mediation in real time.

**Key technical contributions:**
- Five-agent architecture: Perception Agent (MediaPipe Hands, 21-point 
  landmarks at 30fps) → Sign Recognition Agent (deterministic rule-based 
  classifier, 91% accuracy, 8-frame stability buffer) → Language Identification 
  Agent (confidence-weighted sliding window scoring) → Lucy Mediation Agent 
  (deterministic priority-ordered controller) → Output Agent (Web Speech API + GIF rendering)
- Novel probabilistic sign language identification from real-time gesture streams
- Fully observable decision logging: every agent action logged with reason, 
  payload, and timestamp
- Zero backend — runs entirely in the browser

**Stack:** React 18 + Vite, MediaPipe Hands (WASM), Web Speech API, Vanilla JS  
**Venue:** Epiminds Stockholm Application, March 2026

---

## Common Themes Across All Projects

Reading across all eight papers, several recurring design principles emerge:

**1. Determinism before probability**  
Every system separates deterministic computation (risk scoring, gesture 
classification, signal processing) from probabilistic reasoning (LLMs, ML 
models). The deterministic layer is always built first and tested independently.

**2. Honest threat models**  
Every paper explicitly states what the system does NOT protect against. 
Prototype limitations are documented in the paper, not hidden. This is a 
deliberate methodological choice.

**3. Multi-layer trust**  
No single layer is trusted to solve the full problem. Hardware signs data, 
edge infrastructure preserves it, oracle networks bridge it, smart contracts 
settle it. Each layer narrows a specific trust gap.

**4. Observable decisions**  
Every agent decision, every risk score, every policy action is logged with 
a human-readable reason. Nothing happens silently.

**5. Separation of concerns**  
Perception agents never reason. Reasoning agents never perceive. Output agents 
never decide. Clean agent boundaries make failures attributable and systems improvable.

---

## About the Author

**Manthan Bhanushali** is an AI Systems Engineer and independent researcher 
based in London. He designs AI-native infrastructure at the intersection of 
machine learning, decentralized systems, and real-world networks.

- **Current role:** Founding AI Engineer at RadarKit AI
- **Previous:** Smart Contract Security Researcher at Immunefi (25+ DeFi 
  protocol audits), Crypto Asset Analyst at Coinmetrics
- **Education:** MSc Data Science & Analytics, University of Westminster; 
  BSc Management Studies (Statistics), Pune Vidyarthi College

**Contact:** manthanbhanushali7@gmail.com  
**GitHub:** [github.com/Manthanbhanushali010](https://github.com/Manthanbhanushali010)

---

## Citation

If you reference any of these papers, please cite:
```
Bhanushali, M. (2024–2026). Research Papers & Technical Projects. 
Zenodo. DOI: 10.5281/zenodo.XXXXXXX
```

*(Replace XXXXXXX with your actual Zenodo DOI after publishing the release)*

---

*All papers in this repository represent independent research and 
prototype-stage systems. Claims are scoped to demonstrated prototype 
results unless explicitly stated otherwise.*

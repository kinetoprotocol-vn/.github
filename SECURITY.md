# Security Policy & Vulnerability Disclosure Guidelines

The **Axioledger Ecosystem** (`axioledger-monorepo`) manages high-value decentralized infrastructure spanning L1 settlement (`01-axioledger-core`), validator consensus (`02-valiprecision-net`), L2 SVM execution (`03-sequentichain-l2`), zero-knowledge provers (`04-veraciphers-zk`), and concentrated liquidity protocols (`05-kinetoprotocol-dex`).

We treat security as an absolute prerequisite. We invite security researchers, developers, and partners to inspect our open-source codebase and report any potential vulnerabilities responsibly.

---

## 1. Reporting a Vulnerability

**DO NOT** create public GitHub issues or disclose security vulnerabilities on public forums (Discord, Telegram, X/Twitter) prior to patch confirmation and advisory release.

### Official Disclosure Channel

To submit a security report, send an encrypted email to our dedicated Security Operations Center (SOC):

- **Security Contact:** `security@axioledger.org`
- **PGP Key Fingerprint:** `A3F8 9B2C 4D1E 7E0A 8F5B 2C1D 9E8F 7A6B 5C4D`
- **Encrypted Communication:** Please use PGP encryption when submitting details involving sensitive zero-day exploits or key manipulation vectors.

### Required Information in Your Submission

To help us triage and validate your report quickly, please include:

1. **Module / Location:** Specific path in the monorepo (e.g., `04-veraciphers-zk/onchain-verifier/` or `05-kinetoprotocol-dex/clamm-core/`)
2. **Vulnerability Type:** Reentrancy, ZK-Circuit soundness flaw, Arithmetic overflow/underflow, Anti-frontrunning bypass, Consensus slashing bypass, Oracle manipulation, or Logic flaw
3. **Impact Assessment:** Potential threat to funds, system downtime, privacy leakage, or unauthorized governance execution
4. **Proof of Concept (PoC):** Minimal reproducible script or test case (e.g., a `moccasin test` PoC or Rust integration test)
5. **Mitigation Suggestion:** Any recommended fix or architecture adjustment

---

## 2. Response Timelines & SLA

When a security report is submitted to `security@axioledger.org`, our triage team follows this strict timeline:

| Stage | SLA Timeframe | Action |
|:---|:---|:---|
| **Initial Acknowledgment** | Within **12 Hours** | Receipt confirmation and ticket creation |
| **Triage & Validation** | Within **48 Hours** | Assessment of severity and impact validation |
| **Patch Development & Testing** | **3 to 7 Days** | Private patch creation, invariant testing, and circuit verification |
| **Deployment & Public Advisory** | **Post-Fix Verification** | Safe patch deployment to Mainnet/Subnets and coordinated public release |

---

## 3. Scope & Criticality Matrix

### In-Scope Codebase

The following core modules within `axioledger-monorepo` are eligible for evaluation:

- **`01-axioledger-core`:** Post-Quantum Lattice cryptography, MPT state storage, Tribunal ZK Jury, Decay Functions `D(t)`, and Dual-Chamber DAO contracts
- **`02-valiprecision-net`:** ZK-OBFT consensus engine, AF_XDP socket processing, and Validator telemetry indexers
- **`03-sequentichain-l2`:** SVM runtime, Low-latency Sequencer batching, MEV-boost fair ordering, and Paymaster contracts
- **`04-veraciphers-zk`:** Halo2 / PlonKy2 Circuit Compiler, Prover aggregation circuits, ZK-KYC verification contracts, and MACI anti-bribery circuits
- **`05-kinetoprotocol-dex`:** CLAMM pool math, AMM routing, Auto-Rebalancing Vaults, `$veKPX` gauges, and Automated Circuit Breakers

### Out of Scope

- Third-party dependencies or external RPC providers, unless the flaw exists in Axioledger's integration layer
- Social engineering, phishing, or physical attacks against Axioledger contributors or validator operators
- Non-security UI/UX bugs or minor typos that do not compromise state integrity

---

## 4. Bug Bounty Program & Rewards

Axioledger offers rewards for critical security findings disclosed in accordance with this policy. Rewards are evaluated based on the **CVSS v3.1** rating and business impact:

| Severity Level | CVSS Score | Maximum Reward | Key Examples |
|:---|:---|:---|:---|
| **Critical** | 9.0 – 10.0 | **Up to $500,000** | Direct theft of locked funds, double-spend, ZK-Proof forge, consensus halt |
| **High** | 7.0 – 8.9 | **Up to $100,000** | Temporary loss of funds, MEV extraction bypass, oracle manipulation |
| **Medium** | 4.0 – 6.9 | **Up to $25,000** | Unclaimed yield lockup, gas exhaustion DoS, incorrect voting weight decay |
| **Low** | 0.1 – 3.9 | **Up to $5,000** | Informational logic edge cases, minor state desynchronization |

> Rewards are distributed in stablecoins (USDC) or native ecosystem tokens (`$AXQ`, `$KPX`, `$VRQ`).

---

## 5. Emergency Incident Response & Circuit Breakers

Axioledger implements multi-layered defensive engineering to safeguard partner assets:

### Automated Circuit Breakers
**Module:** `05-kinetoprotocol-dex/security-monitoring`

- Real-time telemetry monitors liquidity pools for anomalous withdrawal rates or flash-loan manipulations
- If an anomaly exceeds safety thresholds, the protocol automatically triggers an emergency pause on affected vaults

### Security Council & Guardian Multisig

- In the event of a Critical zero-day exploit, the Axioledger Emergency DAO Guard can pause affected L2 sequencers or bridges for up to **48 hours** to apply patches

### Safe Harbor Provision

> Any security research conducted in good faith under the **Controlled-Environment Security Research License (CESRL)** and disclosed via official channels will be considered authorized. Axioledger will not initiate legal action against researchers acting in good faith.

---

## 6. Official Security Audits

Public audit reports conducted by independent security firms for the Axioledger Monorepo modules are archived at:

```
https://github.com/axioledger/axioledger-monorepo/tree/main/audits
```

---

*Thank you for helping keep the Axioledger Ecosystem and our partner network secure!*

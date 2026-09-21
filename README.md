# FinSc-Fields

[![Idris 2 Verification](https://img.shields.io/badge/Idris_2-0.8.0-blue.svg)](https://www.idris-lang.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**Layer 7 Monadic Session Types, Gauge Group Actions & Gauge Flux Fields for Idris 2**

`FinSc-Fields` forms **Layer 7** of the 10-layer constructive non-linear multiset science framework. It formalizes linear session types for gauge field protocols (`SessionProto`), session protocol duality (`dualProto`), metrically synchronized linear channels (`GaugeSyncChannel`), discrete U(1) gauge group phase transformations (`GaugePhase`), gauge field tensors (`GaugeFieldTensor`), electromagnetic energy density ($Q_{\text{EM}} = E^2 + B^2$), 4D dihedral phase transformations, and compile-time proof witnesses for gauge invariance.

---

## 📦 Core Library Architecture & Modules

### 1. `Math.Fields.SessionType`
- **Linear Session Protocols:** Protocol state AST (`SessionProto`: `Send a p`, `Recv a p`, `Close`) tracking linear gauge field communications.
- **Protocol Duality:** Dual protocol mapping (`dualProto`) transforming `Send` $\leftrightarrow$ `Recv`, with a compile-time proof witness that double dualization is the identity (`verifySessionDuality`).
- **Linear Channels:** `Channel p` and `GaugeSyncChannel dim color p` supporting linear transmission (`sendGaugeToken`, `sendMetricalGaugeTensor`) and reception (`recvGaugeToken`, `recvMetricalGaugeTensor`) with strict linear resource accounting ($\text{Multiplicity } 1$).

### 2. `Math.Fields.GaugeGroup`
- **Discrete U(1) Gauge Phase Group:** Phase elements (`GaugePhase`), phase multiplication (`mulGaugePhase`), and inverse phases (`invGaugePhase`).
- **Gauge Field Tensors:** Electromagnetic field tensors (`GaugeFieldTensor`) holding Electric vector $E$ and Magnetic flux $B$ components.
- **Energy Density ($Q_{\text{EM}} = E^2 + B^2$):** Exact energy density calculation (`computeFieldEnergy`) and metrically bounded spatial transport (`transportField`).
- **Multi-Phase Warping & Invariance Proofs:**
  - U(1) Gauge Warping (`warpFieldByGaugeTensor`) and proof witness `verifyGaugeInvariance`.
  - 4D Dihedral Phase Warping (`warpFieldByDihedralPhase`) and proof witness `verifyDihedralGaugeInvariance`.
  - Linear Spinor Warping (`warpSpinorByGaugeLinear`) and proof witness `verifySpinorGaugeInvariance`.
  - Galois Gauge Invariance Lifting (`gaugeGaloisInvariant`).

---

## 🚀 Building & Installing

```bash
idris2 --build FinSc-Fields.ipkg
idris2 --install FinSc-Fields.ipkg
```

---

## 🔬 Architectural Principles

- **Total Constructivism:** Enforces `%default total` across all session typing and gauge field modules.
- **Linear Session Communication:** Quantitative Type Theory (QTT) linear session channels preventing state leakage or channel cloning.
- **Gauge Energy Invariance:** Type-level proof witnesses verifying $Q_{\text{EM}} = E^2 + B^2$ conservation under U(1), 4D dihedral, and spinor transformations.
- **Zero Floating-Point Drift:** Pure rational phase calculations over exact fields (`UnixelFraction`).

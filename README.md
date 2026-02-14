# DAO Governance Simulation for Real Estate

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE.txt)
[![Research](https://img.shields.io/badge/research-UTHM-green.svg)](https://www.uthm.edu.my/)

A multi-agent simulation platform for comparing decentralized autonomous organization (DAO) governance models in tokenized real estate management.

##  Research Paper

This simulation implements the methodology described in:

> **"A Hierarchical AI-Agent Governance Model for Real-Estate DAOs: Architecture and Simulation Study"**
>
> Muhammad Shahid, Suziyanti Marjudi, Abd Samad Hasan Basari
>
> Universiti Tun Hussein Onn Malaysia (UTHM)

## Authors

| Author | Affiliation | 
|--------|-------------|
| **Muhammad Shahid** | UTHM, Malaysia | 
| **Suziyanti Marjudi** | UTHM, Malaysia | 
| **Abd Samad Hasan Basari** | UTHM, Malaysia | 

## Overview

This simulation compares three generations of DAO governance models:

| Generation | Description | Key Features |
|------------|-------------|--------------|
| **DAO 1.0** | Basic token-voting | Whale dominance, voter apathy, slow coordination |
| **DAO 2.0** | Modular governance | Semi-automation, quadratic voting, partial improvements |
| **DAO 3.0** | Hierarchical AI-agents | Full automation, regulatory/economic/operational agents |

### Simulation Features

-  **100 tokenized properties** with dynamic states
- **Multi-agent hierarchy** (regulatory, economic, operational)
- **Oracle/IoT event simulation** (rental requests, compliance checks, maintenance alerts)
- **Safety invariants enforcement** (consensus validity, data integrity, budget constraints, access control)
- **Gas estimation** with optional Ganache integration
- **Comprehensive metrics** and visualizations

## Key Metrics

The simulation evaluates:

1. **Governance Latency** - Average decision time (proposal → execution)
2. **Compliance Resilience** - Percentage of decisions validated under safety invariants
3. **Cost-Effectiveness** - Estimated gas fees + off-chain computation overhead
4. **ROI** - Return on investment based on governance efficiency

### Expected Results

| Metric | DAO 1.0 | DAO 2.0 | DAO 3.0 |
|--------|---------|---------|---------|
| Avg Latency | ~15.8s | ~9.5s | ~4.2s |
| Compliance | ~71% | ~83% | ~98% |
| Governance Cost | $120,000 | $90,000 | $55,000 |
| ROI | ~1.0% | ~4.0% | ~7.5% |

## Installation

### Requirements

- Python 3.10 or higher
- matplotlib (required)
- web3.py (optional, for Ganache integration)

### Setup

```bash
# Clone the repository
git clone https://github.com/yourusername/dao-governance-simulation.git
cd dao-governance-simulation

# Install dependencies
pip install matplotlib

# Optional: Install web3 for Ganache integration
pip install web3
```

## Usage

### Basic Usage

```bash
python dao_governance_simulation.py
```

### Command Line Options

```bash
python dao_governance_simulation.py [OPTIONS]

Options:
  --rounds INT        Number of simulation rounds (default: 1000)
  --properties INT    Number of tokenized properties (default: 100)
  --seed INT          Random seed for reproducibility (default: 42)
  --outdir PATH       Output directory for results (default: ".")
  --use-ganache       Enable Ganache integration for gas estimation
  --ganache-url URL   Ganache RPC URL (default: http://127.0.0.1:8545)
```

### Examples

```bash
# Run with default settings
python dao_governance_simulation.py

# Run with custom parameters
python dao_governance_simulation.py --rounds 500 --properties 50 --seed 123

# Run with Ganache integration
python dao_governance_simulation.py --use-ganache --ganache-url http://localhost:8545

# Save outputs to specific directory
python dao_governance_simulation.py --outdir ./results
```

## 📁 Output Files

The simulation generates the following outputs:

### CSV Files
| File | Description |
|------|-------------|
| `dao_10_metrics.csv` | Per-round metrics for DAO 1.0 |
| `dao_20_metrics.csv` | Per-round metrics for DAO 2.0 |
| `dao_30_metrics.csv` | Per-round metrics for DAO 3.0 |

### Visualization Files
| File | Description |
|------|-------------|
| `fig6.png` | Bubble plot: Latency vs Compliance (size=cost, color=ROI) |
| `fig7.png` | Distribution of governance latency across DAO generations |
| `fig8.png` | Distribution of compliance resilience across DAO generations |
| `fig9.png` | Average ROI with standard deviation error bars |

##  Figures

### Figure 6: Latency vs Compliance Resilience
Scatter/bubble visualization showing the trade-off between governance speed and compliance, with bubble size representing governance cost and color intensity indicating ROI.

### Figure 7: Governance Latency Distribution
Violin plots comparing the distribution of decision-making times across DAO generations, demonstrating DAO 3.0's superior speed and consistency.

### Figure 8: Compliance Resilience Distribution
Violin plots showing how compliance rates are distributed, highlighting DAO 3.0's high and consistent compliance performance.

### Figure 9: ROI Comparison
Bar chart with error bars comparing average return on investment, demonstrating the economic benefits of AI-agent governance.

##  Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      DAO 3.0 Architecture                    │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │ Regulatory  │  │  Economic   │  │ Operational │         │
│  │   Agent     │  │   Agent     │  │   Agent     │         │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘         │
│         │                │                │                 │
│         └────────────────┼────────────────┘                 │
│                          │                                  │
│                  ┌───────▼───────┐                          │
│                  │ Smart Contracts│                          │
│                  │   (Ethereum)   │                          │
│                  └───────┬───────┘                          │
│                          │                                  │
│         ┌────────────────┼────────────────┐                 │
│         │                │                │                 │
│  ┌──────▼──────┐  ┌──────▼──────┐  ┌──────▼──────┐         │
│  │   Oracle    │  │    IoT      │  │  Digital    │         │
│  │   Feeds     │  │  Devices    │  │   Twins     │         │
│  └─────────────┘  └─────────────┘  └─────────────┘         │
└─────────────────────────────────────────────────────────────┘
```

##  Safety Invariants

The simulation enforces four safety invariants:

1. **Consensus Validity**
   - DAO 1.0: Token vote threshold only
   - DAO 2.0: At least 2 of 3 agent approvals
   - DAO 3.0: All three agent approvals required

2. **Data Integrity**
   - Oracle data cross-verified by 2 independent feeds
   - Tolerance thresholds vary by DAO generation

3. **Budget Constraint**
   - Spending cannot exceed allocated budget
   - Strictness increases from DAO 1.0 to 3.0

4. **Access Control**
   - Role-based permissions enforcement
   - Minimal (1.0) → Partial (2.0) → Strict (3.0)

##  Economic Model

Based on the paper's worked example:

```
Parameters:
  G (Gross Rent)      = $200,000/year
  O (Operating Exp)   = $70,000/year
  P (Equity)          = $1,000,000

Formula:
  Net Income (N) = G - O - Governance Cost
  ROI = N / P

Results:
  DAO 1.0: N = $10,000  → ROI = 1.0%
  DAO 2.0: N = $40,000  → ROI = 4.0%
  DAO 3.0: N = $75,000  → ROI = 7.5%
```

##  Reproducibility

The simulation uses deterministic random seeding for reproducible results:

```bash
# Default seed (42) produces consistent results
python dao_governance_simulation.py --seed 42

# Use different seeds for sensitivity analysis
for seed in 1 2 3 4 5; do
  python dao_governance_simulation.py --seed $seed --outdir results_$seed
done
```

##  Citation

If you use this simulation in your research, please cite:

```bibtex
@article{shahid2025hierarchical,
  title   = {A Hierarchical AI-Agent Governance Model for Real-Estate DAOs: Architecture and Simulation Study},
  author  = {
    Shahid, Muhammad
    and Marjudi, Suziyanti
    and Basari, Abd Samad Hasan
  },
  year    = {2025},
  institution = {Universiti Tun Hussein Onn Malaysia}
}
```

## 📜 License

This software is proprietary. All rights reserved.

See [LICENSE.txt](LICENSE.txt) for full terms.

**© 2025 Muhammad Shahid, Suziyanti Marjudi, Abd Samad Hasan Basari**

##  Acknowledgments

This research was supported by **Universiti Tun Hussein Onn Malaysia (UTHM)** through **Tier 1 (vot J122)**.

##  Contact

For questions, permissions, or collaboration inquiries, please contact the authors at the email addresses listed above.

---

<p align="center">
  <img src="https://www.uthm.edu.my/images/logo-uthm.png" alt="UTHM Logo" width="200"/>
</p>

<p align="center">
  <strong>Universiti Tun Hussein Onn Malaysia</strong><br>
  Faculty of Computer Science and Information Technology
</p>

<div align="center">

# Dr. P. Praveen Kumar

**Energy Systems Researcher Â· Optimization Engineer Â· Energy Trading Specialist**

*PostDoc Researcher â€” INESC TEC, Porto, Portugal*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/praveen-kumar-polamarasetty)
[![Google Scholar](https://img.shields.io/badge/Google_Scholar-4285F4?style=for-the-badge&logo=google-scholar&logoColor=white)](https://scholar.google.com)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sudikdivik)

![Profile Views](https://komarev.com/ghpvc/?username=sudikdivik&color=blue&style=flat-square)

</div>

---

## About Me

I am a PostDoc researcher at **INESC TEC Porto** working at the intersection of energy systems research and industrial energy trading. My work focuses on building production-grade optimization systems that schedule hydro-solar-battery portfolios on Iberian electricity markets â€” the kind of code that runs in control rooms, not just in papers.

- ðŸŽ“ **PhD** â€” Indian Institute of Technology (IIT) Roorkee
- ðŸ“ **Location** â€” Porto, Portugal
- ðŸ›ï¸ **Institution** â€” INESC TEC (Institute for Systems and Computer Engineering, Technology and Science)
- ðŸ“Š **1,350+ citations Â· h-index 21** Â· Scopus-verified
- âš¡ **Research focus** â€” PSP + PV + BESS co-optimization, MILP, Iberian energy markets

I am actively transitioning from academic research into industry roles in **energy trading, asset optimization, and power systems engineering**.

---

## Technical Stack

### Optimization & Mathematical Programming
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Pyomo](https://img.shields.io/badge/Pyomo-MILP_Modelling-orange?style=flat-square)
![HiGHS](https://img.shields.io/badge/HiGHS-Open_Source_Solver-green?style=flat-square)
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=flat-square&logo=mathworks&logoColor=white)

**Solvers:** HiGHS Â· CPLEX Â· Gurobi Â· CBC  
**Frameworks:** Pyomo Â· PuLP Â· CVXPY  
**Problem classes:** MILP Â· MIQP Â· LP Â· Stochastic Programming  

### Energy Markets & Systems
| Domain | Expertise |
|--------|-----------|
| **Markets** | OMIE Iberian DA, aFRR/PICASSO, ENTSO-E |
| **Settlement** | ISP15 imbalance, 96-period quarter-hourly |
| **Assets** | Pumped-storage hydro (PSP), utility-scale PV, BESS |
| **Risk** | VaR, CVaR, Historical simulation, Monte Carlo |
| **Regulations** | EU capacity markets, balancing mechanism |

### Software Engineering
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)

**Architecture patterns:** CLI-driven pipelines Â· SQLite audit logs Â· Four-eyes approval workflows Â· Config-driven design

---

## Featured Project

### [psp-optimizer](https://github.com/sudikdivik/psp-optimizer) â€” Industrial PSP+PV+BESS Trading System

> *Production-grade day-ahead scheduling system for a pumped-storage + solar + battery portfolio on the OMIE Iberian market. Built to the standard of a real energy trading desk.*

```
PSP (Alqueva, 256 MW) + PV (50 MW) + BESS (20 MW / 80 MWh)
      â†“ MILP (Pyomo + HiGHS)
   Day-Ahead Schedule â†’ OMIE Bid â†’ Four-Eyes Approval â†’ Settlement
```

**What makes it industrial-grade:**
- âœ… Full MILP model: unit commitment, SOS2 efficiency curves, McCormick head coupling
- âœ… OMIE DA market bidding + aFRR/PICASSO reserve co-optimisation
- âœ… Four-eyes approval workflow (PENDING â†’ APPROVED â†’ SUBMITTED)
- âœ… VaR/CVaR risk engine: historical simulation + 10,000 Monte Carlo resamples
- âœ… ISP15 imbalance settlement (96 quarter-hourly periods)
- âœ… SQLite audit trail, config-driven YAML, full CLI (`da` / `approve` / `settle`)
- âœ… 30-day backtest: 30/30 days optimal, avg 1.0 s/day

**Tech:** Python Â· Pyomo Â· HiGHS Â· SQLite Â· pandas Â· PyYAML Â· pytest

---

## Research Areas

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚  Energy Storage Optimization                            â”‚
â”‚  â”œâ”€â”€ Pumped-storage hydro scheduling                   â”‚
â”‚  â”œâ”€â”€ Battery energy storage (BESS) dispatch            â”‚
â”‚  â””â”€â”€ Hybrid PSP + PV + BESS co-optimization           â”‚
â”‚                                                         â”‚
â”‚  Electricity Markets                                    â”‚
â”‚  â”œâ”€â”€ Day-ahead market bidding strategies               â”‚
â”‚  â”œâ”€â”€ Reserve capacity (aFRR/PICASSO)                   â”‚
â”‚  â””â”€â”€ Imbalance settlement mechanisms                   â”‚
â”‚                                                         â”‚
â”‚  Risk & Uncertainty                                     â”‚
â”‚  â”œâ”€â”€ Stochastic price forecasting                      â”‚
â”‚  â”œâ”€â”€ VaR / CVaR portfolio risk                         â”‚
â”‚  â””â”€â”€ Scenario-based robust optimisation               â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

---

## Publications & Impact

| Metric | Value |
|--------|-------|
| Total Citations | **1,350+** |
| h-index | **21** |
| i10-index | Available on Google Scholar |
| PhD Institution | **IIT Roorkee** |
| Current Position | **PostDoc, INESC TEC Porto** |

---

## Let's Connect

I am open to discussions on:
- **Energy trading & optimization** roles in Europe
- **Asset management** software for renewables + storage
- **Research collaborations** in energy systems

ðŸ“§ Reach me via [LinkedIn](https://linkedin.com/in/praveen-kumar-polamarasetty) or open an issue/discussion on any repository.

---

<div align="center">

*"The best optimizer is one that runs in production."*

</div>

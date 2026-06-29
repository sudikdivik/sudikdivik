![Header](https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=220&section=header&text=Dr.%20Polamarasetty%20Praveen%20Kumar&fontSize=36&fontColor=ffffff&fontAlignY=40&desc=Energy%20Asset%20Optimisation%20%7C%20Multi-Market%20Bidding%20%7C%20MILP%20Dispatch&descSize=18&descAlignY=62&animation=fadeIn)

<p align="center">
  <a href="https://linkedin.com/in/polamarasetty-praveen-kumar-2a3a422a1">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
  </a>
  <a href="https://scholar.google.com/citations?user=8EFqCyAAAAAJ">
    <img src="https://img.shields.io/badge/Google%20Scholar-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white"/>
  </a>
  <a href="mailto:praveenindia.p@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>
  <img src="https://img.shields.io/badge/Available-July%202026-brightgreen?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/EU%20Work%20Auth-Portugal-003399?style=for-the-badge&logo=europeanunion&logoColor=white"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1000&color=2C8EBB&center=true&vCenter=true&width=600&lines=Energy+Trading+Engineer+%26+MILP+Optimisation;DA+%7C+IDA+%7C+XBID+%7C+aFRR+%7C+mFRR+Pipeline;IBM+CPLEX+%7C+Python+%7C+Risk+Analytics;Iberian+Power+Markets+%E2%80%94+MIBEL+%2F+OMIE;H-Index+23+%C2%B7+1%2C538+Citations+%C2%B7+70%2B+Publications"/>
</p>

---

## 👤 About Me

> Energy systems researcher and industrial-grade software engineer with deep expertise in **hybrid plant optimisation, multi-market bidding and scheduling, and MILP-based dispatch**.

Built a production-grade **14-gate multi-market MILP bidding and scheduling system** (DA, IDA1/2/3, XBID, aFRR, mFRR, ISP dispatch simulation, settlement, and analytics) for the real **Alqueva hybrid plant** (518.4 MW PSP + 5 MWp PV + 1 MW / 2 MWh BESS, Portugal / MIBEL). System uses IBM CPLEX, auto-selects ML forecasters via walk-forward CV, and applies a permanent **13-invariant physical checker** that blocks any bid with a constraint violation before it propagates. Risk framework includes historical VaR/CVaR and Monte Carlo bootstrap confidence intervals.

---

## ⚡ Flagship Project: Alqueva 24-Hour Energy Trading Optimizer

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/IBM%20CPLEX-054ADA?style=for-the-badge&logo=ibm&logoColor=white"/>
  <img src="https://img.shields.io/badge/HiGHS%20%7C%20CBC-Fallback-4CAF50?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/MILP-Optimisation-FF6B35?style=for-the-badge"/>
  <br/>
  <img src="https://img.shields.io/badge/DA%20%7C%20IDA1--3%20%7C%20XBID-Markets-7B2FBE?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/aFRR%20%7C%20mFRR-Ancillary-9C27B0?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/MIBEL%20%7C%20OMIE%20%7C%20REN-Grid-C62828?style=for-the-badge"/>
</p>

<p align="center">
  <i>Production-grade MILP trading pipeline for the <b>Alqueva hybrid plant</b> — Iberian electricity market (MIBEL / OMIE)</i>
</p>

### 🏭 Plant

| Asset | Specification |
|:------|:-------------|
| **PSP: Pumped Storage** | 4 × 129.6 MW reversible Francis units, 518.4 MW generation / 446.4 MW pumping |
| **PV: Floating Solar** | 5 MWp, commissioned 2022 |
| **BESS: Battery** | 1 MW / 2 MWh, SOC 10–95 % |
| **Upper Reservoir** | Alqueva, 3,150 hm³ usable |
| **Lower Reservoir** | Pedrógão, 54 hm³ usable |

### 🔄 15-Phase Pipeline

| Phase | Gate | Scope |
|:------|:-----|:------|
| **1: DA** | OMIE D-1 12:00 | H1–H24 energy bids |
| **2A: IDA1** | OMIE SIDC D-1 15:00 | Position delta re-optimisation |
| **2B: IDA2** | OMIE SIDC D-1 22:00 | Position delta re-optimisation |
| **2C: IDA3** | OMIE SIDC D 10:00 | Position delta re-optimisation |
| **2D: XBID** | SIDC continuous H-1 | Cross-border continuous intraday |
| **3A: aFRR** | PICASSO DA+1h | Symmetric ±MW capacity |
| **3B: mFRR** | MARI DA+1h | Symmetric ±MW capacity |
| **4A: RT Dispatch** | 96 ISPs × 15 min | REN signal simulation |
| **4B: aFRR Activation** | Real-time | TSO activation response |
| **4C: mFRR Activation** | Real-time | TSO activation response |
| **5A: Energy Settlement** | Post-delivery | DA / IDA imbalance reconciliation |
| **5B: Reserve Settlement** | Post-delivery | aFRR / mFRR payment calculation |
| **5C: Imbalance Settlement** | Post-delivery | REN 15-min ISP penalty calculation |
| **5D: Analytics** | End-of-day | KPI report, 5-sheet Excel, 9 figures |

### 🏗️ Architecture Highlights

- **Single shared MILP model**: `core_milp_solver.py` used by all 15 phases; each phase passes its own horizon, frozen variables, and market constraints
- **`--from-phase` hot-restart**: re-enter at any phase without re-running earlier phases; production-safe for intraday gate re-optimisation
- **ComponentStore**: typed dataclass store shared across all phases; zero file I/O between phases
- **13-invariant physical checker**: re-derives dispatch from solved schedule and checks mode exclusivity, ramp rates, reservoir bounds, BESS SoC, energy balance, and FAT deliverability before any result propagates
- **ML forecasting pipeline**: DA price, aFRR, mFRR, PV power, and water inflow forecasters each auto-select best model (Naive / Ridge / LightGBM) via 4-fold walk-forward CV
- **Risk analytics**: historical VaR (95%/99%) and CVaR/Expected Shortfall; Monte Carlo bootstrap; annualised Sharpe ratio; max drawdown; P&L attribution by stream
- **Immutable audit trail**: append-only JSON-lines log of every decision with market-time timestamps; designed for regulatory inspection
- **CPLEX 22.1 primary / HiGHS fallback**: automatic solver detection; same model runs on any machine
- **15-min ISP resolution**: 96 intervals/day matching REN grid operator standard

---

## 🛠️ Technical Skills

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,matlab,git,github,vscode&theme=dark"/>
</p>

| Area | Skills |
|:-----|:-------|
| **Optimisation** | MILP formulation, Pyomo, IBM CPLEX, HiGHS, CBC, unit commitment, piecewise-linear turbine/pump curves, McCormick linearization |
| **Energy Markets** | OMIE DA/IDA, SIDC IDA1/2/3 (post-Jun 2024 reform), aFRR via PICASSO, mFRR via MARI, XBID continuous intraday, ISP imbalance settlement, FCR headroom reservation |
| **Risk & P&L** | VaR & CVaR (historical simulation + Monte Carlo bootstrap), Sharpe ratio, max drawdown, P&L attribution by stream, pre-trade risk checks, audit logging |
| **ML & Forecasting** | LightGBM, Ridge regression, Naive baseline, walk-forward CV, lag/rolling/cyclical calendar features |
| **Programming** | Python, pandas, NumPy, Pyomo, scikit-learn, LightGBM, openpyxl, SQLite, Git/GitHub, YAML config, pytest |
| **Systems & Data** | OMIE live API, PICASSO/MARI/REN structured data, ENTSO-E market frameworks, ERA5 reanalysis (PV weather), Excel report generation |
| **Asset Knowledge** | Pumped-storage hydropower (Francis reversible units), floating solar PV, BESS (SoC tracking, cycle degradation), reservoir dynamics, head-dependent efficiency curves |

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Praveen-Kumar-Energy&show_icons=true&theme=tokyonight&hide_border=true&count_private=true" height="160"/>
  &nbsp;
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Praveen-Kumar-Energy&layout=compact&theme=tokyonight&hide_border=true" height="160"/>
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=Praveen-Kumar-Energy&theme=tokyo-night&hide_border=true&area=true"/>
</p>

---

## 💼 Professional Experience

### 🔬 Energy Optimisation Engineer (PostDoc Researcher)
**INESC TEC, Centre for Power and Energy Systems (CPES), Porto, Portugal** &nbsp;|&nbsp; *Feb 2025 – Present*

*STOR-HY (Horizon Europe GA 101172905), Alqueva Hybrid Plant: 4 × 129.6 MW reversible Francis PSP + 5 MWp Floating PV + 1 MW / 2 MWh BESS*

- Built a 14-gate end-to-end automated bidding and scheduling pipeline covering DA, IDA1/2/3, XBID, aFRR, mFRR, ISP dispatch simulation, activations, settlement, and daily analytics; all orchestrated from a single `run_production.py` with full audit logging; IDA bids are position deltas (post-June-2024 MIBEL reform)
- ML forecasting pipeline: DA price, aFRR, mFRR, PV power, and water inflow forecasters each auto-select best model (Naive / Ridge / LightGBM) via 4-fold walk-forward CV with lag, rolling, and cyclical calendar features
- Physical plant modelling: piecewise-linear turbine efficiency curves; full upper/lower reservoir dynamics with monthly natural inflow; BESS SoC tracking with charge/discharge commitment
- Permanent 13-invariant physical checker: re-derives dispatch from solved schedule before any result propagates; checks mode exclusivity, ramp rates, reservoir bounds, BESS SoC, energy balance, and FAT deliverability
- Risk analytics framework: historical VaR (95%/99%) and CVaR/Expected Shortfall; Monte Carlo bootstrap; annualised Sharpe ratio and max drawdown
- Immutable audit trail: append-only JSON-lines logging every decision with market-time timestamps; designed for regulatory inspection and post-trade accountability
- Participated in consortium technical meetings with **EDP Produção, EDP New Energy Technologies, EDF, and GE Vernova** within the STOR-HY Horizon Europe project

### 🎓 Assistant Professor
**GMR Institute of Technology, Rajam, India** &nbsp;|&nbsp; *Jul 2021 – Jan 2025*

Power systems and renewable energy teaching; hybrid energy systems research.

### 🔬 PhD Research Scholar
**IIT Roorkee, Dept. of Hydro and Renewable Energy** &nbsp;|&nbsp; *Jul 2018 – Jul 2021*

- Designed and optimized hybrid renewable energy systems (PV, wind, biomass, BESS) for rural electrification in India
- Applied metaheuristic optimization in MATLAB to minimize LCC and LCOE across multiple battery technologies and dispatch strategies
- Published complete optimization code on MathWorks File Exchange (open-source, reproducible research)

**PhD Code (MATLAB):** [Optimization of Off-Grid Microgrid with Different Batteries](https://in.mathworks.com/matlabcentral/fileexchange/117260-optimization-of-off-grid-microgrid-with-different-batteries), MathWorks File Exchange, MATLAB R2018a–R2022a

### 🎓 Assistant Professor
**GMR Institute of Technology, Rajam, India** &nbsp;|&nbsp; *May 2013 – Jun 2018*

Power systems and electrical engineering teaching; early research in smart grids and hybrid microgrids.

---

## 🎓 Education

| Degree | Institution | Year |
|:-------|:------------|:-----|
| **Ph.D.** in Renewable Energy | IIT Roorkee, India | 2018 – 2021 |
| **M.E.** in Power Electronics Drives & Control | Andhra University, India | 2010 – 2012 |
| **B.Tech** in Electrical & Electronics Engineering | JNTU Kakinada, India | 2006 – 2010 |

---

## 🤝 Industrial Collaborations & Funded Projects

<table>
<tr>
<td width="50%">

**STOR-HY** &nbsp; `Horizon Europe GA 101172905` &nbsp; `2025–Present`

Partners: EDP Produção, EDP New Energy Technologies, EDF, GE Vernova

*Built core MILP optimisation system for the Alqueva hybrid plant*

</td>
<td width="50%">

**SE-HYDRO** &nbsp; `Horizon Europe GA 101269565` &nbsp; `May 2026–`

16-partner consortium: NTUA, ANDRITZ HYDRO, EDP, GE Vernova, PPC Greece, Smart Innovation Norway

*Co-authored grant proposal; AI-based energy management and digital twin frameworks for hydro pilot sites in Greece, France, Portugal and Serbia*

</td>
</tr>
</table>

---

## 📚 Research Impact

<p align="center">
  <img src="https://img.shields.io/badge/Publications-70%2B-1565C0?style=for-the-badge&logo=bookstack&logoColor=white"/>
  <img src="https://img.shields.io/badge/H--Index-23-2E7D32?style=for-the-badge&logo=googlescholar&logoColor=white"/>
  <img src="https://img.shields.io/badge/Citations-1%2C538-E65100?style=for-the-badge&logo=googlescholar&logoColor=white"/>
</p>

<p align="center">
  <a href="https://scholar.google.com/citations?user=8EFqCyAAAAAJ">
    <img src="https://img.shields.io/badge/View%20Google%20Scholar%20Profile-4285F4?style=for-the-badge&logo=googlescholar&logoColor=white"/>
  </a>
</p>

---

<p align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=Praveen-Kumar-Energy&theme=tokyonight&no-frame=true&margin-w=12&column=4"/>
</p>

![Footer](https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=120&section=footer)

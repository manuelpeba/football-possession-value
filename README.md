# Football Possession Value
### Data-Driven Tactical Analysis with Event Data

A football analytics project that models **possession value and player impact** using event data.

The goal is to quantify how individual actions contribute to goal probability and to identify players who generate real attacking value through ball progression, creativity and decision making.

This project implements modern football analytics concepts such as **Expected Threat (xT)** and **VAEP-style action valuation** using open event data.

---

# Project Overview

Traditional football statistics such as goals and assists fail to capture the value of actions earlier in attacking sequences.

For example:

- a progressive pass breaking defensive lines  
- a carry into the final third  
- a cutback before a shot  

These actions can dramatically increase the probability of scoring.

This project builds a framework that assigns **value to each on-ball action** and aggregates these values to measure **player impact and tactical profiles**.

---

# Dataset

Event data is sourced from **StatsBomb Open Data**.

The dataset contains detailed match event logs including:

- passes
- carries
- shots
- defensive actions
- possession sequences
- spatial coordinates of events

Each event includes contextual information such as:

- location on the pitch
- player
- team
- possession sequence
- pressure status

This allows the reconstruction of attacking sequences and the modelling of possession value.

---

# Methodology

The project follows three modelling layers.

## 1. Expected Threat (xT)

A spatial model that assigns value to pitch zones.

Each action is valued as the increase in threat between the start and end locations:

ΔxT = xT(destination) − xT(origin)

This provides a simple and interpretable baseline model.

---

## 2. VAEP-style Action Valuation

A supervised learning model predicts:

- probability of scoring in the next actions
- probability of conceding

Action value is defined as:

Value(action) = ΔP(score) − ΔP(concede)

This approach captures contextual features such as action type, pressure and possession state.

---

## 3. Player Value & Tactical Profiles

Action values are aggregated to measure:

- value added per 90 minutes
- progression value
- creative value
- turnover cost

These metrics allow the identification of players who generate attacking value beyond traditional statistics.

---

# Project Structure

```bash
football-possession-value
│
├── data
│   ├── raw
│   └── processed
│
├── db
│
├── notebooks
│   ├── 01_data_ingestion.ipynb
│   ├── 02_event_model.ipynb
│   ├── 03_xT_model.ipynb
│   ├── 04_vaep_training.ipynb
│   ├── 05_player_value_analysis.ipynb
│   ├── 06_team_tactical_style.ipynb
│   ├── 07_player_role_fit.ipynb
│   └── 08_reporting.ipynb
│
├── src
│   ├── ingest_statsbomb.py
│   ├── build_duckdb.py
│   ├── features.py
│   ├── xT_model.py
│   ├── vaep_model.py
│   ├── player_value.py
│   └── team_style.py
│
├── docs
│   ├── EP01_possession_value.md
│   └── data_dictionary.md
│
├── reports
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

# Key Outputs

The project produces several analytical outputs.

### Player Impact Rankings

Players ranked by:

- value added per 90
- progression value
- creative impact

---

### Tactical Style Analysis

Team profiles including:

- progression patterns
- spatial threat maps
- attacking tendencies

---

### Player Role Profiles

Players represented as vectors of tactical metrics enabling:

- player similarity search
- role classification
- recruitment analysis

---

# Tech Stack

Python ecosystem:

- pandas
- duckdb
- scikit-learn
- LightGBM

Football analytics libraries:

- statsbombpy
- mplsoccer

Visualization:

- matplotlib
- seaborn

---

# Project Goals

This project aims to demonstrate practical skills in:

- football event data modelling
- spatial analytics
- machine learning applied to sports
- reproducible data science pipelines

The framework can be extended for scouting, tactical analysis and recruitment decision support.

---

## License

This project is licensed under the MIT License.

---

# Author

Manuel Pérez Bañuls
Data Science - Football Analytics

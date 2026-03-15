# fair-opportunity-ai

An AI platform that diagnoses opportunity inequality through data
and recommends personalized growth paths based on individual values.

> "It's not that opportunities don't exist. It's that they don't reach everyone equally."

---

## Why I built this

Most job recommendation services output "you're suited for high-income roles."
But the ability to actually reach those roles differs by person —
region, education level, and income all shape how far the same effort gets you.

This project measures that structural gap in data,
and surfaces "the most fair path given your specific circumstances."

---

## Core index structure

Three indices combined to calculate a personal Fair Growth Score (FGS).

| Index | Meaning | Key components |
|-------|---------|----------------|
| **FOI** (Fair Opportunity Index) | Social opportunity accessibility | Employment rate, training access, digital infrastructure |
| **EOI** (Employment Outcome Index) | Job outcome quality | Wages, tenure, growth potential |
| **LOI** (Life Orientation Index) | Personal values & preferences | Work-life balance, growth, stability, autonomy |
| **FGS** (Fair Growth Score) | Combined fair growth potential | FOI × EOI × LOI composite |
```
FGS = 0.25×FOI + 0.35×EOI_personal + 0.25×(FOI×EOI/100) + 0.15×LOI
```

Where existing indices measure whether opportunities exist,
FOI measures whether an individual can actually access them.

---

## Data sources

| Data | Source |
|------|--------|
| Regional employment rate, unemployment, median wage | Statistics Korea (KOSIS) |
| Occupation-level wages, tenure, satisfaction | Korea Employment Information Service |
| Vocational training supply | HRD-Net |
| Youth support policy count | Public Data Portal |
| Digital accessibility | NIA |
| Personal values survey (LOI) | Custom web survey |

---

## What's implemented

- Django web app structure (config / core / templates)
- FOI · EOI · LOI index calculation logic + normalization (0–100 scaling)
- Recommendation algorithm (similarity + gap-correction weighting + policy eligibility filter)
- UI / dashboard (FOI·EOI·LOI radar chart, FGS gauge, recommendation cards)

---

## Simulation example

| Input | Value |
|-------|-------|
| Region | Jeonbuk Jeongeup |
| Education | Associate degree |
| Major | Design → Data analytics transition |
| Preference | Work-life balance type |
| **Result** | FOI=54 / EOI=58 / LOI=82 → **FGS 56** |
| After improvement | Free online course +8 FOI, NCS cert +7 EOI → **FGS 68–70** |

---

## Stack

`Python` `Django` `HTML/CSS`
`pandas` `numpy` `scikit-learn`

---

## Structure
```
fair-opportunity-ai/
├── config/       # Django settings
├── core/         # Index calculation logic (FOI, EOI, LOI, FGS), recommendation engine
├── templates/    # UI templates, dashboard
├── static/       # CSS
└── manage.py
```
```

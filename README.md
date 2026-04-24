## Project Overview

| Field | Details |
|---|---|
| **Project Title** | Urban Traffic Collision & Severity Analysis |
| **Sector** | Public Sector / Transportation Authority |
| **Team Name** | ModelCraft |
| **Faculty Mentor** | `[To be filled by team]` |
| **Institute** | Newton School of Technology, Pune |
| **Submission Date** | 28-04-2026 |

### Team Members

| Role | Name | GitHub Username |
|---|---|---|
| Project / ETL/ Data Lead | Rohan Kumar | [Necro-Rohan](https://github.com/Necro-Rohan) |
| Analysis Lead | Kundan Gupta | [Kundan-CR7](https://github.com/Kundan-CR7) |
| Visualization Lead | Krish Patil | [krishx06](https://github.com/krishx06) |
| Strategy Lead | Yashraj Chouhan | [jadu07](https://github.com/jadu07) |
| PPT and Quality Lead | Rahul Gupta | [Rahulgupta7777](https://github.com/RahulGupta7777) |

---

## Business Problem

Despite existing traffic regulations, road traffic accidents continue to cause significant casualties and infrastructure disruption. Traffic authorities lack a granular understanding of how environmental conditions, driver demographics, and road surfaces interact to escalate minor collisions into severe accidents. This project analyzes these specific interactions to provide actionable insights for city planners and law enforcement.

**Core Business Question**

> How can city traffic departments optimize patrol deployments and targeted public awareness campaigns to proactively reduce the frequency and severity of road traffic accidents?

**Decision Supported**

> This analysis will enable traffic planning departments to strategically allocate highway patrol resources during high-risk times/conditions and design targeted safe-driving initiatives based on specific demographic and environmental triggers.

---

## Dataset

| Attribute | Details |
|---|---|
| **Source Name** | Road Traffic Accident (RTA) Dataset |
| **Direct Access Link** | `[Paste the direct download or access URL]` |
| **Row Count** | 12,316 |
| **Column Count** | 32 |
| **Format** | CSV |

**Key Columns Used**

| Column Name | Description | Role in Analysis |
|---|---|---|
| `Accident_severity` | Categorization of the crash outcome (Slight, Serious, Fatal) | Target Variable / Primary KPI driver |
| `Day_of_week` / `Time` | Temporal indicators of when the crash occurred | Used for temporal patrol scheduling |
| `Light_conditions` | Lighting environment at the time of the crash | Used for environmental risk segmentation |
| `Road_surface_conditions` | State of the road (e.g., Dry, Wet, Snow) | Used for infrastructure/weather segmentation |
| `Age_band_of_driver` | Demographic grouping of the involved driver | Used for designing targeted public awareness campaigns |

For full column definitions, see [`docs/data_dictionary.md`](docs/data_dictionary.md).

---

## KPI Framework

| KPI | Definition | Formula / Computation |
|---|---|---|
| **Accident Severity Ratio** | Percentage of accidents categorized as 'Serious' or 'Fatal' vs 'Slight'. | `(Count of Serious + Fatal) / Total Accidents` |
| **High-Risk Time Frequency** | The volume of severe accidents occurring during specific time blocks or days. | `Count(Accidents) grouped by Time/Day` |
| **Adverse Condition Rate** | Proportion of accidents occurring under non-optimal lighting or weather conditions. | `Count(Accidents where Light != Daylight) / Total` |

Document KPI logic clearly in `notebooks/04_statistical_analysis.ipynb` and `notebooks/05_final_load_prep.ipynb`.

---

## Tableau Dashboard

| Item | Details |
|---|---|
| **Dashboard URL** | `[Paste Tableau Public link here]` |
| **Executive View** | High-level overview of overall accident frequency, severity trends, and top risk factors. |
| **Operational View** | Granular drill-down by time, day, and specific road condition to guide daily patrol deployment. |
| **Main Filters** | Day of Week, Light Conditions, Driver Age Band, Accident Severity. |

Store dashboard screenshots in [`tableau/screenshots/`](tableau/screenshots/) and document the public links in [`tableau/dashboard_links.md`](tableau/dashboard_links.md).

---

## Key Insights

*Insights to be filled post-EDA. List 8-12 major findings from the analysis, written in decision language. Each insight should tell the reader what to think or act upon, not merely describe a chart.*

1. `[Insight 1]`
2. `[Insight 2]`
3. `[Insight 3]`
4. `[Insight 4]`
5. `[Insight 5]`
6. `[Insight 6]`
7. `[Insight 7]`
8. `[Insight 8]`

---

## Recommendations

*Recommendations to be filled post-analysis. Provide 3-5 specific, actionable business recommendations, each linked directly to an insight above.*

| # | Insight | Recommendation | Expected Impact |
|---|---|---|---|
| 1 | `[Which insight does this address?]` | `[What should the stakeholder do?]` | `[What measurable impact do you expect?]` |
| 2 | `[Which insight does this address?]` | `[What should the stakeholder do?]` | `[What measurable impact do you expect?]` |
| 3 | `[Which insight does this address?]` | `[What should the stakeholder do?]` | `[What measurable impact do you expect?]` |

---

## Repository Structure

```text
SectionName_TeamID_ProjectName/
|
|-- README.md
|
|-- data/
|   |-- raw/                         # Original dataset (never edited)
|   `-- processed/                   # Cleaned output from ETL pipeline
|
|-- notebooks/
|   |-- 01_extraction.ipynb
|   |-- 02_cleaning.ipynb
|   |-- 03_eda.ipynb
|   |-- 04_statistical_analysis.ipynb
|   `-- 05_final_load_prep.ipynb
|
|-- scripts/
|   `-- etl_pipeline.py
|
|-- tableau/
|   |-- screenshots/
|   `-- dashboard_links.md
|
|-- reports/
|   |-- README.md
|   |-- project_report_template.md
|   `-- presentation_outline.md
|
|-- docs/
|   `-- data_dictionary.md
```

---

## Analytical Pipeline

The project follows a structured 7-step workflow:

1. **Define** - Sector selected, problem statement scoped, mentor approval obtained.
2. **Extract** - Raw dataset sourced and committed to `data/raw/`; data dictionary drafted.
3. **Clean and Transform** - Cleaning pipeline built in `notebooks/02_cleaning.ipynb` and optionally `scripts/etl_pipeline.py`.
4. **Analyze** - EDA and statistical analysis performed in notebooks `03` and `04`.
5. **Visualize** - Interactive Tableau dashboard built and published on Tableau Public.
6. **Recommend** - 3-5 data-backed business recommendations delivered.
7. **Report** - Final project report and presentation deck completed and exported to PDF in `reports/`.

---

## Tech Stack

| Tool | Status | Purpose |
|---|---|---|
| Python + Jupyter Notebooks | Mandatory | ETL, cleaning, analysis, and KPI computation |
| Google Colab | Supported | Cloud notebook execution environment |
| Tableau Public | Mandatory | Dashboard design, publishing, and sharing |
| GitHub | Mandatory | Version control, collaboration, contribution audit |
| SQL | Optional | Initial data extraction only, if documented |

**Recommended Python libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scipy`, `statsmodels`

---

## Evaluation Rubric

| Area | Marks | Focus |
|---|---|---|
| Problem Framing | 10 | Is the business question clear and well-scoped? |
| Data Quality and ETL | 15 | Is the cleaning pipeline thorough and documented? |
| Analysis Depth | 25 | Are statistical methods applied correctly with insight? |
| Dashboard and Visualization | 20 | Is the Tableau dashboard interactive and decision-relevant? |
| Business Recommendations | 20 | Are insights actionable and well-reasoned? |
| Storytelling and Clarity | 10 | Is the presentation professional and coherent? |
| **Total** | **100** | |

> Marks are awarded for analytical thinking and decision relevance, not chart quantity, visual decoration, or code length.

---

## Submission Checklist

**GitHub Repository**

- [ ] Public repository created with the correct naming convention (`SectionName_TeamID_ProjectName`)
- [ ] All notebooks committed in `.ipynb` format
- [ ] `data/raw/` contains the original, unedited dataset
- [ ] `data/processed/` contains the cleaned pipeline output
- [ ] `tableau/screenshots/` contains dashboard screenshots
- [ ] `tableau/dashboard_links.md` contains the Tableau Public URL
- [ ] `docs/data_dictionary.md` is complete
- [ ] `README.md` explains the project, dataset, and team
- [ ] All members have visible commits and pull requests

**Tableau Dashboard**

- [ ] Published on Tableau Public and accessible via public URL
- [ ] At least one interactive filter included
- [ ] Dashboard directly addresses the business problem

**Project Report**

- [ ] Final report exported as PDF into `reports/`
- [ ] Cover page, executive summary, sector context, problem statement
- [ ] Data description, cleaning methodology, KPI framework
- [ ] EDA with written insights, statistical analysis results
- [ ] Dashboard screenshots and explanation
- [ ] 8-12 key insights in decision language
- [ ] 3-5 actionable recommendations with impact estimates
- [ ] Contribution matrix matches GitHub history

**Presentation Deck**

- [ ] Final presentation exported as PDF into `reports/`
- [ ] Title slide through recommendations, impact, limitations, and next steps

**Individual Assets**

- [ ] DVA-oriented resume updated to include this capstone
- [ ] Portfolio link or project case study added

---

## Contribution Matrix

This table must match evidence in GitHub Insights, PR history, and committed files.

| Team Member | Dataset and Sourcing | ETL and Cleaning | EDA and Analysis | Statistical Analysis | Tableau Dashboard | Report Writing | PPT and Viva |
|---|---|---|---|---|---|---|---|
| Rohan Kumar | Owner / support | Owner / support | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |
| `[Member 2]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |
| `[Member 3]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |
| `[Member 4]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |
| `[Member 5]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |
| `[Member 6]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` | `[Role]` |

_Declaration: We confirm that the above contribution details are accurate and verifiable through GitHub Insights, PR history, and submitted artifacts._

**Team Lead Name:** `[Rohan Kumar]`

**Date:** `[April 2026]`

---

*Newton School of Technology - Data Visualization & Analytics | Capstone 2*
# Ukraine’s Digital Transformation: A European Perspective

An exploratory analysis of **digital government development** and **business ICT adoption** in Ukraine and the European Union, prepared with Excel, Power Query and Tableau.

## Research question

How has Ukraine’s position in digital government changed, and how does business adoption of digital technologies compare with the EU?

The analysis compares distinct dimensions of digitalisation. Cross-country associations are descriptive and do not establish causation.

## Dashboards

### Digital Government
- EGDI trends for Ukraine and EU countries, with the EU-27 median as a benchmark.
- Ukraine versus the EU-27 median for online services, human capital, telecommunications infrastructure and the additional E-Participation Index.
- Ukraine’s position within the distribution of EU-country EGDI scores across survey editions.

Ukraine’s EGDI reached **0.88407** in 2024, slightly above the EU-27 median of **0.8759**.

### Business Digitalisation
- Country-by-indicator heatmap.
- Overlaid bars comparing Ukraine with the official EU-27 aggregate.
- Indicator-selectable time series with a territorial-coverage annotation.
- Country scatterplots comparing EGDI with a selected business indicator in 2022 or 2024.

The business visualisations cover AI, BI, cloud services, data analytics, e-commerce, ERP, internet use for work and websites. Availability differs by indicator and year.

## Data and methodology

| Dataset | Coverage | File |
|---|---|---|
| UN e-government indicators | 193 countries; 12 survey editions, 2003–2024; 2,316 rows | [EGOV_Union_Tableau_Analysis.xlsx](data/EGOV_Union_Tableau_Analysis.xlsx) |
| Business ICT indicators | Countries and EU aggregate; available observations, 2017–2026; 1,869 rows | [Ukraine_Europe_ICT_Tableau_clean.csv](data/Ukraine_Europe_ICT_Tableau_clean.csv) |

The stored ICT dataset is broader than the dashboard selection. CRM, digital intensity and 2026 observations are excluded from the final dashboard scope.

See [Methodology](docs/methodology.md) for definitions, preparation rules and limitations.

## Sources

- [UN DESA — E-Government Knowledgebase](https://publicadministration.un.org/egovkb/en-us/Data-Center)
- [State Statistics Service of Ukraine — ICT usage in enterprises](https://stat.gov.ua/uk/datasets/vykorystannya-informatsiyno-komunikatsiynykh-tekhnolohiy-na-pidpryyemstvakh)
- Eurostat — enterprise ICT and e-commerce statistics; dataset codes are documented in the methodology.

## Interpretation

- EGDI scores range from 0 to 1; ICT values are stored on a 0–100 scale.
- Internet for Work refers to employed persons; the other selected ICT indicators refer to enterprises.
- The EGDI benchmark is the median of EU-27 country scores. The ICT benchmark is the published EU27_2020 aggregate.
- Missing values are not zero. Survey gaps are not filled with invented observations.
- Changes in territorial coverage limit direct comparisons of Ukrainian business statistics across time.

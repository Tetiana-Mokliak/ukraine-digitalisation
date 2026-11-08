# Methodology

## Scope

This exploratory study compares Ukraine’s development in digital government with enterprise ICT adoption in a European context. The dashboards use a fixed EU-27 comparison group plus Ukraine. The stored source tables also retain other countries, indicators and years.

## Sources and indicators

UN DESA E-Government Survey editions: 2003, 2004, 2005, 2008, 2010, 2012, 2014, 2016, 2018, 2020, 2022 and 2024.

| UN measure | Interpretation |
|---|---|
| EGDI | E-Government Development Index |
| OSI | Online Service Index |
| TII | Telecommunication Infrastructure Index |
| HCI | Human Capital Index |
| EPI | E-Participation Index; an additional index, not a fourth EGDI component |
| E-Government Rank | Global rank, also affected by other countries’ results |

Source: https://publicadministration.un.org/egovkb/en-us/Data-Center

Business ICT data combine the State Statistics Service of Ukraine and Eurostat enterprise ICT surveys. The selected enterprise size class is 10 or more employed persons; national totals are used rather than separate size or industry breakdowns.

| Dashboard indicator | Eurostat dataset | Code recorded in preparation notes | Denominator |
|---|---|---|---|
| AI | isoc_eb_ain2 | E_AI_TANY | Enterprises |
| BI | isoc_eb_iip | E_ITBI | Enterprises |
| Cloud | isoc_cicce_usen2 | E_CC | Enterprises |
| DataAnalytics | isoc_eb_das | E_DA | Enterprises |
| Ecommerce | isoc_ec_eseln2 | E_AESELL | Enterprises |
| ERP | isoc_eb_iip | E_ERP1 | Enterprises |
| InternetAccess, displayed as Internet for Work | isoc_ci_cm_pn2 | P_IUSE | Employed persons |
| Website | isoc_ciweb | — | Enterprises |

Ukraine source: https://stat.gov.ua/uk/datasets/vykorystannya-informatsiyno-komunikatsiynykh-tekhnolohiy-na-pidpryyemstvakh

The prepared table does not retain every original Eurostat indicator code. The dataset identifiers above document the source families.

## Data preparation

### E-government

Twelve annual CSV files were combined using Power Query. The resulting table contains 2,316 records: 193 countries for each of 12 survey editions. It retains source filename, survey year, country, global rank, five index values and a two-letter country code.

The original E-Government Index is preserved. In the analytical field `EGDI_analysis`, an original zero is treated as missing only when the global rank is also absent. This rule affects 8 records; 65 other zero values remain unchanged. This is an analytical missing-data rule, not a modification of the source index.

Ukraine control values: EGDI 0.46167 and global rank 54 in 2003; EGDI 0.88407 and global rank 30 in 2024.

### Business ICT

Eurostat and Ukrainian observations were assembled into long format. The observation key is country + year + indicator + series.

The CSV contains 1,869 records for 2017–2026:
- 1,450 EU-member-country records;
- 316 other-European-country records;
- 53 EU-27 aggregate records;
- 50 Ukrainian records.

The key is unique. Twenty missing values remain blank. Numeric values use the 0–100 scale, not 0–1 fractions. Source flags and confidentiality markers are preserved.

Country codes EL and UK were standardised to GR and GB in the working country-code field. Original source geography codes remain available. `is_aggregate` identifies EU27_2020.

The fields `source`, `source_sheet`, `source_geo_code`, `source_indicator_code`, `obs_flag`, `conf_status`, `dataset_note` and `observation_note` retain available provenance and qualifications.

## Dashboard calculations and comparisons

- The e-government benchmark is the median of available EU-27 country values for the selected survey year. It is not the EU business ICT aggregate.
- Business comparisons use the published EU27_2020 aggregate, without replacing it with an unweighted average of countries.
- Overlaid bars show only indicators with values for both Ukraine and the EU-27 in the selected year.
- EGOV and ICT are related in Tableau by country_code and exact year (Survey Year = year). EGOV has one record per country-year; ICT can have several indicator/series records for that pair.
- Scatterplots select one business indicator and one year, 2022 or 2024. Each plotted country requires both EGDI and the selected ICT value. EU aggregates are excluded from country scatterplots.
- Scatter reference lines represent means of the plotted observations. Trend lines illustrate association, not causation.
- Missing survey years are not imputed. Lines connect available observations; markers identify observations.

## Territorial coverage

Ukraine’s statistical territorial coverage changes across the series. The analytical field `ua_territory_break` marks the first available observation after the coverage change when the series also has earlier observations.

The marker is placed in 2022 for DataAnalytics, Ecommerce and InternetAccess, and in 2024 for Website because 2022–2023 website observations are absent. Series without observations before the change do not receive this marker.

The dashboard uses a 2022 vertical annotation to identify the coverage change. A continuous line does not establish full comparability across that boundary. The analytical marker is separate from source-provided observation flags.

## Selection and exclusions

- Archived Ukrainian 2016–2017 candidates are not appended. Their definitions, denominators or units differ or are not established as comparable. A bulletin published in 2017 reports 2016 observations.
- CRM remains in the CSV as distinct series, including Eurostat E_CRM and E_CRM1 and the Ukrainian series. It is excluded from the selected dashboard indicators because compatibility across definitions is unresolved.
- DigitalIntensity remains in the stored data, but the original version codes were not retained during preparation. It is excluded from dashboard comparisons.
- Observations labelled 2026 remain in the stored CSV and are excluded from dashboard scope because their reporting status and reference period are not established here.

## Limitations

Digital government indices and business ICT statistics measure different populations and concepts. A strong EGDI score does not directly measure enterprise technology adoption.

A common 10+ size threshold alone does not establish identical sector coverage, questionnaire definitions, reference periods or survey populations. E-commerce and website statistics describe the covered enterprise population, not all online sellers or the entire digital economy.

Data availability is uneven by country, indicator and year. Missing values must not be interpreted as non-use. Territorial and methodological changes can affect time comparisons.

Changes in UN index methodology also limit interpretation of long-run score movements as a perfectly uniform measure. Global rank is relative to other countries.

The selected country scatterplots are exploratory comparisons with a limited number of observations. They do not identify a causal mechanism.

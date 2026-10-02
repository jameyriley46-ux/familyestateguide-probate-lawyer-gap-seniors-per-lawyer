# The Lawyer Gap for Seniors: Residents 65+ per Employed Lawyer by State and Metro/Nonmetro Area

Seniors (65+) per employed lawyer for 50 states + DC and 521 BLS metro and nonmetro areas, from BLS OEWS May 2025, Census Vintage 2025 population estimates and County Business Patterns 2023.

**Live page:** https://familyestateguide.com/estate-planning-data/probate-lawyer-gap-seniors-per-lawyer/  
**Publisher:** Family Estate Guide (https://familyestateguide.com)  
**Version:** 1.0.0 (2026-10-02)  
**License:** CC BY 4.0 (data). See LICENSE.

> Not legal, tax, financial or medical advice. Figures are estimates with sampling error; legal rules change. Verify anything important with the original source or a qualified professional.

## Files

| File | Rows | Contents |
|---|---|---|
| `data/lawyer_gap_states.csv` | 51 | 51 rows (50 states + DC). |
| `data/lawyer_gap_metro_nonmetro_areas.csv` | 521 | 521 OEWS areas (387 metro + 134 nonmetro; Puerto Rico and territories excluded). 3 areas have no published lawyer count (blank). |
| `data/lawyer_gap_us.csv` | 1 | 1 row, United States (50 states + DC). |

Blank cells mean not available, not published or not applicable; they are never zero.

## Data dictionary

### `data/lawyer_gap_states.csv`

| Column | Description |
|---|---|
| `state` | State name (50 states + District of Columbia; some files add a United States row). |
| `state_fips` | Two-digit state FIPS code. |
| `total_pop_2025` | Resident population, July 1, 2025 (PEP Vintage 2025, summed from counties). |
| `seniors_65plus` | Residents aged 65+, July 1, 2025. |
| `pct_pop_65plus` | seniors_65plus as % of total_pop_2025. |
| `seniors_85plus` | Residents aged 85+, July 1, 2025. |
| `lawyers_employed` | Wage-and-salary lawyer jobs (SOC 23-1011), OEWS May 2025 TOT_EMP. Blank if not published (never zero). |
| `lawyers_emp_rse_pct` | Relative standard error of lawyers_employed, percent. |
| `seniors_per_lawyer` | seniors_65plus / lawyers_employed (main metric; higher = fewer employed lawyers per senior). |
| `lawyers_per_10k_seniors` | lawyers_employed per 10,000 residents 65+. |
| `residents_per_lawyer_all_ages` | total_pop_2025 / lawyers_employed. |
| `rank_seniors_per_lawyer_1_is_fewest_lawyers` | Rank by seniors_per_lawyer, 1 = most seniors per lawyer. |
| `lawyer_median_annual_wage_usd` | Median annual lawyer wage, USD, OEWS May 2025. |
| `law_offices_cbp2023` | Employer establishments in NAICS 541110 Offices of Lawyers, County Business Patterns 2023. |
| `seniors_per_law_office_cbp2023` | seniors_65plus / law_offices_cbp2023 (supplementary). |

### `data/lawyer_gap_metro_nonmetro_areas.csv`

| Column | Description |
|---|---|
| `AREA` | OEWS May 2025 metropolitan or nonmetropolitan area code. |
| `AREA_TITLE` | OEWS area name. |
| `area_kind` | metro or nonmetro. |
| `states` | State abbreviation(s) covered by the area (hyphen-separated). |
| `counties` | Number of counties in the area (BLS May 2025 area definitions). |
| `total_pop_2025` | Resident population, July 1, 2025 (PEP Vintage 2025, summed from counties). |
| `seniors_65plus` | Residents aged 65+, July 1, 2025. |
| `pct_pop_65plus` | seniors_65plus as % of total_pop_2025. |
| `lawyers_employed` | Wage-and-salary lawyer jobs (SOC 23-1011), OEWS May 2025 TOT_EMP. Blank if not published (never zero). |
| `lawyers_emp_rse_pct` | Relative standard error of lawyers_employed, percent. |
| `seniors_per_lawyer` | seniors_65plus / lawyers_employed (main metric; higher = fewer employed lawyers per senior). |
| `lawyers_per_10k_seniors` | lawyers_employed per 10,000 residents 65+. |
| `lawyer_median_annual_wage_usd` | Median annual lawyer wage, USD, OEWS May 2025. |

### `data/lawyer_gap_us.csv`

| Column | Description |
|---|---|
| `area` | Geography label. |
| `seniors_65plus` | Residents aged 65+, July 1, 2025. |
| `lawyers_employed_national_file` | U.S. lawyer jobs from the OEWS national file. |
| `lawyers_employed_sum_of_states` | Sum of the 51 state OEWS lawyer counts (check: equals national file). |
| `seniors_per_lawyer` | seniors_65plus / lawyers_employed (main metric; higher = fewer employed lawyers per senior). |
| `residents_per_lawyer_all_ages` | total_pop_2025 / lawyers_employed. |
| `law_offices_cbp2023_sum` | Sum of state CBP 2023 law-office establishments. |

## Sources

- U.S. Bureau of Labor Statistics, Occupational Employment and Wage Statistics (OEWS), May 2025 estimates (state file oesm25st.zip, national file oesm25nat.zip, metro/nonmetro file oesm25ma.zip, area definitions area_definitions_m2025.xlsx). https://www.bls.gov/oes/tables.htm . Public domain (U.S. government work).
- U.S. Census Bureau, Population Estimates Program, Vintage 2025, county characteristics by age (cc-est2025-agesex-all.csv, July 1, 2025). https://www2.census.gov/programs-surveys/popest/datasets/2020-2025/counties/asrh/ . Public domain.
- U.S. Census Bureau, County Business Patterns 2023, NAICS 541110 Offices of Lawyers, state establishments, via https://api.census.gov/data/2023/cbp . Public domain.

## Methodology

- Lawyers = OEWS SOC 23-1011 TOT_EMP. Seniors = PEP Vintage 2025 county AGE65PLUS_TOT (YEAR = 7, July 1, 2025), summed to states and, via the BLS May 2025 county-to-area crosswalk, to OEWS metro/nonmetro areas.
- The OEWS national total (754,500) equals the sum of the 51 state counts.

## Limitations

- Biggest caveat: OEWS excludes self-employed lawyers and partners, so it undercounts lawyers most where solo practice is common (rural areas, small states). Ratios overstate true scarcity.
- Counts are all employed lawyers, not probate or elder-law specialists; the 'probate lawyer' framing is editorial.
- Lawyers are counted where they work, seniors where they live (commuting mismatch, e.g., DC, The Villages FL).
- Several areas have RSEs above 15-30%; Mississippi vs. Iowa is a statistical tie.
- Different dates: OEWS May 2025, PEP July 1, 2025, CBP 2023.

## Rights review and exclusions

Family Estate Guide publishes here only its own compiled data and U.S. government public-domain data (Census, BLS, CMS, DOL), plus third-party data that is under CC BY or a compatible open license, with attribution. Third-party copyrighted or non-commercial-licensed data is excluded.

- None in the data. American Bar Association lawyer-population counts were considered as a cross-check but not used (not downloaded; not openly licensed).

## How to cite

Family Estate Guide (2026). *The Lawyer Gap for Seniors: Residents 65+ per Employed Lawyer by State and Metro/Nonmetro Area* (Version 1.0.0) [Data set]. https://familyestateguide.com/estate-planning-data/probate-lawyer-gap-seniors-per-lawyer/ . GitHub: https://github.com/jameyriley46-ux/familyestateguide-probate-lawyer-gap-seniors-per-lawyer

A Zenodo DOI will be added here once version 1.0.0 is released and archived. Machine-readable citation: `CITATION.cff`.

Please link to the live page when you use the data.

## License

Data in this repository is licensed under the Creative Commons Attribution 4.0 International license (CC BY 4.0). Underlying U.S. government data is public domain; third-party CC BY data keeps its original attribution requirements (see Sources).

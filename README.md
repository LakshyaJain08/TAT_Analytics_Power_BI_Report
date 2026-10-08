# Turnaround Time (TAT) Analytics

A Power BI proof of concept for monitoring laboratory turnaround time, measuring service-level agreement (SLA) compliance, and exploring operational delays across tests, departments, laboratories, and locations.

## Business context

Turnaround time is the time from test registration to final approval. Laboratories need visibility into whether tests meet their defined SLAs, where performance varies, and which steps in the sample journey may be contributing to delays. This project brings those operational questions into an interactive report for analysis by operations teams and management.

## What the report analyzes

- **Workload and outcomes:** total tests, tests within and outside SLA, rejected tests, outsourced tests, tests on hold, and re-runs.
- **SLA performance:** the share of performed tests completed within their defined SLA.
- **Operational comparisons:** TAT performance by laboratory, department, test type, state, and city.
- **Sample journey and hourly patterns:** sample volumes and elapsed time across registration, SRA receipt, department receipt, result entry, and approval, to help identify peak-load periods and delay-prone stages.
- **Interactive exploration:** date range, laboratory, department, test type, state, and city slicers filter report visuals.

### Key metric

**% In TAT** is calculated as:

`(Tests completed within SLA / Total tests performed) × 100`

An **In TAT** test is completed within its defined SLA; an **Out TAT** test exceeds it. TAT is measured from registration to final approval.

## Data model and approach

The report uses a POC-level star schema with a test-transaction fact table and supporting dimensions for laboratory, department, test, date, and geography. Transaction data provides registration, processing, and completion timestamps; master data provides descriptive attributes such as lab, department, test, city, and state. Relationships use single-direction filtering.

This is descriptive and comparative analytics. Predictive modeling, machine learning, real-time streaming, source-system data correction, and user-level row security are outside the POC scope.

## Open the report

Open [`TAT Analysis.pbix`](TAT%20Analysis.pbix) in Power BI Desktop. The current proof of concept uses manual refresh. The source CSV and Excel extracts are not included in this repository; to refresh the report, use authorized source data and configure the data-source paths and credentials in Power BI Desktop. Production deployment would require a validated refresh process and may require scaling and access-control work.

Do not add customer, operational, or otherwise confidential source data to this repository.

## Repository contents

| File | Description |
| --- | --- |
| [`TAT Analysis.pbix`](TAT%20Analysis.pbix) | Interactive Power BI report |
| [`requirements.txt`](requirements.txt) | Notes that this project has no Python package dependencies |
| [`.gitignore`](.gitignore) | Excludes source extracts and document formats not intended for GitHub |

Power BI Desktop is required to open the report. No Python packages are required.

## Project walkthrough

[Watch the project walkthrough](https://www.youtube.com/watch?v=FedaZXj3mm8).

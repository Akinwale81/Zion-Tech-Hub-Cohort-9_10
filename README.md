<img width="4049" height="81" alt="image" src="https://github.com/user-attachments/assets/1e5aeccf-2d17-4195-b364-7d1c92647383" /># ZION TECH HUB COHORT 9_10 CANDIDATES ANALYSIS
An exploratory data analysis project using Zion Tech Hub applicant data to identify high-performing acquisition channel, audience segments, registration trends, and opportunities for optimising market spending
## PROJECT OVERVIEW
Zion Tech Hub runs applied data-skills training programs and collected candidate applications through an online intake form. This project takes the raw form exports, builds a clean data model, and delivers a two-page Power BI report — OVERVIEW and LEADING TRENDS — that tracks who is applying, where they come from, which programs they choose, and how they hear about the program.
This document is the full analytics write-up behind that dashboard: it walks through the dataset, the preparation which involves cleaning of the dataset using Microsoft Excel, the exploratory analysis performed before any visual was built, the DAX layer that powers every KPI on the report, how the two dashboard pages were designed, and the business insights and recommendations — including a specific ad-budget split and a Cohort 11 growth plan — that the finished dashboard was built to support.

## PROJECT HIGHLIGHT
Consolidated two raw Excel exports into a working Power BI data model using Power Query (null-handling, column renaming, type casting).
Built 24 custom DAX measures and 4 calculated columns spanning KPI counts, percentages, and date intelligence (month, quarter, weekday) across the three tables.
Designed a 2-page interactive report (OVERVIEW + LEADING TRENDS) with 8 KPI cards, 3 slicers per page, and 6 chart visuals surfacing demographic, geographic, and channel patterns and 2 tables.
The Male gender accounted for the most gender representation of 73.8% against the other two (Female gender and the Undisclosed).
Converted the diagnosis into a specific, percentage-based first ad-budget split across 5 channels/audiences, plus a concrete action plan for growing Cohort 11.

## OBJECTIVES
Most importantly, growing Zion Tech Hub community, and filling Cohort 11
Consolidate two near-duplicate raw candidate exports into a clean, query-ready model by using the append query on power query
Build reusable DAX measures and calculated columns to power gender-split, geographic-reach, program-demand, and peak-period KPIs without hard-coding values.
Design a two-page Power BI report that lets Zion Tech Hub filter and read candidate volume, geography, gender, program choice, and source at a glance.
Move past descriptive reporting into prescriptive analysis — identify which acquisition channels are converting, fading, or underused — and translate that into an actionable plans for Cohort 11 growth plan.

## DATASET
The report is built on two Excel workbooks loaded via Power Query — Zion Hub Challenge Append.xlsx and Zion Hub Challenge Append 2.xlsx — landing as two near-identical candidate tables (Cleaned Append and Cleaned Append (2)), each holding 1,308 rows. 



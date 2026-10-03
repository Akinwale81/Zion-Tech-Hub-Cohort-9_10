# ZION TECH HUB COHORT 9_10 CANDIDATES ANALYSIS
An exploratory data analysis project using Zion Tech Hub applicant data to identify high-performing acquisition channel, audience segments, registration trends, and opportunities for optimising market spending
## PROJECT OVERVIEW
Zion Tech Hub is a data and technology training community that runs cohort-based programmes in data analytics and AI. This project analyses the registration data for Cohort 9 and 10 (November 2025 to June 2026): 1,231 applicants from 43 countries across six programmes.

Using Power BI, Power Query and DAX, I built a three-page interactive dashboard covering registration volume, geography and programme choice, and acquisition channels. The analysis shows that registration is driven by campaign bursts rather than steady growth, that Nigeria supplies nearly 59% of applicants, and that X (Twitter) now brings in almost nine in ten registrations while WhatsApp, LinkedIn and referrals have faded.

The project ends with practical recommendations for the next cohort: diversify channels, build a trackable referral system, expand into the most responsive countries, and improve the registration form so future analysis can follow applicants through to completion.

The final output is an interactive Power BI dashboard with three pages:
|Page                              |Question it answers                                             |                                                                                  
|----------------------------------|----------------------------------------------------------------|
|Registration Volume               |When do people apply, and who are they?                         |
|Geography and Programme Choice    |Where are they from, and what do they want to learn?            |
|Acquisition Channels              |How did they find us, and what should we do about it?           |

### TOOLS USED: Microsoft Excel, Power Pivot, Power BI Desktop, Power Query, DAX.

## PROJECT HIGHLIGHT
- 1,231 applicants from 43 countries, across 6 programme choices.
- Nigeria supplies 58.7% of applicants, and the top four countries (Nigeria, South Africa, Kenya, Ghana) supply 84.6%.
- X (Twitter) brought in 65% of applicants. WhatsApp and LinkedIn, which were strong in November, nearly disappeared by May.
- Women are 26% of applicants, but they are 39% of the Healthcare Data Analytics applicants and only 19% of Data Science and   AI/ML applicants.
- Referrals stayed flat at about 2% of registrations in every month. T
- The Occupation question was added only in May 2026, so 87.6% of applicants have no occupation recorded. The audience cannot yet be profiled by profession.

## OBJECTIVES
- Measure the size and timing of applicant registrations across the cohort window.
- Profile applicants by gender, country, and programme choice.
- Identify which acquisition channels perform, which are declining, and which have never worked.
- Understand whether different channels reach different kinds of people (by occupation).
- Turn the findings into practical recommendations for growing the community and running the next cohort's registration.

## DATASET
One registration table (ZionTechHub, 1,231 rows × 9 source columns) plus a small hand-written Insights table that powers the findings panel.
|FIELD                             |TYPE                             |NOTE                                                 |                                               
|----------------------------------|---------------------------------|------------------------------------------------------|
|Date                              |Date                             |Application timestamp; range Nov 6, 2025 – Jun 4, 2026|
|Name / Email / Phone              |Text                             |Retained in the model for operational use; excluded   |
|                                  |                                 |from this report and used only in aggregate           |
|Country                           |Text                             |46 distinct values; renamed from "Country (e.g.       |
|                                  |                                 |Nigeria, UK)" in one source table                     |
|Gender                            |Text                             |Male / Female / Prefer not to say                     |
|Choice of programme               |Text                             |6 distinct programs across both cohorts, including 2  |
|                                  |                                 |pilot tracks introduced in Cohort 10                  |
|How Heard                         |Text                             |Renamed from "How did you hear about our Program?"; 7| 
|                                  |                                 |channels                                              |
|Occupation                        |Text                             |collected from May 2026 only                          |

## DATA PREPARATION
### Before performing the analysis , the dataset was prepared to ensure that the data was suitable for analysis and visualisation.  The preparation was done using Microsoft Excel and Power Query. The process include: 
- Checked for duplicate records. 10 duplicate records were found and were removed.
- Reviewed the structure of the dataset.
- Checked and corrected the datatype for Timestamp into short date data type 
- Created a new column and split the date and time from Timestamp column, renamed the column to Date and deleted the column    accommodating Time.
- Standardised the Name, Country and Choice of Program column using the Trim and Proper functions.
- Created new columns: Year Month, Year Month Sort, Weekday, Weekday number.
- Deleted the Amount Paid column because it was an empty field and had no record.
- Prepare fields required for analysis and visualization.
### The purpose of this stage was to ensure that the dataset was clean, consistent and suitable for analysis.

## EXPLORATORY DATA ANALYSIS (EDA)
### After preparing the dataset, Exploratory Data Analysis was performed to understand the characteristics and patterns with the data before developing the final dashboard. The EDA focus on:
### Volume & Timing: 
Applications arrived in two distinct waves rather than a continuous stream: 87% of all candidates (1,133 of 1,308) landed in the Nov 2025–Jan 2026 wave, peaking at 525 in January 2026, before collapsing to near-zero in February and re-emerging as a smaller 167-candidate wave in May 2026. Sign-ups also cluster by weekday — Thursday and Friday together account for 54% of all applications.
### Geography:
Candidates were drawn from 46 countries, but the base is heavily African and Nigeria-anchored: 93.5% of candidates are from Africa, and Nigeria alone supplies 58.2% (761 candidates), with South Africa, Ghana and Kenya each contributing roughly 9%.
### Gender Composition:
Overall the pipeline is 73.8% male, 25.5% female, 0.8% preferring not to say. The gap is not uniform: Healthcare Data Analytics is the most balanced program (38.0% female) while Data Science and AI — the highest-volume program — is the most male-skewed (82.4% male).
### Programme Demand:
Data Science and AI drew 518 candidates in Cohort 9 alone; combined with its Cohort 10 rebrand ("Data Science and ML", 72 candidates), AI/data-science tracks account for 45% of all applicants. Healthcare Data Analytics (305) and Financial Analytics (210) form a clear second tier.
### Acquisition Channels:
X (Twitter) sourced 859 candidates overall, and its share of volume actually grew between cohorts. WhatsApp, by contrast, delivered 209 candidates— a channel that disappeared rather than one that gradually faded. LinkedIn acquired a total of 183 candidates to finish 3rd     in the order of acquisition channel
### Occupation (Cohort 10 only):
Occupation was captured for the first time in Cohort 10 (100% disclosure, 167 of 167), as it was not collected for cohort 9. Within it, 60% describe themselves under a broad "other professional" bucket, 18% are students, and only 6.6% are working Data/IT professionals — a small share for a program selling data-career skills.

## DAX MEASURES AND CALCULATED COLUMNS
Twenty-four DAX measures were built across the Cleaned Append, Cleaned Append (2), and a dedicated Measure table, covering headline counts, gender splits and percentages, geographic reach, and program/channel/peak-period flags used directly by the KPI cards on both report pages.
|Table                             |Measures                         |DAX Expresssion                                      |                                               
|----------------------------------|---------------------------------|------------------------------------------------------|
|Measure                           |Total Candidates                 |COUNTROWS('Cleaned Append')                           |
|Measure                           |Total Male                       |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Gender]="Male")                               |
|Measure                           |Total Female                     |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Gender]="Female")                             |
|Measure                           |Male %                           |DIVIDE([Total Male],[Total Candidates],0)             |
|Measure                           |Female %                         |DIVIDE([Total Female],[Total Candidates],0)           |
|Measure                           |Total Country                    |DISTINCTCOUNT('Cleaned Append'[Country])              |
|Measure                           |Prefer not to say                |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Gender]="Prefer not to say")                  |
|Cleaned Append (2)                |Data Science and ML Count        |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Choice of Program]="Data Science and ML")     |
|Cleaned Append (2)                |Top programme %                  |DIVIDE([Data Science and AI Count]+[Data Science and  |
|                                  |                                 |ML Count],'Cleaned Append (2)'[Total Candidate],0)    |
|Measure                           |Data science and AI count        |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Choice of Program]="Data Science and AI")     |
|Measure                           |Nigeria candidate count          |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Country]="Nigeria")                           |
|Measure                           |Peak month_year                  |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Year Month]="Jan 2026")                       |
|Cleaned Append                    |Top programme                    |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Choice of Program]="Data Science and AI")     |
|Cleaned Append                    |Top channel X(Twitter)           |CALCULATE(COUNTROWS('Cleaned Append'),'Cleaned        |
|                                  |                                 |Append'[Source]="X (TWITTER)")                        |
|Cleaned Append                    |Top Channel X(Twitter) %         |DIVIDE([TOP CHANNEL X],[Total Candidate],0)           |
|Measure                           |Top programme %                  |DIVIDE([Dat Science and AI Count],[Total Candidate],0)|
|Measure                           |Peak month_year                  |DIVIDE([Peak Month_Year],[Total Candidate],0)         |

### CALCULATED COLUMN
Four different columns were created to enhance further analysis: Year_month, Year_month sort, Week day and Week day number for sorting.
|Column                            |DAX Expression                  |Purpose                                                |                                               
|----------------------------------|---------------------------------|------------------------------------------------------|
|Year_month                        |FORMAT([Date]),"mmm yyyy")       |Human readable month label for axis/slicer display    |
|Year_month sort                   |EOMONTH([Date]),0)               |Hidden sort key so "Year_month" sort chronologically, |
|                                  |                                 |not alphabetically                                    |
|Week day                          |FORMAT([Date]),"dddd")           |Day_of_week label use in the week day sign-up analysis|
|Weekday number                    |Weekday([Date]),2)               |Number sort key (MONDAY=1,Sunday=7) behind the weekday|
|                                  |                                 |column                                                |

## DASHBOARD DEVELOPMENT
### The report ships as two pages sharing a single theme and a consistent KPI-card-plus-slicer layout, so a viewer can orient on either page the same way.
- OVERVIEW page
Leads with 4 KPI cards — Total Candidates, Top Gender (Male), Total Countries, and Most Candidates (Nigeria) — followed by three chart visuals: a line chart of candidates by month, a clustered column chart of the top 5 countries, and a pie chart of gender split. A table which identify 5 occupations by applicant count. Three slicers (visible as a filter panel) let the viewer cut every visual by date, program, and other dimensions.
- LEADING TRENDS page
Mirrors the same KPI-card-plus-slicer structure with 4 cards — Total Candidates, Peak Month/Year (Jan 2026), Top Programme (Data Science and AI), and Top Source (X) — plus a clustered bar chart of candidates by program, a clustered column chart of candidates by country, and a supporting data table. This page is oriented toward "what's driving the numbers" rather than the OVERVIEW page's "what are the numbers".

## KEY INSIGHTS
- Demand is bursty, not steady — 87% of applications landed in a single Nov 2025–Jan 2026 wave, peaking at 525 in January 2026.
- Data Science & AI/ML dominates demand, drawing 45.1% of all applicants across both cohorts combined.
- Acquisition is heavily concentrated: X (Twitter) sourced 65.7% of all candidates, and its share grew further between cohorts (63% → 88%).
- WhatsApp silently disappeared — 18.4% of Cohort 9 volume fell to 0% in Cohort 10, the single biggest funnel change in the dataset.
- LinkedIn is smaller but higher-value — it disproportionately brings working professionals into the career-switcher programs (Financial & Healthcare Analytics), even as its overall share declined.
- Reach is pan-African and Nigeria-anchored (93.5% African, 58% Nigerian), while gender skews male overall (74%) and most sharply within the flagship Data Science & AI/ML track (82% male).
- Occupation data only exists for Cohort 10, where students are surprisingly high slice (19.1%) of applicants to a data-careers program, indicating high percentage of students willinglingness to transition into Data tech space.

## RECOMMENDATIONS
### Ad budget split (first budget)
Treat the first ad budget as 100 units, allocated across five lines rather than spread evenly, because X and LinkedIn already show proven
|Channel                         |Line                        |Focus                                                      |                                               
|--------------------------------|----------------------------|-----------------------------------------------------------|
|X(Twitter)                      |50%                         |Broad awareness + retargeting; amplify the proven, growing |
|                                |                            |channel                                                    |
|LinkedIn                        |25%                         |Narrow targeting of working professionals for              |
|                                |                            |Financial/Healthcare Analytics and Data Science & ML       |
|Whatsapp Revival                |15%                         |Re-engage the lapsed Cohort-9 audience; relaunch WhatsApp  |
|                                |                            |Community                                                  |
|Referral incentive fund         |7%                          |Small reward for existing candidates/alumni who refer      |
|Facebook/Instagram (test)       |3%                          |Small experimental spend targeting women for Data Science &|
|                                |                            |AI/ML                                                      |

## Growing the community & filling Cohort 11
- Fix the WhatsApp leak first — confirm whether the original group/broadcast list still exists and reboot a Thursday-cadence broadcast, its historical peak day.
- Launch a simple referral loop this week — a personal referral link plus a small incentive, pushed alongside the Thursday content drop.
- Make Occupation (and "how did you hear about us") required fields on the Cohort 11 form. 
- Run a short LinkedIn campaign targeting working data/IT professionals specifically, the most underrepresented segment in the cohort with clean occupation data.
- Plan a extensive content run-up before the Cohort 11 launch, mirroring the build-up that preceded the January 2026 peak, rather than a single announcement.
- Pair a women-in-tech push with the LinkedIn campaign to address the gender gap in Data Science & AI/ML, using Healthcare Data Analytics as a model.







































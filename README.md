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
- Referrals stayed flat at about 2% of registrations in every month. 
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
- Checked for duplicate records. 87 duplicate records were found and were removed.
- Reviewed the structure of the dataset.
- Checked and corrected the datatype for Timestamp into short date data type 
- Created a new column and split the date and time from Timestamp column, renamed the column to Date and deleted the column    accommodating Time.
- Standardised the Name, Country and Choice of Program column using the Trim and Proper functions.
- Handled the Occupation gap. The field was only added in May 2026, so earlier rows were blanked.These were converted to
  null so they no longer count as a real occupation or distort the occupation chart (87.6% of rows were affected).
- Created time helper columns (Weekday, Weekday Number, Month_Year, Month_Year Sort) so charts sort chronologically rather
  than alphabetically.
- Deleted the Amount Paid column because it was an empty field and had no record.
- Built a separate Measures table to keep every DAX measure in one place.
- Built an Insights table with three fields (Key Insight, Value, Recommendation) to present the headline findings inside the
  dashboard.
- Prepare fields required for analysis and visualization.
### The purpose of this stage was to ensure that the dataset was clean, consistent and suitable for analysis.

## EXPLORATORY DATA ANALYSIS (EDA)
### After preparing the dataset, Exploratory Data Analysis was performed to understand the characteristics and patterns with     the data before developing the final dashboard. The EDA focus on:
### Timing and Volume of Applications
|Month_Year                        |Applicants                       |
|----------------------------------|---------------------------------|
|Nov 2025                          |408                              |
|Dec 2025                          |172                              |
|Jan 2026                          |493                              |
|Feb 2026                          |4                                |
|May 2026                          |150                              |
|June 2026                         |4                                |

- January is the peak month (40% of all applicants), and 22 Jan (249) and 23 Jan (187) alone account for 35%.
- Thursday (32%) and Friday (21%) lead the weekday view, but this is largely driven by the January spike, not by a weekly habit. In November, Monday and Wednesday led

### Who Applied
- Gender: 72.9% male, 26.2% female, 0.8% undisclosed.
- Programme: Data Science and AI/ML 45.2%, Healthcare Data Analytics 23.3%, Financial Analytics 16.5%, Sales and Marketing Analytics 13.8%, Supply Chain Analytics 0.8%, AI Automation 0.3%.
- Female share by programme: Healthcare Data Analytics 39%, Sales and Marketing 28%, Financial Analytics 26%, Data Science and AI/ML 19%.

### Where They Are
- Nigeria 58.7%, South Africa 9.7%, Kenya 8.2%, Ghana 8.0%, Uganda 2.8%.
- Nigeria's share moved from 77% in November to 41% in January and 61% in May, so the January push reached a much wider
  African audience.

### How They Heard
|Month_Year       |X (Twitter)     |Whatsapp        |LinkedIn       |Referral        |
|-----------------|----------------|----------------|---------------|----------------|
|Nov 2025         |140             |168             |85             |9               |
|Dec 2025         |103             |9               |50             |7               |
|Jan 2026         |428             |23              |24             |8               |
|Feb 2026         |0               |0               |4              |0               |
|May 2026         |131             |0               |9              |3               |
|June 2026        |1               |0               |3             |0                |

### Occupation (May to June 2026 only, 153 applicants)
- Students (32), Unemployed (12), Entrepreneurs (9) lead. Working professionals such as IT, Data Analyst, Banker, and Finance Analyst appear in small numbers
  
## DAX MEASURES AND CALCULATED COLUMNS
Twenty-two DAX measures were built and a dedicated Measure table, covering headline counts, gender splits and percentages, geographic reach, and program/channel/peak-period flags used directly by the KPI cards on both report pages.

|Measures                         |DAX Expresssion                                                                         |
|---------------------------------|----------------------------------------------------------------------------------------|
|Total Applicants                 |COUNTROWS(ZionTechHub)                                                                  |
|Male Applicants                  |CALCULATE(COUNTROWS(ZionTechHub), ZionTechHub[Gender] = "Male")                         |
|Female Applicants                |CALCULATE(COUNTROWS(ZionTechHub), ZionTechHub[Gender] = "Female")                       |
|Undisclosed                      |CALCULATE(COUNTROWS(ZionTechHub), ZionTechHub[Gender] = "Undisclosed")                  |
|Male %                           |DIVIDE([Male Applicants], [Total Applicants], 0)                                        |
|Female %                         |DIVIDE([Female Applicants], [Total Applicants], 0)                                      |
|Undisclosed %                    |DIVIDE([Undisclosed], [Total Applicants], 0)                                            |
|Total Countries                  |DISTINCTCOUNT(ZionTechHub[Country])                                                     |
|Total Occupations                |DISTINCTCOUNTNOBLANK(ZionTechHub[Occupation])                                           |
|Peak Day Name                    |MAXX(TOPN(1, VALUES(ZionTechHub[Weekday]), [Total Applicants]), ZionTechHub[Weekday])   |
|Peak Month_Year                  |MAXX(TOPN(1,VALUES(ZionTechHub[Month_Year]),[Total Applicants]),ZionTechHub[Month_Year])|
|Top Gender Name                  |MAXX(TOPN(1, VALUES(ZionTechHub[Gender]), [Total Applicants]), ZionTechHub[Gender])     |
|Top Programme Name               |MAXX(TOPN(1, VALUES(ZionTechHub[Choice of Program]),[Total Applicants]),                |
|                                 |ZionTechHub[Choice of Programm])                                                        |
|Top Country Name                 |MAXX(TOPN(1, VALUES(ZionTechHub[Country]), [Total Applicants]), ZionTechHub[Country])   |
|Top Channel Name                 |MAXX(TOPN(1, VALUES(ZionTechHub[How Heard]),[Total Applicants]), ZionTechHub[How Heard])|
|Peak Day %                       |DIVIDE(MAXX(ADDCOLUMNS(VALUES(ZionTechHub[Weekday]), "@n", [Total Applicants]), [@n]),[Total Applicants], 0)|                                                                  
|Peak Month_Year %                |DIVIDE(MAXX(ADDCOLUMNS(VALUES(ZionTechHub[Month_Year]), "@n", [Total Applicants]),[@n]),[Total Applicants], 0)|
|Top Country %                    |DIVIDE(MAXX(ADDCOLUMNS(VALUES(ZionTechHub[Country]), "@n", [Total Applicants]), [@n]),    [Total Applicants], 0)|
|Top Programme %                  |DIVIDE(MAXX(ADDCOLUMNS(VALUES(ZionTechHub[Choice of Program]),"@n", [Total Applicants]), [@n]),[Total Applicants], 0)|
|Top Channel %                    |DIVIDE(MAXX(ADDCOLUMNS(VALUES(ZionTechHub[How Heard]), "@n", [Total Applicants]), [@n]), [Total Applicants], 0)|
|Applicants(Known Occupation)     |CALCULATE([Total Applicants], KEEPFILTERS(NOT ISBLANK(ZionTechHub[Occupation])))        |
|Day on Day %                     |VAR Prev= CALCULATE([Total Applicants],OFFSET(-1,ALL(ZionTechHub[Weekday Number],       | |                                 |ZionTechHub[Weekday]),ORDERBY(ZionTechHub[Weekday Number])))                            |
|                                 |RETURN DIVIDE([Total Applicants] - Prev, Prev)                                          |

### N.B:
- DISTINCTCOUNTNOBLANK is used so applicants with no recorded occupation are not counted as an occupation.
- @n is just a temporary column name used inside the variable table
- KEEPFILTERS makes the "known occupation" condition work alongside the chart's own category filter instead of overriding
  it. Without it, every bar showed the same value (153)
- Day on Day % compares each weekday with the weekday before it (for example, Tuesday against Monday), used in the weekday
  breakdown table. Monday is blank because it has no previous day.
  
### CALCULATED COLUMN
Four different columns were created to enhance further analysis: Weekday, Month_Year, Week day number and Month_Year Sort.

|Column Name                      |DAX Expresssion                                                                         |
|---------------------------------|----------------------------------------------------------------------------------------|
|Weekday                          |FORMAT(ZionTechHub[Date], "DDDD")                                                       |
|Month_Year                       |FORMAT(ZionTechHub[Date], "mmm yyyy")                                                   |
|Weekday Number                   |WEEKDAY(ZionTechHub[Date], 2)                                                           |
|Month_Year Sort                  |EOMONTH(ZionTechHub[Date], 0)                                                           |

### N.B: Weekday Number and Month_Year Sort are used as "Sort by column" fields so Monday-to-Sunday and Nov-to-Jun display in the right order.

## DASHBOARD DEVELOPMENT
### The report uses a 1280 × 720 canvas with a consistent template on every page: a bold navy title block ("ZION TECH HUB, COHORT 9_10 APPLICANTS"), a row of slicers across the top, a row of colour-coded KPI cards, and a grid of charts underneath. 

### Page 1: Registration Volume
**Slicers**: Gender, Country, Month_Year
|Visual                                                            |Purpose                                                | 
|------------------------------------------------------------------|-------------------------------------------------------|
|**KPI cards**: Total Applicants, Male %, Peak Month %, Peak Day % |The headline numbers at a glance                       |
|**Line chart**: Applicants by Month                               |Shows the November burst, the December dip, the January peak, and the gap in March and April|
|**Column chart**: Applicants by Weekday                           |Shows which days drive registrations                   |
|**Donut chart**: Applicants by Gender                             |Shows the gender balance                               |
|**Table**: Weekday Breakdown by Gender                            |Compares gender mix and weekday-to-weekday change      |

### Page 2: Geography and Programme Choice
**Slicers**: Gender, Country, Choice of Program
|Visual                                                            |Purpose                                                |
|------------------------------------------------------------------|-------------------------------------------------------|
|**KPI cards**: Total Applicants, Total Countries, Top Country %,  |Reach and concentration                                |
Top Programme %                                                                                                            |
|**Filled map**: Countries by Applicants                           |Where applicants are located (darker means more)       |
|**Line chart**: Applicants by Month and Choice of Programme       |How programme demand shifts over time                  |
|**Table**: Applicants by Choice of Programme                      |Gender split inside each programme                     |

### Page 3: Acquisition Channels
**Slicers**: How Heard, Country, Occupation
|Visual                                                                |Purpose                                             |
|----------------------------------------------------------------------|----------------------------------------------------|
|**KPI cards**: Total Applicants, Top Channel %, Occupation Counts     |Channel dependence and data coverage                |
|**Line chart**: Applicants by Month and Channel                       |Rise of X and decline of WhatsApp and LinkedIn      |
|**Bar chart**: Applicants by Occupation(Top 5, known occupations only)|Who the applicants are professionally               |
|**Insights table**: Key Insight, Value, Recommendation                |Decision-ready findings inside the report           |

### Screenshots
[Registration Volume](....)
[Geography and Programme Choice](....)
[Acquisition Channels](....)

## KEY INSIGHTS
- Registration is driven by moments, not by momentum. Applications came in bursts: 408 in November, 493 in January, and
  almost nothing in February, 150 in May. Two days, 22 and 23 January, produced 436 applicants (35% of the total). That is
  why Thursday and Friday look like the "best days"; it is a campaign effect, not a weekly pattern.

- Nigeria is the core, but the January push proved the hub can reach further. Nigeria supplies 58.7% of applicants and the
  top four countries supply 84.6%. Yet Nigeria's share fell from 77% in November to 41% in January, when South Africa (17%)
  and Kenya (14%) surged. When the hub promotes widely, other markets respond.

- Data Science and AI/ML is the flagship, but women are drawn elsewhere. 45% of applicants chose Data Science and AI/ML,
  with Healthcare Data Analytics second at 23%. Women are 26% of all applicants, but 39% of Healthcare Data Analytics
  applicants versus 19% of Data Science and AI/ML applicants. Supply Chain Analytics (0.8%) and AI Automation (0.3%) barely
  register.

- X (Twitter) is carrying the hub, and other channels have faded. X's share of applicants grew from 34% in November to 87%
  in January and May. The reason is as much decline elsewhere as growth on X: WhatsApp fell from 168 applicants in November
  to 9 in December and none in May, and LinkedIn fell from 85 to 9 over the same period. One platform now accounts for
  almost every registration, which is a concentration risk.

- Referrals are not working. Referrals sit at about 2% in every month. Current applicants are not bringing others in.

- Different channels appear to reach different people. Among the 19 applicants with a professional occupation (IT, Data
  Analyst, Banker, Finance Analyst, Accountant), 26% came from LinkedIn against 8% of all applicants with a recorded
  occupation. This is an early signal only, based on a small sample.

- The hub does not yet know its audience's profession. Occupation was only collected from May 2026, so 87.6% of applicants
  have no occupation. Among those who answered, students (21%), unemployed applicants (8%), and entrepreneurs (6%) lead.

## RECOMMENDATIONS
- Plan registration as a campaign calendar, not a single launch. Schedule a teaser phase, a launch burst, and two reminder
  bursts. The January spike shows the response is there when the hub pushes hard.
- Keep X as the main channel, but stop depending on it alone. Build at least two other channels to a meaningful share
  (target 15 to 20% each) by the next cohort.
- Investigate why WhatsApp and LinkedIn fell. Check whether groups were closed, posts stopped, or messaging changed. Restart
  them with a clear plan rather than hoping they recover.
- Launch a referral incentive. For example, a small reward or priority access for every verified referral, with a unique
  referral link or code so it can be tracked.
- Test paid promotion in South Africa, Kenya, and Ghana first. They already respond and they are the next three largest
  markets. Treat other countries as low-cost experiments.
- Make LinkedIn content profession-specific. Target bankers, accountants, finance and IT professionals with the Financial
  Analytics and Data Science tracks.
- Tell women's stories in the Data Science and AI/ML track. Healthcare Data Analytics already attracts women; use alumni
  stories and women-focused sessions to widen participation in the flagship programme.
- Decide the fate of the smallest programmes. Either promote Supply Chain Analytics and AI Automation properly, or fold them
  into a broader track.
- Keep Occupation mandatory in the form, and add more fields
  
## WHAT SHOULD BE DONE TO GROW THE COMMUNITY AND FILLING FOR THE NEXT COHORT
### Growing the community
- Turn applicants into members before the cohort starts. Add everyone who applies to a WhatsApp or Telegram community
  straight away, with a welcome message and a first useful resource. Right now, 1,231 people showed interest, but the
  dashboard cannot say how many stayed engaged.
- Build a referral and ambassador system. Recognise alumni and active members who bring in others. Give them badges,
  certificates, early access to sessions, or a spotlight on the hub's X and LinkedIn pages.
- Publish consistently, not just at launch. Share weekly tips, student projects, and alumni outcomes. The data shows
  registrations collapse when promotion stops, so visibility between cohorts matters.
- Use alumni as proof. Short stories from graduates, especially women in data science and professionals from banking,
  finance, and healthcare, will convert better than generic posts.
- Go regional on purpose. Run focused campaigns for South Africa, Kenya, Ghana, and Uganda, with local-time live sessions,
  local examples, and local community leads.
- Partner with universities and professional groups. Students are the largest known occupation group, and professionals are
  the group LinkedIn reaches best. Campus clubs and professional associations can supply both.
- Reactivate dormant channels. Rebuild WhatsApp groups and LinkedIn presence with a clear owner and posting plan.


## Author

**MAKU AKINWALERE JAMES** 

LinkedIn: www.linkedin.com/in/james-maku

Email: makuakinwalere81@gmail.com







































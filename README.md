# Data-Analysis-projects
**HR DATA ANALYTICS**

**Overview:**

This Power BI dashboard provides a detailed analysis of employee attendance by leveraging an Excel dataset. The dataset was first cleaned and structured into a required format, followed by the creation of necessary DAX measures for calculating key attendance metrics.

**Key Metrics**

The dashboard captures and visualizes the following employee attendance insights:

Presence % - Percentage of employees present on a given day.

Work from Home (WFH) % - Percentage of employees working remotely.

Sick Leave (SL) % - Percentage of employees on sick leave.

**Data Processing & Visualization**

**Data Cleaning & Preparation:**
The raw dataset was formatted to ensure consistency and accuracy. Unnecessary columns were removed, missing values handled, and date formats standardized.

**DAX Formulas & Measures:**
Created custom measures using DAX (Data Analysis Expressions) to calculate the percentage of presence, WFH, and sick leaves. Aggregated data based on employee attendance records to generate insights.

**DAX Formulas Used**

1️⃣Present Days Calculation

Present Days = VAR Presentdays = CALCULATE(COUNT('Final Data'[Value]), 'Final Data'[Value] = "P")

RETURN Presentdays + [WFH Count]

This formula counts the total number of Present (P) days from the dataset. It also adds Work from Home (WFH) days to get the total number of working days, considering both in-office and remote attendance.

2️⃣ Presence Percentage (%)

Presence % = DIVIDE([Present Days], 'Measure Table'[Total Working Days], 0)

This metric calculates the percentage of days an employee was present compared to the total working days. The DIVIDE function ensures safe division, avoiding errors if Total Working Days = 0.

3️⃣ Total Working Days Calculation

Total Working Days =

VAR totaldays = COUNT('Final Data'[Value])

VAR nonworkdays = CALCULATE(COUNT('Final Data'[Value]), 'Final Data'[Value] IN {"WO", "HO"})

RETURN totaldays - nonworkdays

This formula counts the total days recorded in the dataset. It then excludes weekends (WO) and holidays (HO) to derive the actual total working days.

4️⃣ Sick Leave (SL) Count and Percentage (%)

SL Count = SUM('Final Data'[SL Count])

This formula sums up all instances of sick leaves (SL Count) recorded in the dataset.

SL % = DIVIDE([SL Count], [Total Working Days], 0)

This calculates the percentage of sick leaves relative to the total working days.

5️⃣ Work from Home (WFH) Count and Percentage (%)

WFH Count = SUM('Final Data'[WFH Count])

This sums up all instances of Work from Home (WFH Count) in the dataset.

WFH % = DIVIDE([WFH Count], [Present Days], 0)

This calculates the percentage of Work from Home days relative to Present Days.

**Dashboard Elements:**
Employee Table: Displays individual attendance percentages (Presence, WFH, SL).

Trends Over Time: Line charts visualizing the trends of attendance, remote work, and sick leave percentages over time.

Day-of-Week Insights: Breakdown of attendance trends based on weekdays.

Matrix View: Displays employees' attendance status across different dates, indicating whether they were present in the office, working remotely, or on sick leave.

**Key Findings**

The dashboard enables HR teams and management to track attendance trends, analyze remote work patterns, and identify days with high absenteeism.

Presence, WFH, and SL trends help in workforce planning and decision-making.

--Tools & Technologies Used--

--> Power BI for data visualization

-->Excel for data preprocessing

-->DAX for measure calculations

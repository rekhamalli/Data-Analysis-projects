
**REVENUE INSIGHTS IN HOSPITALITY DOMAIN**

**Overview**

This Power BI dashboard provides a comprehensive analysis of revenue trends in the hospitality sector. It enables stakeholders to monitor key performance metrics, compare revenue across time periods, and make data-driven decisions. The dashboard integrates multiple datasets, applies DAX formulas, and visualizes insights using Power BI’s interactive features.

**Step-by-Step Project Process**


**1. Data Collection & Import**


Imported datasets containing hotel revenue, room availability, and booking details as a folder.

Tables include:

dim_date (Calendar details)

dim_rooms (Room categories and types)

dim_hotels (Hotel properties and locations)

fact_aggregated_bookings (Summarized booking and revenue data)

fact_bookings (Detailed booking transactions)

**2. Data Cleaning & Transformation (Power Query)**


Removed duplicate records and handled missing values.

Standardized date formats and merged datasets to maintain consistency.

Created calculated columns for accurate reporting.

**3. Data Modeling in Power BI**


Established relationships between dimension and fact tables.

Used DAX formulas to compute revenue-based KPIs.

**4. DAX Formulas and Key Metrics**


Revenue-Based Metrics:

Total Revenue:

Total Revenue = SUM(fact_aggregated_bookings[Revenue])

Revenue Per Available Room (RevPAR):

RevPAR = DIVIDE([Total Revenue], SUM(fact_rooms[Total Rooms]), 0)

Average Daily Rate (ADR):

ADR = DIVIDE([Total Revenue], SUM(fact_bookings[Number of Nights]), 0)

Daily Sellable Room Nights (DSRN):

DSRN = SUM(fact_rooms[Total Rooms])

Daily Booked Room Nights (DBRN):

DBRN = SUM(fact_bookings[Rooms Booked])
Daily Utilized Room Nights (DURN):

DURN = SUM(fact_bookings[Rooms Occupied])
Time-Based Comparisons:

Month-over-Month (MoM) Revenue Change:

MoM Revenue Change = 

VAR PreviousMonthRevenue = CALCULATE([Total Revenue], DATEADD(dim_date[Date], -1, MONTH))

RETURN DIVIDE([Total Revenue] - PreviousMonthRevenue, PreviousMonthRevenue, 0)

Week-over-Week (WoW) Revenue Change:

WoW Revenue Change = 
VAR PreviousWeekRevenue = CALCULATE([Total Revenue], DATEADD(dim_date[Date], -7, DAY))

RETURN DIVIDE([Total Revenue] - PreviousWeekRevenue, PreviousWeekRevenue, 0)

Room Utilization Metrics:

Booking Utilization Rate:

Booking Utilization Rate = DIVIDE([DBRN], [DSRN], 0)
Occupancy Rate:

Occupancy Rate = DIVIDE([DURN], [DSRN], 0)
**5. Dashboard Development & Visualization**

KPIs & Cards: Displaying Total Revenue, RevPAR, ADR, and Occupancy Rate.

Bar & Line Charts: Showing MoM and WoW revenue trends.

Heatmaps: Highlighting peak revenue periods.

Slicers & Filters: Allowing dynamic selection based on hotel location, date range, and room type.

**6. Testing & Validation**

Verified DAX calculations against raw data.

Ensured interactive filters and slicers functioned correctly.

**7. Final Deployment & Business Insights**

Published the dashboard for business users.

Key takeaways:

✔ Identified peak revenue seasons and optimized pricing strategies.

✔ Analyzed room utilization rates for better resource management.

✔ Tracked revenue fluctuations to improve financial forecasting.

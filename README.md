# SENAE National Customs Revenue & Operations Dashboard

An enterprise-grade Business Intelligence solution engineered for the **National Customs Service of Ecuador (SENAE)**. This strategic dashboard provides a 24/7 real-time tracking architecture for tax collection, fiscal budget performance, and logistical operation metrics across all national ports and districts.



##  Executive Impact & Business Value

By shifting from reactive reporting to a data-driven paradigm, this analytical ecosystem achieved significant institutional milestones:

*   **Historical Revenue Collection:** Supported strategic oversight leading to an all-time high revenue collection of **$4 Billion USD** (a **15% year-over-year growth**).
*   **Sustained Fiscal Acceleration:** Driven an additional **25% growth during 2026** up to the current repository refresh date.
*   **24/7 Core Availability:** Eliminated reporting downtime by guaranteeing constant data availability for senior executive decision-making.
*   **Budget Alignment:** Established precision tracking for **Budget Achievement** and **YTD Execution** across multiple customs sub-categories (Tariffs, VAT, and Excise Taxes).



##  Key Visual Interfaces

### 1. Core Tax Revenue Performance `![Core Tax Revenue Performance](images/Captura_1.png)`
As shown in capture, this module breaks down monthly collections and percentage variations across the country's primary revenue streams: *Tariffs + FONDINFA*, *Value Added Tax (VAT)*, and *Excise Tax (ICE)*.

### 2. ISO-Standard Periodical Matrix `![Periodical matrix](images/Captura_2.png)`
Displayed in capture, this matrix isolates collection variations grouped by customized ISO-week periods, enabling granular comparative analytics across multiple historical fiscal years.

### 3. District Budget Tracking `![budget](images/Captura_3.png)`
Illustrated in capture, this tracking system analyzes performance target compliance by geographical customs districts (e.g., Guayaquil Marítimo, Quito, Manta), featuring daily accumulation trends and comprehensive gauge progress metrics.

### 4. Consolidated Monthly Analysis `![monthly analysis](images/Captura_4.png)`
As visualized in capture, this high-level summary computes total YoY growth, macro budget accomplishments, and cumulative monthly variances for executive presentations.



##  Technical Challenges & Architecture

### High-Volume Big Data ETL
The primary challenge of developing for a major public institution is processing and optimizing the massive, continuous influx of transaction ledgers. This required comprehensive data engineering to:
*   Sanitize and restructure deep historical database schemas.
*   Write ultra-efficient **SQL queries** to optimize ETL pipelines, drastically reducing memory usage and direct server stress.
*   Model an optimal star-schema data structure to support high-performance rendering in Power BI.

### Advanced DAX Engineering: Custom ISO Week Calendar
While standard time intelligence functions satisfy basic needs, the institution required a strict tracking framework tailored to custom operational cycles. To prevent temporal alignment drifting between fiscal years, a custom calendar table was engineered using **ISO 8601 Week Standards** via the following DAX calculations:

**ISO Year Extraction:**
```dax```
Year_Iso = YEAR('Calendar'[Date] + (4 - WEEKDAY('Calendar'[Date], 2)))


**ISO week creation**
```dax```
Weeks = 
VAR Fecha = 'Calendar'[Date]
VAR AnoISO = YEAR(Date + (4 - WEEKDAY(Date, 2)))
VAR First_Thursday = DATE(Year_Iso, 1, 4)
VAR First_Week_Start = First_Thursday - WEEKDAY(First_Thursday, 2) + 1
RETURN
INT( (Date -  First_Week_Start) / 7 ) + 1

##  Operational Optimization & Customs Dispatch Analytics

Beyond financial metrics, this project features an **operational analytics engine** dedicated to tracking import volumes and customs clearance dispatch times. 

*   **Customs Service Rate Analysis:** The system captures data showing that dispatch times experienced increases due to a strategic shift toward a **100% physical inspection policy (Aforo 100%)** driven by customs service rate structures.
*   **Bottleneck Mitigation:** This analytical layer allows port authorities to proactively manage logistics staff in high-traffic ports, balance the operational workload under full physical inspections, and mitigate infrastructure bottlenecks to expedite supply chain nationalization.

>  **Confidentiality Notice:** Because operational customs data, physical inspection logs, and logistics volumes are a matter of national security and strictly confidential, those specific layouts have been omitted from this public text and repository. I am currently developing an open-source version utilizing a robust **anonymized/synthetic dataset** to demonstrate the operational flow without exposing sensitive state records.

---

## Tech Stack Placed into Production
*   **BI & Modeling Engine:** Microsoft Power BI Desktop / Power BI Service
*   **Data Manipulation:** Power Query (M Language), DAX
*   **Database Management:** Advanced SQL Server (Query Optimization, Views, ETL)


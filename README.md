# HR Workforce Analytics & Exploratory Data Analysis
### Understanding Employee Retention, Sentiment, and Attrition Dynamics[cite: 4]
**Author:** Olaomo Favour Fiyinfoluwa[cite: 4]

---

## 📌 Project Overview

<p align="center">
  <a href="Image\Gemini_Generated_Image_sq9583sq9583sq95.jpg">
    <img src="Image\Gemini_Generated_Image_sq9583sq9583sq95.jpg" alt="HR Analytics Project " width="100%">
  </a>
</p>

---

## 📖 Introduction
The **HR Workforce Analytics & Exploratory Data Analysis** project evaluates workforce retention, compensation structures, employee sentiment, and organizational attrition across 311 employee records[cite: 4]. Utilizing relational human resources records across seven normalized entities, the analysis examines the operational, behavioral, and demographic markers that impact workforce stability[cite: 4]. By evaluating key factors such as engagement scores, tenure trajectories, project assignments, and exit rationales, this study bridges the gap between transactional workforce records and proactive human capital planning[cite: 4].

---

## 🚨 Problem Statement
Modern enterprises face escalating operational and financial overheads associated with talent attrition, employee disengagement, and unmonitored compensation disparities[cite: 4]. Without systematic diagnostic visibility into workforce records, organizations experience avoidable operational frictions[cite: 4]:

* **Unplanned Talent Attrition:** Unmonitored employee disengagement and uncompetitive compensation structures leading to high voluntary turnover[cite: 4].
* **Disengagement Leading Indicators:** Lack of visibility into behavioral precursors—such as sudden increases in tardiness or unexcused absences—that precede formal resignations[cite: 4].
* **Demographic & Compensation Misalignment:** Unaddressed disparities across departments and demographic cohorts where high compensation fails to translate into day-to-day job satisfaction[cite: 4].

The absence of unified, diagnostic workforce analytics prevents HR leadership and people managers from deploying targeted retention interventions before talent loss occurs[cite: 4].

---

## 🎯 Objectives
* **Consolidate Dimensional Data Architecture:** Integrate one central fact table with six dimension tables to normalize operational reporting lines, job titles, performance tiers, and departments[cite: 4].
* **Engineer Tenure & Longitudinal Features:** Calculate continuous employee tenure (`expyear`) and discretize workforce longevity into distinct analytical cohorts[cite: 4].
* **Quantify Behavioral & Operational Drivers:** Measure statistical correlations between compensation, special project volume, attendance metrics, and survey engagement[cite: 4].
* **Profile Demographic & Sentiment Equity:** Audit base salary structures and employee satisfaction across racial backgrounds, gender classifications, and marital statuses[cite: 4].
* **Diagnose Attrition Root Causes:** Isolate voluntary and involuntary exit rationales among terminated personnel to identify high-risk flight factors[cite: 4].

<p align="center">
  <a href="Image\Data_info.png">
    <img src="Image\Data_info.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

---

## 🗂️ Data Overview

The primary analytical dataset is derived from `HR Analytics.xlsx` containing 311 records across 30 attributes alongside supporting lookup tables[cite: 4]:

* **`Employee_Name`:** Full legal name of the employee (*Text / String*)[cite: 4].
* **`EmpID`:** Unique primary key identification number (*Numeric / Integer*)[cite: 4].
* **`Salary`:** Base annual compensation in USD (*Numeric / Integer*)[cite: 4].
* **`Termd`:** Binary employment status flag where $1 = \text{Terminated}$ and $0 = \text{Active}$ (*Numeric / Integer*)[cite: 4].
* **`Position` / `PositionID`:** Standardized organizational role designation (*Text / Integer*)[cite: 4].
* **`Department` / `Department ID`:** Business unit assignment such as Production, IT/IS, or Sales (*Text / String*)[cite: 4].
* **`ManagerName` / `ManagerID`:** Direct supervisory and reporting hierarchy (*Text / Integer*)[cite: 4].
* **`State`:** State of employee residence (*Text / String*)[cite: 4].
* **`DOB` / `DateofHire`:** Employee birth date and onboarding timestamps (*Datetime*)[cite: 1, 4].
* **`DateofTermination`:** Official timestamp of employment cessation (*Datetime / 104 Non-Null, 207 Null for Active Staff*)[cite: 4].
* **`TermReason`:** Documented business rationale for contract termination (*Text / String*)[cite: 4].
* **`EngagementSurvey`:** Internal organizational engagement score ranging from 1.00 to 5.00 (*Numeric / Float*)[cite: 4].
* **`EmpSatisfaction`:** Standardized self-reported job satisfaction rating from 1 to 5 (*Numeric / Integer*)[cite: 4].
* **`SpecialProjectsCount`:** Number of cross-functional strategic initiatives assigned (*Numeric / Integer*)[cite: 4].
* **`DaysLateLast30`:** Frequency of tardiness occurrences within the trailing 30 days (*Numeric / Integer*)[cite: 4].
* **`Absences`:** Cumulative count of unexcused absences (*Numeric / Integer*)[cite: 4].

<p align="center">
  <a href="Image\Data_info.png">
    <img src="Image\Data_info.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

---

## 📊 Analytical Methodology & Feature Engineering

### 1. Data Cleaning & Tenure Engineering
* **Right-Censoring Imputation:** Imputed missing values in `DateofTermination` for active personnel using the observation date, ensuring tenure calculation without dropping active workforce records[cite: 4].
* **Tenure Calculation (`expyear`):** Engineered a continuous service length metric:
  $$\text{expyear} = \frac{\text{Effective End Date} - \text{DateofHire}}{365.25}$$
* **Cohort Segmentation:** Categorized workforce tenure into strategic bands: `0-2 Years`, `3-5 Years`, `6-10 Years`, and `10+ Years`[cite: 4].

<p align="center">
  <a href="Image\Data_cleaning.png"
    <img src="Image\Data_cleaning.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

<p align="center">
  <a href="Image\Data_cleaning_2.png"
    <img src="Image\Data_cleaning_2.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

### 2. Analytical Framework
* **Correlation Matrix Evaluation:** Mapped Pearson linear relationships between numerical operational metrics (Salary, Engagement, Satisfaction, Special Projects, Tardiness, Absences, and Tenure)[cite: 4].
* **Cross-Demographic Aggregation:** Grouped base salary, engagement, and satisfaction indices across demographic groups to evaluate structural parity[cite: 4].
* **Multi-Variable Sentiment Profiling:** Segmented satisfaction across role designations, gender classifications, and marital categories[cite: 4].
* **Terminated Cohort Isolation:** Filtered the subset of departed staff ($N = 104$) to analyze frequency distributions of documented departure reasons[cite: 4].

<p align="center">
  <a href="Image\Data_correlation.png">
    <img src="Image\Data_correlation.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

---

## 💡 Key Insights

### 1. Behavioral Predictors & Operational Drivers
* **Tardiness Serves as an Attrition Warning ($r = -0.59$):** A strong negative correlation exists between trailing 30-day tardiness (`DaysLateLast30`) and employee engagement scores[cite: 4]. Escalating attendance irregularities indicate declining employee engagement prior to formal resignation[cite: 4].
* **Special Projects Drive Compensation Growth ($r = +0.51$):** Cross-functional strategic initiatives correlate positively with base compensation, highlighting that project opportunities are concentrated among senior technical and managerial positions[cite: 4].

<p align="center">
  <a href="Image\Table_1.png">
    <img src="Image\Table_1.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

### 2. Demographic Equity & Satisfaction Patterns
* **Compensation vs. Satisfaction Divergence:** The **Hispanic** demographic records the highest average base compensation ($83,667) and highest engagement survey rating (4.37), yet registers the lowest satisfaction score (3.00)[cite: 4]. This indicates that compensation alone does not ensure day-to-day job satisfaction[cite: 4].
* **High Satisfaction Cohorts:** The **American Indian or Alaska Native** group records the highest overall satisfaction score (4.67) and strong engagement (4.20) at a base salary of $65,806[cite: 4].
* **Core Segment Distributions:** **Black or African American** personnel average $74,431 in salary with balanced satisfaction (3.94) and engagement (4.07), while **White** personnel average $67,288 in base pay with 3.89 satisfaction and 4.16 engagement[cite: 4].

<p align="center">
  <a href="Image\Chart_4.png">
    <img src="Image\Chart_4.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

### 3. Root Causes of Workforce Attrition
* **Competitive Poaching Dominates Departures:** **"Another position"** accounts for 20 exits, making it the primary driver of turnover[cite: 4]. Combined with **"Unhappy"** (14 exits), **"More money"** (11 exits), and **"Career change"** (9 exits), voluntary market-driven exits outnumber involuntary terminations[cite: 4].
* **Operational Enforcements:** Involuntary separations primarily stem from attendance violations (7 exits), performance deficiencies (4 exits), and unexcused no-call/no-shows (4 exits)[cite: 4].
* **Demographic Exit Proportions:** Total terminations follow broader organizational representation, led by White employees (>60 exits), followed by Black or African American employees (~29 exits) and Asian employees (~9 exits)[cite: 4].

<p align="center">
  <a href="Image\data_Chart.png">
    <img src="Image\data_Chart.png" alt="HR Analytics Project " width="100%">
  </a>
</p>

---

## 🛠️ Strategic Recommendations

1. **Implement Early-Warning Retention Protocols:** Establish automated HR alerts for spikes in 30-day tardiness (`DaysLateLast30`) to initiate proactive stay-interviews before disengagement results in turnover[cite: 4].
2. **Benchmark Pay & Career Mobility Pathways:** Formulate structured compensation adjustments and transparent internal promotion ladders to counter external talent loss, addressing the leading exit causes ("another position" and "more money")[cite: 4].
3. **Investigate Departmental Culture Friction:** Review day-to-day workplace dynamics within high-compensation, low-satisfaction units to reduce operational burnout and workplace friction[cite: 4].
4. **Democratize Strategic Project Allocation:** Broaden assignment criteria for high-impact special projects beyond senior staff to expand professional development pathways for mid-tier personnel[cite: 4].

---

## 🔗 Project Links

* 📝 **Medium Case Study:** [Read Full Analysis on Medium](https://medium.com/@olaomofavour/decoding-workforce-dynamics-an-in-depth-hr-analytics-eda-case-study-3ed125a3d65aE)
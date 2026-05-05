# Annex Technologies Limited. Data Engineer Case Study

## ABC Phones Credit Portfolio Analysis

**Position:** Data Engineer  
**Expected Time Commitment:** 72 hours  
**Submission Format:** Slide deck (maximum 10 slides) + GitHub repository or zipped code folder

---

## Our Mission

At Annex Technologies, we build scalable data infrastructure that powers intelligent decision-making across East Africa. We believe well-architected data pipelines are the foundation of great analytics, and we're looking for engineers who can design, build, and productionize them at scale.

---

## Case Study Overview

ABC Phones offers smartphones to customers through installment-based credit plans and manages these accounts throughout the repayment period. Customers make regular payments toward their outstanding balances, and credit decisions play a critical role in both portfolio performance and customer experience.

While ABC Phones has systems to process payments and manage accounts, their data engineering and analytics infrastructure is still maturing. **Your challenge is to design and build the data systems that will enable reliable, repeatable analysis.**

### Provided Datasets

| Dataset | Description | Contents |
|---------|-------------|----------|
| **Credit Data (1).zip** | Credit portfolio snapshots, point-in-time views across multiple reporting dates | Account balances, payment history, status, arrears |
| **Sales and Customer Data (1).zip** | Customer demographics and sales records | DOB, income fields, employment duration, acquisition data |
| **NPS Data (1).xlsx** | NPS survey responses, linked to customer IDs | Customer satisfaction metrics, feedback |

**Note:** These datasets contain real-world inconsistencies, missing values, and structural challenges, exactly what you'd encounter in a production environment.

---

---

## Part 1: Data Preparation & Pipeline Design

### 1A. Data Profiling & Cleaning

Before any analysis can begin, you must thoroughly understand the raw data.

**Complete the following:**

- **Profile all three datasets:**
  - Row counts and column data types
  - Null percentages for each column
  - Data inconsistencies (date formats, currency formats, duplicate IDs, etc.)
  - Relationship analysis between datasets (join keys, cardinality, foreign key integrity)

- **Document your findings:**
  - Create a data quality report showing inconsistencies discovered
  - State all assumptions clearly (e.g., how you handle missing values, date interpretations)
  - Justify every cleaning decision

### 1B. Feature Engineering

Derive the following fields programmatically (using Python/SQL):

| Feature | Definition | Bands/Categories |
|---------|-----------|-------------------|
| `age_band` | Calculate age from DOB as at each reporting date | 18–25, 26–35, 36–45, 46–55, 55+ |
| `avg_monthly_income_band` | Sum all income-related columns; divide by employment duration | Below 5,000 / 5,000–9,999 / 10,000–19,999 / 20,000–29,999 / 30,000–49,999 / 50,000–99,999 / 100,000–149,999 / 150,000+ |
| `days_past_due` | Days between payment due date and reporting date (0 if no arrears) | Integer |
| `risk_category` | Derived from account status, arrears amount, and payment history patterns | Define your logic (e.g., Low / Medium / High / Critical) |

**Requirement:** Show your feature engineering logic in clean, documented code.

### 1C. ETL Pipeline Design

Design a **batch ETL pipeline** that ingests the three source files and produces clean, analytics-ready data tables.

**Your answer must include:**

- **Architecture Diagram**
  - Illustrate data flow from source → ingestion → transformation → storage
  - Show tools/technologies (e.g., Python + Pandas, dbt, SQL, cloud services)
  - Include error handling and logging paths
  
- **Ingestion Strategy**
  - Full load vs. incremental load approach
  - Scheduling and frequency (daily, weekly, etc.)
  - Handling of late-arriving or duplicate data

- **Transformation Logic**
  - Data cleaning and standardization steps
  - Deduplication rules
  - Enrichment (e.g., joining customer and credit data)
  - Feature engineering automation
  
- **Storage & Output Design**
  - What analytics-ready tables/views would you create?
  - How would analysts query this data?
  - Partitioning strategy (e.g., by reporting date, customer segment)

- **Error Handling & Recovery**
  - What happens if a source file is missing or malformed?
  - How do you alert stakeholders?
  - How do you ensure data consistency?

**Deliverable:** 
- Architecture diagram (PNG or PDF)
- 2–3 slides explaining key engineering decisions
- Annotated code or pseudocode for critical transformation steps

---

## Part 2: Data Quality Framework

As ABC Phones' customer base grows, data quality becomes mission-critical. Design a robust monitoring framework.

### Requirements

**1. Implement 5 Specific Data Quality Checks**

Examples (choose yours based on the data):
- **Freshness:** Is data arriving on schedule? (e.g., daily portfolio snapshot by 6 AM)
- **Uniqueness:** Are there unexpected duplicate customer or account records?
- **Referential Integrity:** Do all customer IDs in credit data exist in customer master?
- **Range Checks:** Are ages between 18–120? Are income values within reasonable bounds?
- **Null Thresholds:** What percentage of missing values is acceptable per column?

**2. Alerting Strategy**

- How does the team know when a check fails?
- Who gets notified (data engineer, analyst, business stakeholder)?
- What's the escalation path for critical failures?

**3. Real Example from Provided Data**

Identify one actual inconsistency or anomaly in the provided datasets and explain how your framework would detect it before it reached analysts.

**4. Monitoring Cadence**

Define what's checked:
- **Real-time:** (e.g., row count thresholds)
- **Daily:** (e.g., referential integrity)
- **Weekly:** (e.g., trend analysis for anomalies)

**Deliverable:**
- Framework overview (1–2 slides in your presentation)
- SQL or Python example implementation of at least one check
- Screenshot or log output showing the check in action

---

## Part 3: Portfolio Analysis & Insights

Using your cleaned data and ETL pipeline, answer the following business questions.

### Question 3A: Portfolio Health

Select **3–5 key metrics** to assess credit portfolio performance, such as:
- Delinquency rate (% of accounts past due)
- Loss rate (write-offs / total portfolio)
- Average payment collection rate
- Customer retention rate

**Analyze:**
- How do these metrics trend across reporting snapshots?
- Identify one customer segment (age or income band) where risk behaviour differs meaningfully from the portfolio average
- Visualize findings clearly

### Question 3B: Credit Outcomes × Customer Experience

Explore the relationship between credit performance and NPS scores.

**Investigate:**
- Do customers with lower credit scores report lower NPS?
- Is there a tension between collections effectiveness and customer satisfaction?
- Where could ABC Phones improve both outcomes simultaneously?

**Recommendation:** Propose one concrete, actionable change ABC Phones should make based on your analysis.

### Question 3C: Data Gaps & Future Improvements

Critique the source data honestly.

**Identify:**
- What is missing? (e.g., employment type, location data, transaction-level detail)
- What is inconsistent? (e.g., date formats, income calculation methods)
- What is ambiguous? (e.g., how is account status defined?)

**Propose 2–3 specific improvements** to how ABC Phones captures or structures data for easier ongoing monitoring.

**Deliverable:** Analysis integrated into your slide deck (not submitted separately)

---

## Submission Structure

Create a folder and organize your submission as follows:

```
Annex_DE_<YourName>/
├── README.md                          # Setup, assumptions, how to run
├── pipeline_design/
│   └── architecture.png               # Architecture diagram
├── scripts/
│   ├── data_profiling.py              # or .sql — profile all datasets
│   ├── data_cleaning.py               # Cleaning and standardization
│   ├── feature_engineering.py         # Feature derivation logic
│   ├── quality_checks.py/.sql         # Data quality check examples
│   └── analysis.py/.sql               # Portfolio analysis queries
├── slides/
│   └── Annex_DE_Presentation.pdf      # Final presentation deck
└── outputs/
    ├── cleaned_summary.csv            # Sample cleaned dataset
    ├── data_quality_report.md         # Profiling findings
    └── portfolio_metrics.csv           # Analysis results
```

### Submission Options

**Preferred:** Public GitHub repository with complete code and documentation
- Link must be provided in your submission email
- Repository should include a clear README with setup and execution instructions

---

**Thank you for your interest in Annex Technologies. We look forward to reviewing your work**

*Annex Technologies Limited*  
*Talent Acquisition Team*

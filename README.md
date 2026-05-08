# Customer Shopping Behaviour Analysis

> Uncovering insights from 3,900 purchases to guide strategic business decisions.

---

## Project Overview

This project analyses a retail customer dataset of **3,900 transactions** to understand shopping patterns, identify high-value customer segments, and generate actionable business recommendations. The full pipeline covers data cleaning in Python, structured query analysis in MySQL, and interactive dashboards in Power BI.

**Tools used:** Python (pandas), MySQL, SQLAlchemy, Power BI Service

---

## The Dataset

The dataset contains 3,900 rows and 18 columns covering customer demographics, purchase behaviour, product preferences, and transaction details. The only column with missing values was Review Rating, which had 37 missing entries.

---

## Step 1 — Data Loading & Initial Exploration

The dataset was loaded into a pandas DataFrame and inspected to understand its structure. Summary statistics were generated to check the range and distribution of numeric columns such as age, purchase amount, review rating, and previous purchases. This initial pass confirmed the data was well-formed with only one column requiring attention.

---

## Step 2 — Handling Missing Values

The 37 missing values in the Review Rating column were filled using the **median rating for each product category**. This approach was chosen over a global median because different categories (Clothing, Footwear, etc.) naturally attract different satisfaction levels, making a category-level imputation more accurate and representative.

---

## Step 3 — Standardising Column Names

All column names were converted to lowercase with underscores replacing spaces, so the data could be queried consistently in Python and SQL without case-sensitivity issues. The column `Purchase Amount (USD)` was renamed to `purchase_amount` for simplicity.

---

## Step 4 — Removing Redundant Columns

It was discovered that the `Promo Code Used` column was completely identical to the `Discount Applied` column — every single row had the same value in both. Since they carried no additional information, `Promo Code Used` was dropped to keep the dataset clean and avoid confusion in analysis.

---

## Step 5 — Feature Engineering

Two new columns were created to enable richer analysis:

**Age Group** — Customers were divided into four segments based on their age using quartile-based binning: Young Adult, Adult, Middle-aged, and Senior. This allows revenue and behaviour to be compared across life stages rather than individual ages.

**Purchase Frequency in Days** — The `Frequency of Purchases` column contained text values like "Weekly", "Fortnightly", and "Annually". These were converted to numeric day values (7, 14, 365, etc.) so that engagement frequency could be analysed and compared quantitatively.

---

## Step 6 — MySQL Integration

The cleaned dataset was pushed into a MySQL database using SQLAlchemy. This allowed all further analysis to be done using structured SQL queries, which are better suited for aggregations, grouping, and filtering across large datasets. The database and table were created automatically, and the data was verified by reading back a sample.

---

## Step 7 — SQL Analysis

Ten structured queries were written to extract business insights from the data, covering revenue by gender, high-value discount users, top-rated products, shipping preferences, subscription impact, discount rates by product, customer segmentation, top products per category, repeat buyer patterns, and revenue by age group.

---

## Step 8 — Power BI Dashboard

The cleaned dataset was exported as a CSV and connected to Power BI Service. An interactive dashboard was built with KPI cards showing total customers, average purchase amount, and average review rating, alongside bar charts for revenue and customer count by category, a pie chart for revenue by gender, and a donut chart showing subscription status distribution.

---

## Key Findings

| Finding | Detail |
|---------|--------|
| Top revenue age group | Middle-aged customers — $87,576 |
| Lowest revenue age group | Young Adults — $34,630 |
| Best-rated product | Gloves — 3.86 out of 5.0 |
| Highest discount usage | Hat — 50% of purchases used a discount |
| Most popular category | Clothing — Pants and Blouse tied at 171 orders each |
| Shipping spend difference | Express customers spend 3.5% more per transaction |
| Loyal customer share | 80% of the base — 3,116 customers with 11+ purchases |
| New customer share | Only 2% — 83 first-time buyers |

---

## Business Recommendations

### R1 — Launch a Tiered Loyalty Rewards Program

80% of customers are already loyal repeat buyers, but there is no structured system to reward or reinforce that loyalty. A tiered programme with Bronze, Silver, and Gold levels — each unlocking better perks like exclusive discounts, early access to sales, and free shipping upgrades — would give customers a reason to keep choosing the brand over competitors. It also creates a sense of progress and belonging that keeps engagement high.

### R2 — Personalised Re-engagement Campaigns

Annual and quarterly buyers are the most disengaged segment and are at the highest risk of dropping off entirely. Sending personalised outreach — such as a tailored discount or product recommendation — to customers who have not purchased in 90 or more days can bring them back before they are lost. The messaging should reference their past purchases and preferred category to feel relevant rather than generic.

### R3 — Strengthen the Subscription Value Proposition

Subscribers and non-subscribers spend nearly the same amount per purchase, which suggests that the subscription is not offering enough compelling value to drive higher engagement or spending. Adding perks that are exclusive to subscribers — such as priority shipping, birthday rewards, monthly surprises, or early sale access — would make the subscription feel worth having. These benefits should be clearly communicated at sign-up and renewal.

### R4 — Target Young Adults with Tailored Campaigns

Young Adults generate the lowest revenue of any age group and are the least represented in the loyal customer base. This segment likely responds differently to marketing, products, and pricing than older groups. A dedicated strategy using social media, influencer partnerships, and a student or young adult discount tier could grow this segment and build the next generation of loyal customers.

### R5 — Product Quality Improvement Program

The average review rating across all products is 3.75 out of 5.0, which leaves meaningful room for improvement. Products that consistently receive low ratings should be investigated for quality issues, misleading descriptions, or sizing problems. Actively collecting post-purchase feedback and acting on it would improve satisfaction and reduce the likelihood of one-time buyers not returning.

### R6 — Accelerate New Customer Acquisition

With only 83 new customers representing 2% of the entire base, the pipeline is dangerously thin. The business is almost entirely reliant on existing customers, meaning any increase in drop-off rates would have a significant impact. A referral programme, seasonal acquisition campaigns, and partnerships with complementary brands would widen the top of the funnel and ensure the customer base grows rather than gradually shrinks.

---

## File Structure

| File | Description |
|------|-------------|
| `customer_shopping_behavior.csv` | Raw dataset |
| `customer_data.csv` | Cleaned and enriched dataset after EDA |
| `customer_shopping_behaviour_analysis.ipynb` | Full Python analysis notebook |
| `customer_behaviour.pbix` | Power BI interactive dashboard |


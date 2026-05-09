# Digital Wallet Customer Retention Analysis

## Cohort Analysis for Customer Retention, Engagement, and Marketing Strategy

This project analyzes customer retention behavior for a digital wallet platform using cohort analysis. The goal is to understand how users return after their first transaction, identify retention drop-off patterns, and uncover product-category-level opportunities that can support customer engagement and lifecycle marketing strategies.

The analysis is built in Python using transaction-level digital wallet data and focuses on turning raw transactional activity into actionable retention insights.

---

## Project Objective

Digital wallet platforms depend heavily on repeat usage. A customer making one transaction is valuable, but long-term business growth depends on whether that customer continues using the wallet across future months and product categories.

The objective of this project is to:

- Evaluate customer retention behavior over time
- Build monthly cohorts based on each user’s first transaction month
- Measure how many users return in later months
- Identify where customer drop-off is highest
- Analyze product-category-level retention patterns
- Translate findings into business recommendations for marketing and customer engagement teams

---

## Business Problem

Many digital wallet users may try the platform once but fail to return. This creates challenges for growth, customer lifetime value, and marketing efficiency.

Key business questions explored in this project:

- Are customers returning after their first transaction?
- Which monthly cohorts show stronger or weaker retention?
- How quickly do users drop off after onboarding?
- Are recent cohorts smaller, indicating a possible acquisition slowdown?
- Do certain product categories show stronger repeat behavior?
- How can marketing teams use retention patterns to improve engagement?

---

## Dataset Overview

The dataset contains digital wallet transaction records sourced from Kaggle.

Key fields include:

- `transaction_id`
- `user_id`
- `transaction_date`
- `product_category`
- `product_name`
- `merchant_name`
- `product_amount`
- `transaction_fee`
- `cashback`
- `loyalty_points`
- `payment_method`
- `transaction_status`
- `merchant_id`
- `device_type`
- `location`

---

## Methodology

### 1. Data Loading and Initial Exploration

The transaction dataset was loaded into a Pandas DataFrame and reviewed for structure, data types, missing values, and key summary statistics.

Initial checks included:

- Dataset shape and column review
- Data type validation
- Missing value analysis
- Descriptive statistics
- Transaction date conversion
- Monthly transaction period creation

The dataset had no missing values across the available fields, which allowed the analysis to move directly into feature preparation and cohort modeling.

---

### 2. Transaction Month Creation

The `transaction_date` field was converted into a datetime format and transformed into a monthly period.

This helped group customer activity by month and build retention cohorts.

Example logic:

```python
df_trans['transaction_date'] = pd.to_datetime(df_trans['transaction_date'])
df_trans['transaction_month'] = df_trans['transaction_date'].dt.to_period('M')
```

---

### 3. Cohort Assignment

Each user was assigned a cohort month based on their first transaction month.

This means every user belongs to the month in which they first used the digital wallet.

Example:

- If a user made their first transaction in August 2023, they belong to the August 2023 cohort.
- Their future transactions in later months are used to measure retention.

---

### 4. Cohort Index Calculation

A cohort index was created to measure how many months had passed since the user’s first transaction.

For example:

- Month 0 = first transaction month
- Month 1 = first month after initial transaction
- Month 2 = second month after initial transaction

This allows retention to be compared consistently across cohorts.

---

### 5. Retention Matrix Creation

A cohort retention table was created by counting unique active users in each cohort month and dividing future-month activity by the original cohort size.

This helped measure:

- Initial cohort size
- Month-over-month user retention
- Drop-off after first usage
- Retention consistency across cohorts

---

### 6. Visualization

The retention matrix was visualized using heatmaps to make retention patterns easier to interpret.

This helped identify:

- Stronger and weaker cohorts
- Drop-off points
- Retention decay over time
- Month 1 retention performance
- Category-level retention opportunities

---

## Key Findings
### 1. Recent Cohorts Appear Smaller

The analysis showed that more recent cohorts were smaller than earlier cohorts. This may indicate a slowdown in new customer acquisition.

Possible causes could include:

- Lower marketing spend
- Increased competition
- Reduced campaign effectiveness
- Product experience friction
- Lower customer awareness

---

### 2. Significant Drop After Month 1

The monthly retention rate showed a sharp drop after the first month. This suggests that many users try the digital wallet once but do not continue using it regularly.

This is a critical retention issue because digital wallet success depends on habit formation and recurring transactions.

---

### 3. Retention Remains Low Across Most Cohorts

Most cohorts were only able to sustain customers at a low retention level after the first month. This indicates that customer loyalty and repeat engagement may be weak across the platform.

From a business perspective, this suggests the platform may need stronger onboarding, lifecycle campaigns, personalized offers, or category-specific engagement strategies.

---

### 4. Some Categories Show Better Retention Potential

The notebook analysis suggests that a few product categories perform better after Month 1 compared to others. These categories may represent stronger use cases where customers are more likely to build repeat behavior and trust.

These categories should be studied further to identify what drives stronger retention.

---

## Business Recommendations

Based on the cohort analysis, the digital wallet platform should focus on improving early lifecycle engagement and category-level retention.

### 1. Improve First 30-Day Engagement

Since retention drops sharply after the first month, the platform should focus on the customer’s first 30 days after signup or first transaction.

Recommended actions:

- Trigger welcome campaigns after first transaction
- Offer second-transaction cashback incentives
- Send reminders for common recurring payments
- Promote high-retention use cases early
- Create personalized nudges based on first transaction category

---

### 2. Build Category-Specific Retention Campaigns

Some categories show better retention potential than others. Marketing teams can use this insight to design category-specific campaigns.

Examples:

- Bill payment reminders
- Cashback on repeat utility payments
- Subscription payment offers
- Travel or ticketing promotions
- Merchant-specific loyalty campaigns

Instead of treating all users the same, the platform can personalize engagement based on product category behavior.

---

### 3. Use Cashback and Loyalty Points Strategically

The dataset includes cashback and loyalty points, which can be used as retention levers.

Recommended next steps:

- Analyze whether higher cashback leads to repeat transactions
- Compare retention between high-loyalty-point and low-loyalty-point users
- Test targeted rewards for users likely to churn
- Measure whether reward campaigns improve Month 1 and Month 2 retention

---

### 4. Segment Users by Payment Method, Device, and Location

The dataset includes payment method, device type, and location. These dimensions can help uncover behavioral differences.

Potential segmentation:

- UPI vs debit card vs credit card vs wallet balance users
- Android vs iOS users
- Urban vs semi-urban vs rural customers
- High-value vs low-value transaction users

This can help marketing and product teams understand which customer groups are more likely to return.

---

### 5. Build a Retention Monitoring Dashboard

The cohort analysis can be extended into a dashboard for ongoing retention monitoring.

Recommended dashboard metrics:

- Monthly active users
- New user cohorts
- Month 1 retention
- Month 2 retention
- Product-category retention
- Payment-method retention
- Churned users
- Repeat transaction rate
- Average transaction value by cohort

---

## Potential Business Impact

This analysis can help digital wallet teams:

- Identify early customer drop-off
- Improve repeat transaction behavior
- Increase customer lifetime value
- Design better lifecycle marketing campaigns
- Prioritize high-retention product categories
- Optimize cashback and loyalty programs
- Support data-driven customer engagement strategy

---

## Future Enhancements

This project can be extended further by adding:

- Revenue retention analysis
- Customer lifetime value analysis
- Churn prediction model
- RFM segmentation
- Product-category-level cohort analysis
- Payment-method-level retention analysis
- Cashback effectiveness analysis
- Loyalty point impact analysis
- Streamlit dashboard for interactive retention monitoring
- Automated monthly retention reporting

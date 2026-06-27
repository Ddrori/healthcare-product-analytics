# Healthcare Product Analytics: Clinician Engagement and Retention

## Overview

This notebook demonstrates a product analytics workflow using a synthetic event dataset that simulates clinician interactions with a healthcare AI platform.

The goal of the project is to analyze user behavior throughout the product lifecycle, from onboarding and retention to feature adoption and disengagement, while emphasizing not only how to calculate product metrics, but also how to critically evaluate whether those metrics truly reflect product value.
---

## Project Objectives

The notebook addresses four common product analytics questions:

- How well are new users retained over time?
- Where do users drop out of the product workflow?
- How should engagement with AI-generated recommendations be measured?
- How can behavioral data be used to detect early signs of user disengagement?
---

## Dataset

A synthetic event dataset was generated containing approximately **1,000 events** across **120 users**.

Each event contains:

- `user_id`
- `signup_date`
- `event_date`
- `event_type`

The simulated event types are:

- Login
- Open Patient Chart
- Accept AI Insight
- Dismiss AI Insight
- Documentation

---

## Notebook Contents

### 1. Synthetic Data Generation

Creates an event log that simulates clinician interactions with a healthcare AI platform.

---

### 2. Cohort Analysis

Calculates weekly activity by signup cohort and visualizes the results using a cohort heatmap. The analysis measures activity-based retention, allowing users to become active again after periods of inactivity.

---

### 3. Conversion Funnel

Builds a clinician workflow funnel:

**Login → Open Patient Chart → Accept AI Insight**

The implementation enforces chronological event order, making the analysis more robust to real-world data quality issues such as delayed event logging or missing events.

The funnel analysis reports:

- User counts at each stage
- Overall conversion from login to each subsequent stage
- Conversion between consecutive stages
- Step-to-step drop-off to highlight the largest point of user abandonment

---

### 4. Engagement KPI

Defines and analyzes the custom KPI:

**Accepted Insights per Active Clinician per Week**

Rather than simply calculating the metric, the notebook discusses its strengths and limitations in the context of clinical decision support.

A central conclusion is that **acceptance of AI recommendations should not automatically be interpreted as product success**, since clinicians should critically evaluate AI recommendations rather than accept them by default.

---

### 5. Drop-off Detection

Identifies clinicians who were active for at least two consecutive weeks before becoming inactive for two consecutive weeks.

For each flagged user, the notebook reports:

- Last active week
- Weeks active before drop-off
- Total recorded events
- Last recorded event type

Additional visualizations summarize:

- Distribution of weeks active before disengagement
- Last event type before drop-off

---

## Key Findings

- Weekly clinician activity varied across cohorts but remained within a relatively consistent range. By Week 4, activity ranged between 48% and 65% across cohorts. Because this analysis measures activity-based retention, clinicians can return after periods of inactivity, resulting in fluctuations rather than the steady decline typically observed in continuous retention analyses.
- The largest workflow drop-off occurred before clinicians reached the platform's core feature. While 100% of users logged in, only **55.7%** progressed to opening a patient chart, suggesting that improving navigation or workflow integration may have a greater impact on adoption than optimizing later stages of the user journey.
- Only **20.0%** of clinicians ultimately accepted an AI-generated insight. However, this metric should not be interpreted as a direct measure of product success. In a clinical decision support system, rejecting an AI recommendation may represent appropriate clinical judgment rather than ineffective product usage.
- Most users flagged as disengaging had been active for several weeks before becoming inactive. This suggests that maintaining long-term engagement may be as important as improving onboarding and early feature adoption. In a production environment, these users could be targeted with proactive interventions before they disengage completely.

---

## Technologies Used

- Python
- pandas
- NumPy
- Matplotlib
- Jupyter Notebook

---

## Skills Demonstrated

- Product analytics
- User behavior analysis
- Cohort analysis
- Funnel analysis
- KPI design and evaluation
- Retention analysis
- User engagement analysis
- Behavioral event analysis
- Exploratory data analysis (EDA)
- Data visualization

---

## Discussion

A central objective of this project was to demonstrate that effective product analytics extends beyond calculating metrics. Equally important is selecting appropriate measures, understanding their limitations, and interpreting them in the context of product goals and user behavior.

Throughout the notebook, each analysis is accompanied by product-oriented insights that connect quantitative results to potential business decisions. The project also highlights methodological considerations, for example, distinguishing activity-based retention from continuous retention and enforcing chronological event order in the funnel analysis to better reflect real-world event data.

The engagement KPI illustrates why metric selection requires careful consideration. In a clinical decision support system, maximizing AI recommendation acceptance is not necessarily aligned with the product's purpose. Clinicians should evaluate AI recommendations critically rather than accept them by default, meaning that a rejected recommendation may still represent successful product use.

More broadly, the project argues that product metrics should encourage behaviors that create genuine value for users rather than simply optimize dashboard numbers. This perspective emphasizes that effective product analytics is not only about measuring user behavior, but also about ensuring that the chosen metrics support better product decisions and better user outcomes.

---

## Future Work

Possible extensions of this project include:

- **Predictive modeling** to identify clinicians at risk of disengagement before churn occurs using behavioral features derived from event data.
- **Survival analysis** to model long-term user retention and estimate the probability of disengagement over time.
- **Validation using real product event data** to evaluate how well the analyses, KPIs, and engagement patterns identified in this synthetic dataset generalize to production environments.

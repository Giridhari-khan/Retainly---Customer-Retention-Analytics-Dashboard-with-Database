# Retainly---Customer-Retention-Analytics-Dashboard-with-Database

<img width="737" height="570" alt="image" src="https://github.com/user-attachments/assets/cfb88662-ccf9-4028-a8ba-026257a636cf" />


## Project Overview

Retainly is a customer retention analytics platform designed to help coaches, consultants, freelancers, and service businesses identify at-risk clients before churn occurs.

The system automates weekly client check-ins, collects structured feedback, analyzes sentiment, and provides a real-time dashboard for monitoring client health.

This project focuses on retention analytics, customer behavior monitoring, KPI tracking, and business intelligence reporting using a relational database and dashboard-driven insights.

---

## Business Problem

Acquiring clients is expensive.

Many coaches and freelancers lose clients without receiving early warning signals. Traditional CRM systems track customer information but fail to provide actionable retention insights.

Retainly solves this problem by:

* Automating client engagement
* Tracking customer sentiment
* Identifying churn risk
* Monitoring retention trends
* Providing real-time retention dashboards

---

## Objectives

* Improve customer retention visibility
* Detect at-risk clients early
* Measure client engagement levels
* Monitor response behavior over time
* Support data-driven customer success decisions

---

## Dataset Structure

<img width="975" height="567" alt="image" src="https://github.com/user-attachments/assets/6b51622c-1602-44b3-86e2-00c51e3ba831" />

### Coaches

Stores account and subscription information.

| Field             | Description             |
| ----------------- | ----------------------- |
| user_id           | Coach account           |
| plan              | Subscription plan       |
| plan_client_limit | Maximum client capacity |
| plan_expires_at   | Subscription expiry     |

### Clients

Stores customer profile and engagement information.

| Field                     | Description           |
| ------------------------- | --------------------- |
| client_id                 | Unique customer       |
| coach_id                  | Associated coach      |
| goal                      | Customer objective    |
| timezone                  | Customer timezone     |
| status                    | Current health status |
| last_checkin_submitted_at | Latest engagement     |
| checkin_frequency_days    | Contact frequency     |

### Checkins

Stores weekly customer feedback.

| Field            | Description               |
| ---------------- | ------------------------- |
| stars            | Satisfaction score        |
| sentiment_result | Happy / Neutral / At Risk |
| blocker_text     | Customer challenges       |
| win_text         | Customer achievements     |

### Checkin Tokens

Tracks secure survey submissions.

---

## Entity Relationship Model

coaches
│
├── clients
│
└── checkins
│
└── checkin_tokens

Relationship:

Coach → Many Clients

Client → Many Check-ins

Client → Many Check-in Tokens

---

## Key Performance Indicators (KPIs)

<img width="1468" height="685" alt="image" src="https://github.com/user-attachments/assets/d3b48584-4b6c-4458-be6a-6619c77f33b0" />

### Retention Rate

Percentage of active clients remaining over a period.

Retention Rate (%) =
(Ending Clients - New Clients) / Starting Clients × 100

---

### Churn Risk Rate

Percentage of clients currently classified as "At Risk".

Churn Risk Rate (%) =
At Risk Clients / Total Clients × 100

---

### Customer Health Score

Calculated using:

* Satisfaction Rating
* Response Frequency
* Sentiment Classification
* Recent Activity

---

### Check-in Completion Rate

Completion Rate (%) =
Submitted Check-ins / Sent Check-ins × 100

---

### Average Satisfaction Score

Average Stars =
Sum(Stars) / Total Check-ins

---

### Response Time

Average duration between:

Check-in Sent → Check-in Submitted

---

### Client Status Distribution

Categories:

* Happy
* Neutral
* At Risk

Used to monitor overall portfolio health.

---

## Dashboard Components

### Executive Overview

KPIs:

* Total Clients
* Active Clients
* Retention Rate
* Churn Risk Rate
* Average Satisfaction Score

---

### Client Health Dashboard

Visualizations:

* Client Status Breakdown
* At-Risk Client List
* Health Score Ranking
* Recent Activity Timeline

---

### Retention Dashboard

Visualizations:

* Retention Trend
* Monthly Churn Trend
* Check-in Participation Rate
* Engagement Trend

---

### Sentiment Analysis Dashboard

Visualizations:

* Positive Feedback Count
* Neutral Feedback Count
* At-Risk Feedback Count
* Sentiment Trend Over Time

---

### Coach Performance Dashboard

Visualizations:

* Clients per Coach
* Retention by Coach
* Engagement by Coach
* Client Capacity Utilization

---

## SQL Analysis Performed

### Total Clients

```sql
SELECT COUNT(*) AS total_clients
FROM clients;
```

### At-Risk Clients

```sql
SELECT COUNT(*)
FROM clients
WHERE status = 'At Risk';
```

### Average Satisfaction

```sql
SELECT ROUND(AVG(stars),2)
FROM checkins;
```

### Check-in Completion Rate

```sql
SELECT
COUNT(submitted_at) * 100.0 /
COUNT(*) AS completion_rate
FROM checkins;
```

### Retention Status Distribution

```sql
SELECT
status,
COUNT(*) AS clients
FROM clients
GROUP BY status;
```

---

## Business Insights Generated

* Identify customers likely to churn.
* Detect engagement decline before cancellation.
* Measure customer satisfaction trends.
* Monitor retention performance by coach.
* Optimize customer success workflows.
* Improve long-term customer lifetime value.

---

## Tech Stack

### Database

* PostgreSQL
* Supabase

### Querying

* SQL

### Analytics

* KPI Design
* Customer Retention Analysis
* Customer Health Scoring
* Sentiment Monitoring

### Visualization

* Interactive Dashboard
* Real-Time Monitoring

---

## Skills Demonstrated

* Data Modeling
* Relational Database Design
* SQL Querying
* KPI Development
* Dashboard Design
* Customer Analytics
* Churn Analysis
* Retention Analytics
* Business Intelligence
* Data Visualization

---

## Future Enhancements

* Churn Prediction Model
* Customer Lifetime Value (CLV)
* Cohort Retention Analysis
* RFM Segmentation
* Automated Risk Scoring
* Predictive Customer Health Index
* Machine Learning-Based Retention Forecasting

---

## Project Impact

Retainly transforms raw customer feedback into actionable retention insights, enabling businesses to identify churn risks early, improve customer engagement, and increase long-term client retention through data-driven decision making.

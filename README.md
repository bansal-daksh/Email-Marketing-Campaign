# 📧 Email Marketing Campaign Optimization

This project analyzes an email marketing campaign's performance and builds a predictive model to enhance user engagement by increasing click-through rates (CTR). It employs a two-stage machine learning pipeline to predict user interactions with marketing emails.

## 📊 Campaign Overview

- **Total users contacted**: 100,000
- **Users who opened the email**: 10,345 (10.35%)
- **Users who clicked the link**: 2,119 (2.12%)
- **Click-through rate conditional on open**: 20.48%

These metrics indicate that while a smaller segment of users open the emails, those who do are relatively likely to engage further by clicking the provided links.

## 🎯 Objective

The primary goal is to develop a predictive model that identifies users most likely to click on email links. By targeting these users, the campaign can achieve higher engagement rates and optimize resource allocation.

## 🧠 Modeling Approach

A two-stage predictive pipeline is implemented using Random Forest classifiers:

### Stage 1: Predicting Email Opens

- **Target**: `is_email_opened`
- **Features**:
  - Email content and version
  - Hour and weekday of delivery
  - User's country
  - Purchase history

### Stage 2: Predicting Link Clicks

- **Target**: `is_link_clicked`
- **Features**:
  - All features from Stage 1
  - Predicted probability of email being opened from Stage 1

This sequential modeling reflects the real-world dependency where a link click is contingent upon the email being opened.

## 🧪 Evaluation Strategy

To assess the model's effectiveness:

1. **Scoring**: Assign click probability scores to all users.
2. **Targeting**: Select top N% of users with the highest predicted probabilities for future campaigns.
3. **Measurement**: Compare the CTR of the targeted group against the overall CTR to evaluate improvement.

An A/B testing framework can further validate the model's impact by comparing engagement metrics between the targeted group and a control group.

### Technologies Used

- Python
- Required Python libraries:
  - `pandas`
  - `numpy`
  - `scikit-learn`
  - `matplotlib`
  - `seaborn`

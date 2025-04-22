# Email-Marketing-Campaign
1. What percentage of users opened the email and clicked on the link?
----------------------------------------------------------------------
Based on the dataset:

- Total users: 100,000  
- Users who opened the email: 10,345  
- Users who clicked the link in the email: 2,119  

Hence:
- Email Open Rate = 10.35%
- Click-Through Rate (CTR) = 2.12%
- Click Through Rate conditional on open = 20.48%

This shows that while a small portion of users open the email, those who do are fairly likely to click the link.


2. Can we build a model to optimize email sending strategy for more clicks?
---------------------------------------------------------------------------
Yes, I have built a two-stage predictive pipeline:

1. Stage 1: A RandomForestClassifier predicts whether a user will open the email (is_email_opened) based on features like:
   - Email content and version  
   - Hour and weekday of delivery  
   - User country and purchase history  

2. Stage 2: A second RandomForestClassifier uses both the original features and the predicted open status to predict whether the user will click the link (is_link_clicked).

This structure mimics real-world dependencies, as a link click is only possible if the email is opened. The pipeline helps to:
- Estimate the likelihood of both events
- Strategically target users and optimize email timing and content


3. How much would the model improve click-through rate, and how to test it?
---------------------------------------------------------------------------
To estimate improvement:
- Use the model to score all users by predicted probability of clicking.
- Target only top-ranked users (e.g., top 20%) with future campaigns.
- Measure CTR from that group.

A/B Testing Strategy:
- Control Group: Send emails randomly as done currently.
- Test Group: Send emails based on model predictions (targeted users).
- Track CTR across both groups over a fixed time.

If the test group has a significantly higher CTR, it confirms that the model improves performance.

This approach allows for quantitative measurement of model impact and provides a scalable solution for future campaigns.


4. Interesting patterns and insights about campaign performance
---------------------------------------------------------------
Several insights emerged from exploratory analysis and correlation mapping:

Basic CTR Comparison by Email Version:
- Personalized emails outperformed generic ones in terms of engagement.

Regional Differences:
- Users from the US generally engaged more than those from the UK, both in opening and clicking.


Summary
-------
- I built a robust, interpretable machine learning pipeline to model and optimize user engagement with marketing emails.
- The model addresses business constraints, such as needing to open the email before a click can occur.
- An A/B test framework is proposed to validate model efficacy.
- We uncovered useful patterns that can guide segmentation and scheduling strategies.

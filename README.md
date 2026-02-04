<p align="center">
  <img src="img/logistics-ai.png" width="400">
</p>


# Predicting Customer Happiness for a Logistics Startup

## About This Project

A fast growing logistics and delivery startup wants to understand what makes their customers happy or unhappy. By analyzing survey responses, we can identify customers before they churn and take action to retain them.

### The Problem

The company surveyed customers with 6 questions about their experience:

| Question | Description |
|----------|------------------|
| X1 | Was my order delivered on time? |
| X2 | Were the contents as expected? |
| X3 | Could I order everything I wanted? |
| X4 | Did I pay a good price? |
| X5 | Was I satisfied with the courier? |
| X6 | Is the app easy to use? |

**Goal**: Predict whether a customer is happy or unhappy based on their answers.

[View the Jupyter Notebook here](https://nbviewer.org/github/macsiwase/logistics-happy-customers/blob/main/happiness.ipynb)

## Results

### Final Model Identifies 3 Out of 4 Unhappy Customers

The final model, Support Vector Machine (SVM) with polynomial kernel, catches **75% of unhappy customers**, allowing the company to proactively reach out before they churn.

### Only 3 Questions Are Needed
Using feature importance analysis and feature engineering, I found that only **3 of the 6 survey questions** are necessary to maintain prediction performance:

| Keep | Remove |
|------|--------|
| X1 - Delivery on time | X2 - Contents as expected |
| X3 - Found everything wanted | X4 - Good price |
| X6 - App easy to use | X5 - Courier satisfaction |

This means **future surveys can be 50% shorter** without losing predictive power.

### Global Pain Point

**X2 (order contents not as expected)** scored poorly across *all* customers — both happy and unhappy. This is a company-wide issue affecting everyone, not just a predictor of unhappiness.

## My Approach

### Focus on Unhappy Customers

The initial goal was to achieve 73% prediction accuracy. However, I discovered something more valuable for the business:

> **45% of surveyed customers were unhappy.**

This is a significant problem. Rather than optimizing for overall accuracy, I shifted focus to **identifying unhappy customers** because saving a dissatisfied customer has more business impact than correctly labeling an already happy one.

### Methodology

1. **Exploratory Data Analysis**: To understand patterns and figure out which questions showed the biggest differences between happy and unhappy customers.

2. **Built prediction models** using four different machine learning approaches (Logistic Regression, Random Forest, Gradient Boosting, and Support Vector Machine).

3. **Optimized for finding unhappy customers** rather than overall accuracy

4. **Identified which questions matter most** to simplify future surveys

## Recommendations

| Action | Impact |
|--------|--------|
| **Shorten the survey** to 3 questions (X1, X3, X6) | Higher response rates, same insights |
| **Fix the order accuracy problem (X2)** | Improves satisfaction for all customers |


## Technical Summary

- **Model**: Support Vector Machine with polynomial kernel
- **Validation**: Nested cross-validation to ensure reliable performance estimates
- **Key metric**: 75.2% recall for unhappy customers
- **Dataset**: 126 customer survey responses

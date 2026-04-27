# College Earnings Regression Analysis

## Overview

This project looks at how college cost, student composition, and institutional characteristics relate to long-term earnings. We used the College Scorecard dataset to analyze median earnings of students 10 years after entering college and tried to understand what actually drives those outcomes.

A common assumption is that more expensive schools lead to higher earnings. We wanted to test that idea while accounting for things like student quality and socioeconomic background.

## Authors

Jackson Justice
Trieste Cerny

## Data

We used the College Scorecard Institution-Level dataset from the U.S. Department of Education. Each observation represents a college or university in the United States.

Key variables:

* `MD_EARN_WNE_P10`: Median earnings 10 years after entry (response)
* `NET_PRICE`: Average net cost of attendance
* `PCTPELL`: Percentage of students receiving Pell Grants
* `SAT_AVG`: Average SAT score (proxy for student quality)
* `UGDS`: Undergraduate enrollment (school size)
* `CONTROL`: Institution type (public, private nonprofit, for-profit)

## What We Did

### Data Cleaning

* Converted "NULL" values to NA and handled missing data
* Combined public/private tuition into a single net price variable
* Created SAT average from reading and math scores
* Log-transformed earnings to handle skewness

### Exploratory Analysis

* Looked at distributions and relationships between variables
* Found earnings were strongly right-skewed
* Observed:

  * Positive relationship between tuition and earnings
  * Negative relationship between Pell Grant share and earnings
  * High variability across institutions

### Modeling

We built several regression models, starting simple and adding complexity:

* Baseline: earnings vs net price
* Added socioeconomic composition (Pell %)
* Added institution type
* Tested interaction effects
* Added controls (SAT, enrollment, admission rate)

We compared models using:

* Adjusted ( R^2 )
* AIC
* 10-fold cross-validation

### Final Model

The final model included:

* Net price
* Pell Grant percentage
* Average SAT score
* Enrollment size
* Institution type

## Key Findings

* **SAT score was the strongest predictor** of earnings
  → Student academic preparation matters more than cost

* **Pell Grant percentage had a negative relationship** with earnings
  → Socioeconomic composition plays a major role

* **Net price was positively associated with earnings**, but the effect was small
  → Higher cost schools don’t necessarily cause higher earnings

* **Institution type was not significant** after controlling for other variables

Overall, a lot of what looks like a “tuition effect” is really explained by the types of students schools enroll.

## Takeaways

* Paying more for college doesn’t automatically mean better financial outcomes
* Student characteristics matter more than institutional cost
* Observational data makes it hard to claim causality, but strong patterns still show up

## Tools Used

* R
* tidyverse
* ggplot2
* caret (cross-validation)

## Files

* `Stat-330-Final-Project.qmd` – full analysis
* `stat330-college-earnings-proposal.qmd` – initial proposal
* PDF outputs and figures

## Notes

This project was originally completed as part of STAT 330 at BYU, but has been cleaned up and organized here for portfolio purposes.

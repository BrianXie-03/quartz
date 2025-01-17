---
title: Course Introduction
tags:
- cmsc320
---

# Introduction to Data Science

Data science is an interdisciplinary field focused on discovering patterns and describing relations using data, consisting of computational and statistical techniques to address or gain [managerial or scientific] insight.

The process consists of taking raw data and turn it into insights about the world or predictions about the future.

## Big Data and Data Science

Big data describes datasets with large volume, created and updated with high velocity that have variety in structure and format.


| Term | Definition |
| -------------------- | -------------------- |
| **Volume** | The amount of data from myriad sources |
| **Velocity** | The speed at which big data is generated |
| **Variety** | The types of data (structured, semi-structured, unstructured) |

Examples of raw data consists of: 
- Medical records
- Patient demographics
- Lab results

Insights and Predictions: Identifies patterns in patient data to
- predict disease outbreak
- optimize treatment plans
- provide insights for medical research

## The Data Lifecycle

```mermaid
flowchart LR
  A(Data Collection) --> B(Data Processing)
  B --> C(Exploratory Analysis & Data visualization)
  C --> D(Analysis, Hypothesis testing & Machine Learning)
  D --> E(Insight & Policy Decision)
```

**Note:** Data science is not a strictly one-way linear process; it's dynamic, iterative, and adaptive (revisit previous steps along the way

### Before all: Define Problem Statement

What problem are you going to solve?
* Well-defined problem statement to collect and determine what information needed

### Collect Data

Data collection is a systematic approach to gather relevant information from a variety of sources.
- Gather from external sources
- Gather from existing company databases
- Gather by tools created by you

#### Methods

**2 Types of Data Collection Methods**

| | Primary Data Collection | Secondary Data Collection |
| -- | -- | -- |
| **Examples:** |  Web Analyics | Publishing Articles|
| | Surveys | Blogs |
| | Listening Labs | White Papers |
| | |
| **Situation:** | Unique problem and no related research  | Data is readily available |
| | | 
| **Solution:** | Collect new data (primary)  | Use the data (secondary)
| | |
| **Different Method:** | Surveys | Internet |
| | Interviews | News articles |
| | Monitoring | Govt. Census |
| | | Magazines |
| | | |
| **Note:** | Time consuming| Less time consuming |  

### Data Processing

Sanity checks on data, ensuring that data are usable
>In a collection of data on test scores with N/A responses, replace N/A entries with a neutral value, 0, and filling missing score with the correct value.

### Exploratory Analysis & Data Visualization

Extract useful insights from the data, understanding patterns, and setting the stage for effective model building and decision-making.  
**Note:** Skipping this step may lead to inaccurate models as well as insignificant variables in your models.

**Exploratory Analysis:** Find correlation between study hours and scores by calculating the average score, find the range of scores, and notice that some students scored exceptionally well.

**Data Visualization:** Visually show the relationship between study hours and average scores for different groups of students in order to revevla that students who study more tend to have higher average scores.

### Analysis, hypothess testing & Machine Learning

Build a model and training the model.
>Example: making a machine learning model that predicts a student's test score based on their study hours, while training the model.

### Insight & Policy Decision

- Deriving Insights and make policy decisions if needed.
- Present the results from your analysis to the stakeholders.
- Convince people: explain the specific conclusions and critical findings, probably in understandable manner.

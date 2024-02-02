---
title: Experimental Design
tags:
- cmsc320
- wip
---

# Experimental Design

Otherwise known as the science and subfield of statistics about how to collect data efficiently.

**Definition:** Process of planning, carrying out, and analyzing experiments to<ins> test a hypothesis

Experimental Design is a crucial aspect of data science that focuses on <ins> planning</ins> and <ins> conducting</ins> *experiments* to gather **meaningful data.**
* Involves making decisions about **how** to **collect**, **manipulate**, and **analyze data** to answer specific research questions or test hypothesis.
> **Goal:** Ensure collected data is reliable, unbiased, and leads to valid conclusions, while minimizing the time, costs, and mistakes.

Steps in Experimental Design:
1. Define the Problem or Research Question aims to address
   * Asking the right questions before solving a DS problem is a great start, be specific.
2. Identify the variable(s) including potential confounding variables and the population/sample you will study.
3. Formulate hypothesis
4. Develop a detailed plan for data collection, ensuring representativeness when using a sample.
5. Select Data Collection Methods
6. Collect Data

**Note:** For most data science applications, ultimately, comes down to predicting the future.  
We answer the question, "Given some set of options, which option **maximizes** my **optimization criteria**"
> Identify the option/decision that maximizes or optimizes the desired outcomes based on these predefined criteria.

## An Example of Experimental Design
>[!example]- Online Rail
> **Scenerio:** Lets say  you're a data scientists working for an online retailer, and you want to test whether changing the color of the "Buy Now" button on your website affects the click-through rate (CTR - the percentage of users who clicked on the ad after seeing it).  
>**Problem:** FInd which version of the "Buy Now" (option A (default) or option B (red)) is more likely to maximize the CTR.  
>**Optimiziation Criteria:** we want to select the ad option with button "buy now" the leads to higher CTR.  
>**Question: How can we set up an experiment to collect data in this case?**
> Data Size/Sample: Number of website visitors
> | Control Group  | Treatment Group |
> |--|--|
> | Original blue button | new red button |
> | No changes | Change you want to test |
>
> **Collect** data on the click-through rates for both groups over a specific period.  
> **Compare** the click-through rates (CTR) between the groups after the experiment
> **Check** if there's a signfiicant difference [wip], We can infer that the change in button color influenced the click-through rate.  
> **Variables:**  
>* Click Through rate -> dependent variable (measure)
>* Color -> independent variable (manipulate)

## Variables & Population/Sample

Once the problem is defined, identify the variable(s) of interest that are relevant to your research question.
Also, specify the population and sample that your study will focus on.

| Term | Definition |
| -- | -- |
| Variable | Any caracteristic that is recorded for subjects to study |
| Population | The entire group that we want to learn about |
| Sample | Smaller group from the population that we study to draw conclusion |

| Variable Types | Definition |
| -- | -- |
| Independent Variable | Factors/causes that may influence the outcome |
| Dependent Variable | Outcome of interest (what we measure)
> Note: While independent variables product dependent variables, it is also true that multiple indepndent variables may influence one another. This can complicate the intepretation of results (challenging to determine the individual impact of each independent variable to dependent variable. We want to minimize the presence of **correlated** variables.

## Hypothesis

Definition: The question/assumption statement in your experiment that you want to test.
* A testable explanation/statement that addresses the question.
* Represents an educated guess as to the relationship between variables and outcomes of the experiment.
* Experiments or Observations are conducted to see whether the predictions are correct. If confirmed, the hypothesis is supported. If not, it may be time for a new hypothesis.

## Confounder Variables

Before collecting data to test your hypothesis, you first have to consider the probelms that can cause errors in your result, one of them being a confounder.
Analyze if any other variables (beyond the ones you intended to manipulate or measure) could have impacted/influenced your results (Note that, if is true, we may need to redesign the experiment for ensuring more accurate and reliable conclusions).

**Extraneous variables** that may affect the relationships between dependent and independent variables.
* May not be the focus of the study but can impact the results by influencce the dependent variable
* An additional factor that is not controlled for but could potentially influence the outcomes.

A confounder can lead to incorrect conclusions about the true effect of the independent variables on the dependent variables.

## Dealing with Confounder

Considering and addressing confounders in experimental design is crucial to ensure accurate results, preventing extenal factors from influencing outcomes, and ensuring the correct design of experiments.
There are three ways you can deal with confounders:
* Control
  * Manage or eliminate the impact of confounding variables
    * Control Groups
    * Treatment Groups
* Randomization
* Repliciation

>[!example]- Example One
>"If the amount of study time is increased, then exam scores will also increase.
> WE can measure the prior knowledge of each individual; to see the effects/impacct of prior knowledge on  exam score.
> Control -> Participants with no prior knowledge.
>Treatment -> Participants with a range of prior knowledge levels.
>Comparison: Results are compared to determine whether the no prior knowledge group differs in exam score from the group of having varying levels of prior knowledge

[!example]- Example Two[wip]

[wip]

## Methods for Collecting Data

Below are some common methods\ways to collecct data if pre-existing datasets are not available.
* Observational studies - observe and record data (variables) without intervening or manipulating results (Observe; dont change anything intentionally).
* surveys - Collect information through structured questionnaies or interviews
* experiments - we actively change something to see what happens
* simulations - Create artificial scenarios to model real-world situations for data collection

## Observational Studies

* Cross Sectional Studies - collects data from many different individuals at one specific singel point of time
* Retrospective (case control) studies - looking backwars at studies of events in the past to examine the relationship between the exposure and the outcome. 
* Prospective (longitudinal or cohort) studies - Researches follow and observe a group(s) of people (called a cohort) closeely - over a period of time, collecting data on their exposure to a factor of interest (observe changes; identify potential causes).

Surveys A survey is used to investigate characteristics of a population. It is frequently used when the subjects are people, and questions are asked of them.
* When designing a survey, you must be very careful of wording (and somtimes ordering) the equestions so that the results are not biased

## Experiment

In an experiment, a researcher assigns a treatment and observes te response.
* Observe effects on subjects after the application of some treatment
  * Might want to compare a treatement versus a control or multiple treatements
* The more variables yo u can control for, the better your expeiremtn

**Placebo Effect:** Belief  in treatment leads to feeling better even without actual treatement
	  * A person believes psychologically that a certain treatment is positively affecting them, even though no traetement was given at all.

**Blinding:** (Subjects would  be blinded) when the people involved in an experiment don't know who's getting the real treatement and who's not. Prevent Biases. It is a technique used to make the subects "blind" to which treatment (or plaacebo) they are given.
* Singel-blinding is when either the participants or the researches don't know* Double-blinding is when both don't know 
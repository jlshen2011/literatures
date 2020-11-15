# Causal Inference Methods


## Causal inference fundamentals

### Potential, actual, and counterfactual outcomes
Each unit of observational data has either received the treatment or not. That means one of the potential outcomes is an actual outcome (i.e., something that we see in the data). The other potential outcome is a counterfactual one. It is the outcome that would have occurred if something different had happened. If a unit was treated, we observe the outcome for being treated, which becomes the actual outcome. But we cannot observe the outcome if the unit didn’t get treated, which becomes the counterfactual outcome.

What that means is that the question of causality comes down to comparing actual outcomes with counterfactual outcomes; in other words, what would have happened if things had been different. Causal inference methods employ various assumptions to let us estimate the unobservable counterfactual outcome. By doing this, we can use them to make the appropriate comparison and estimate the treatment effect.

### Confounders
Causal effects are changes in outcomes due to changes in treatments, holding all other variables constant. Basically, if something other than the treatment differs between the treated and untreated groups, we cannot conclusively say that any difference observed in the outcome is due solely to the treatment. This “mixing of effects” is a confounding effect. A confounding variable (also known as confounder) is a variable that influences both the treatment and outcome, causing a spurious association. Any variable that differs between the treatment and control groups could potentially be a confounding variable if it also influences the outcome. A correlation between having the treatment and having a good outcome, for example, could be due to confounders.

### Selection bias
Selection bias is a phenomenon in which the distribution of the observed group is not representative of the group we are interested in. 

### Ignorability
This assumption can sometimes be referred to as the “no unmeasured confounders assumption”. (See A Survey on Causal Inference.) Given pre-treatment covariates X, treatment assignment is independent from the potential outcomes:
Y ⁰, Y ¹ ⫫ T |X
For example, suppose X is a single variable (age) that can take the values “younger” or “older”. Older people are more likely to get treatment T = 1. Older people are also more likely to have the outcome “hip fracture,” regardless of treatment. Thus, Y ⁰ and Y ¹ are not independent from T (marginally). However, within levels of X, treatment might be randomly assigned.


### Types of treatment effects
Average treatment effect (ATE): At the population level, the treatment effect is called the average treatment effect (ATE),

Average treatment effect on the treated (ATT): For the treated group, the treatment effect is called the average treatment effect on the treated group (ATT)

Conditional average treatment effect (CATE): At the subgroup level, the treatment effect is called conditional average treatment effect (CATE), which is defined as:


Individual treatment effect (ITE): At the individual level, the treatment effect is called individual treatment effect 


## Controlled experiments, A/B testng

one applies a “treatment” to
some set of “subjects” and observes some “outcomes.” The
outcomes for the treated subjects can be compared with the
outcomes for the untreated subjects (the control group) to determine the causal effect of the treatment on the subjects.

However, experiments are often costly and in many important
cases are not feasible.

## Train-test-treat-compare, Estimate treatment effect on the treated

TTTC is a generalization of the classic treatment–control
approach to experimentation. In that model, the control group provides an estimate of the counterfactual, which is the gold
standard for causal inference. However, even if we do not have a
true control group, we still may be able to develop a predictive
model of the counterfactual using other methods. 

In TTTC, the model is estimated during the training
period and its predictive performance is assessed during the test period. The
extrapolation of the model during the treat period (red line) serves as a
counterfactual. This counterfactual is compared with the actual outcome (black
line), and the difference is the estimated treatment effect. When the treatment is ended, the outcome returns to something close to the original level.

We have seen that causal inference involves comparing actual
outcomes to counterfactual outcomes. The standard approach is
typically a cross-section model to compare treated subjects to
untreated subjects. In this case, the counterfactual is a prediction
of the outcome for those treated if they had not been treated,
which is typically based on the outcome for the control group
(sometimes with an adjustment for other factors).


 RCT is the traditional gold standard that enables unbiased estimation of treatment effects. However, in observational studies, the possibility of bias arises because a difference in the treatment outcome may be caused by a factor that predicts treatment rather than the treatment itself, known as confoundedness. As a result, it’s desirable to replicate a randomized experiment as closely as possible through various strategies.


 We have carried out separate research to estimate the delay and decay of treatment effects over time, which we won’t discuss in this article due to length constraints. If you would like to include repeated observations of outcome over time into your causal research design, depending on whether you have control time series data from a non-treated unit, you can consider approaches like difference-in-difference and interrupted time series synthetic control, among others. Uber has also discussed various causal inference methods for time series observations in their post.



 

## Difference in differences

Difference in Differences. In this case, we have two groups, the treated and the untreated, and two time periods, before treatment and after treatment. We also have a number of predictors that may affect the observed values of the outcome for each group. 


The goal is to estimate a predictive model of what the outcome would be for the treated group if it were not treated. To accomplish this goal, one can use a model, possibly nonlinear, of the observed outcomes of the untreated group in the posttreatment period.

 There, we
built a predictive model for the outcome when no treatment was
applied. Here, we can build a predictive model for those units
where no treatment was applied. We then apply this model to the
treated units to get the counterfactual and then compare the
actual outcome to the counterfactual.


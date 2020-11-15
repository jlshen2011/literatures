# Causal Inference


## Concepts

### Counterfactual outcomes
Counterfactual outcome is the outcome that would have occurred if something different had happened. If a unit was treated, we observe the outcome for being treated, which becomes the actual outcome. But we cannot observe the outcome if the unit didn’t get treated, which becomes the counterfactual outcome.

Causal inference methods employ various assumptions to let us estimate the unobservable counterfactual outcome. By doing this, we can use them to make the appropriate comparison and estimate the treatment effect.

### Confounders
Causal effects are changes in outcomes due to changes in treatments, holding all other variables constant. A confounding variable is a variable that influences both the treatment and outcome, causing a spurious association. Any variable that differs between the treatment and control groups could potentially be a confounding variable if it also influences the outcome. A correlation between having the treatment and having a good outcome, for example, could be due to confounders.

### Selection bias
Selection bias is a phenomenon in which the distribution of the observed group is not representative of the group we are interested in. Confounders usually affect treatment choices among units, which leads to the selection bias. 

### Ignorability
Ignorability refers to that given pre-treatment covariates, treatment assignment is independent from the potential outcomes. This is one of the fundamental assumptions for many causal inferecnce methods

### Types of treatment effects
The objective for causal inference is to estimate the treatment effect from the observational data. The treatment effect can be measured at the population, treated group, subgroup, and individual levels: 
* Average treatment effect (ATE): At the population level, the treatment effect is called the average treatment effect (ATE).
* Average treatment effect on the treated (ATT): For the treated group, the treatment effect is called the average treatment effect on the treated group (ATT).
* Conditional average treatment effect (CATE): At the subgroup level, the treatment effect is called conditional average treatment effect (CATE).
* Individual treatment effect (ITE): At the individual level, the treatment effect is called individual treatment effect.


## Randomized controlled trials

This the gold standard method. However, experiments are often costly and in many important cases are not feasible. In observational studies, the possibility of bias arises because a difference in the treatment outcome may be caused by a factor that predicts treatment rather than the treatment itself. 


## Methods for repeated observations of outcomes over time

### Diffference-in-differences

the difference-in-differences analysis, looks at the difference in outcomes between those who are treated and those who are not treated before and after the treatment of interest takes place.25,26  The assumption here is that if the treatment influences the outcome of interest, then there should be a change in the difference between those who are treated and those who are not, from before to after the intervention. A typical use case for these types of methods is a marketing campaign or a new product feature that is launched in a particular city.

We have seen that causal inference involves comparing actual
outcomes to counterfactual outcomes. The standard approach is
typically a cross-section model to compare treated subjects to
untreated subjects. In this case, the counterfactual is a prediction
of the outcome for those treated if they had not been treated,
which is typically based on the outcome for the control group
(sometimes with an adjustment for other factors).

Difference in Differences. In this case, we have two groups, the treated and the untreated, and two time periods, before treatment and after treatment. We also have a number of predictors that may affect the observed values of the outcome for each group. 


The goal is to estimate a predictive model of what the outcome would be for the treated group if it were not treated. To accomplish this goal, one can use a model, possibly nonlinear, of the observed outcomes of the untreated group in the posttreatment period.

 There, we
built a predictive model for the outcome when no treatment was
applied. Here, we can build a predictive model for those units
where no treatment was applied. We then apply this model to the
treated units to get the counterfactual and then compare the
actual outcome to the counterfactual.


### Train-test-treat-compare, Estimate treatment effect on the treated

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


## Methods for one snapshot of the outcome

### Propensity matching

### Inverse propensity weighting

### Doubly robust learning

### Stratification

To adjust selection bias, stratification (also known as subclassification or blocking) splits the entire group into homogeneous subgroups, where within each subgroup, ideally the treated group and the control group are similar under certain measurements over covariates. Then the treatment effect within each subgroup can be calculated using a method first developed on RCT data. With the CATE of each subgroup, the treatment effect over the interested group can be obtained by combining the CATEs of subgroups belonging to that group. 

### Meta-learning methods

Meta-learners can take advantage of any supervised learning or regression methods in machine learning and statistics to estimate a treatment effect, such as the conditional average treatment effect (CATE) function.

#### S-learner
This algorithm estimates the target variable using all the covariate features and treatment indicator, without giving the treatment indicator any special role. The estimate is done using a single algorithm estimator, hence the name S-learner. The estimation consists of two stages. First, a predictive model is built using the outcome as a target and control for both treatment and other features. Then the difference is calculated among the estimated values when the treatment assignment indicator is changed from control to treatment, with all other features held fixed. The difference among the estimated values is the CATE for an individual unit.


#### T-learner
This algorithm estimates the response functions separately for the treatment and control populations. First, it uses base learners to estimate the conditional expectations of the outcomes separately for units under control and those under treatment. Second, it takes the difference between these estimates. We refer to the general mechanism of estimating the response functions separately as the T-learner, “T” being short for “two.”

#### X-learner

#### R-learner

## References
* [A comparison of approaches to advertising measurement: evidence from big field experiments at Facebook](https://www.kellogg.northwestern.edu/faculty/gordon_b/files/fb_comparison.pdf)
* [Causal inference (Part 1 of 3): Understanding the fundamentals](https://medium.com/data-science-at-microsoft/causal-inference-part-1-of-3-understanding-the-fundamentals-816f4723e54a)
* [Causal inference (Part 2 of 3): Selecting algorithms](https://medium.com/data-science-at-microsoft/causal-inference-part-2-of-3-selecting-algorithms-a966f8228a2d)
* [Causal inference in economics and marketing](https://www.pnas.org/content/pnas/113/27/7310.full.pdf)
* [Evaluating online ad campaigns in a pipeline: causal models at scale](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/36552.pdf)
* [Using causal inference to improve the Uber user experience](https://eng.uber.com/causal-inference-at-uber/)


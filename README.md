These are the R notebooks for the experiments conducted during my internship at the Max Planck Institute for Software Systems (MPI-SWS), at Dr. Manuel Gomez Rodriguez's Human-Centric Machine Learning Group.

## Background: Threshold Test

Individuals have multiple socially-salient attributes (traits) that define them, some of them are observable by others. Decision makers often judge individuals based on these observed traits, as well as the (un)conscious biases that they may harbour in favour of, or against, certain traits. Usually more than one trait influences the final decision taken, that is, it is an intersection of traits of the individual which may determine the decisions taken on them.

Thus, it may be the case that a decision maker employs different metrics for measuring the worthiness of different individuals when assigning an outcome to them.

For binary decisions, we can consider the metric to be a numerical threshold for assigning the outcome "yes" to an individual. We wish to infer the different threshold values that are employed for different subsets of traits (or see whether such a relation even exists).

This involves the following: 
    1. identifying the subset of traits that plays the most significant role in determining the decision taken. (if such a unique subset exists)
    2. identifying the threshold employed for that subset of socially-salient attributes.

## Problem Formulation
Given:

    1. Dataset of socially-salient attributes of $N$ individuals, $\mathcal{X}=\{\mathbf{x}_{i}\}_{i=1}^{N}$, each $\mathbf{x}_{i}$ is a vector of $K$ socially-salient attributes, eg. $$\mathbf{x}_{i}=(\underbrace{x_{1}}_{\text{race }} \underbrace{x_{2}}_{\substack{\text { gender }}} \cdots \underbrace{x_{k}}_{\substack{\text { income } \\ \text { bracket }}})$$

    2. The final level decision taken by the decision maker, $\mathcal{D}=\left\{d_{i}\right\}_{i=1}^{N}$,  $d_{i}\in \{0,1\}$.
    
    3. The true label of the individual (true category of the individual, observed if the decision taken was $=1$), $\mathcal{Y}=\left\{y_{i}\right\}_{i=1}^{N}$,  $y_{i}\in \{0,1\}$.

Our goal is to cluster the data according to (1.), (2.) and (3.), using the Dirichlet process mixture model (DPMM), a Bayesian nonparametric model for clustering, and to infer the true model parameters.
For this, we use the R library ```dirichletprocess```.


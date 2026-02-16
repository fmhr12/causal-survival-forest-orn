# Causal Survival Forest Analysis for Osteoradionecrosis (ORN)

## Overview
This repository contains the analytical code used to estimate the **Heterogeneous Treatment Effects (HTE)** of tooth extraction prior to radiotherapy on the incidence of Osteoradionecrosis (ORN).

The analysis utilizes **Causal Survival Forests (CSF)** via the `grf` package to estimate conditional average treatment effects (CATE) based on Restricted Mean Survival Time (RMST). Unlike standard Cox regression models, this machine learning approach allows for the detection of non-linear interactions and identifies specific patient subgroups that benefit most (or least) from the intervention.

## Key Features
* **Causal Survival Forest (CSF):** Uses "honest" splitting and random forests to estimate the causal effect of tooth extraction on ORN-free survival.
* **Restricted Mean Survival Time (RMST):** The treatment effect is measured as the difference in expected survival time up to a 60-month horizon, avoiding the strict proportional hazards assumption.
* **Strict Cross-Validation:** Implements a repeated k-fold cross-fitting procedure to generate unbiased out-of-sample predictions for CATE and Doubly Robust (DR) scores.
* **Policy Evaluation:** Computes the Rank-Weighted Average Treatment Effect (RATE) and plots the Targeting Operator Characteristic (TOC) curve to evaluate how well the model identifies high-risk subgroups.
* **Heterogeneity Analysis:** Uses Best Linear Projection (BLP) to test if treatment effects vary significantly across covariates.

## Prerequisites
The code is written in **R**. The following libraries are required:

* `grf` (Generalized Random Forests)
* `readxl` (Data import)
* `ggplot2` (Visualization)
* `dplyr` (Data manipulation)
* `pbapply` (Progress bar for loops)
* `caret` (Stratified sampling)

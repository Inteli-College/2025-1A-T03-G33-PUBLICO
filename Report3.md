# Inteli - Instituto de Tecnologia e Liderança 

<p align="center">
<a href= "https://www.inteli.edu.br/"><img src="https://github.com/2023M7T3-Inteli/Projeto3/blob/main/assets/imagens/Inteli.png" alt="Inteli - Instituto de Tecnologia e Liderança" border="0" width=40% height=40%></a>
</p>

# Public Report - Rede Gazeta

**Group:** Izabella Faria, Livia Coutinho,  Mariana de Paula and Mateus Neves <br>
**Partner:** Rede Gazeta <br>
**Track:** Corporate 


<br>

# Summary

- [1. Introduction](#1-introduction)
  - [1.1 Project Objective](#11-project-objective)
  - [1.2 Problem Contextualization](#12-problem-contextualization)
  - [1.3 Approach and Methodology Used](#13-approach-and-methodology-used)
- [2. Project Planning and Structure](#2-project-planning-and-structure)
  - [2.1 Team and Roles](#21-team-and-roles)
  - [2.2 Sprint Roadmap](#22-sprint-roadmap)
  - [2.3 Alignment with the Partner](#23-alignment-with-the-partner)
- [3. Data Preparation and Exploratory Analysis](#3-data-preparation-and-exploratory-analysis)
  - [3.1 Data Cleaning and Feature Engineering](#31-data-cleaning-and-feature-engineering)
  - [3.2 Dataset Description](#32-dataset-description)
- [4. Predictive Modeling](#4-predictive-modeling)
  - [4.1 Price Acceptance Model](#41-price-acceptance-model)
  - [4.2 Occupancy Estimation Model](#42-occupancy-estimation-model)
  - [4.3 Model Interpretation and Business Alignment](#43-model-interpretation-and-business-alignment)
  - [4.4 Elasticity Modeling - Price Sensitivity and Optimal Range Estimation](#44-elasticity-modeling---price-sensitivity-and-optimal-range-estimation)
- [5. Dynamic Pricing Strategy](#5-dynamic-pricing-strategy)
  - [5.1 Price Suggestion Logic](#51-price-suggestion-logic)
  - [5.2 Adjustment Rules and Thresholds](#52-adjustment-rules-and-thresholds)
  - [5.3 Impact Simulation](#53-impact-simulation)
- [6. Evaluation and Results](#6-evaluation-and-results)
  - [6.1 Metrics Overview](#61-metrics-overview)
  - [6.2 Business Impact](#62-business-impact)
  - [6.3 Lessons Learned](#63-lessons-learned)
- [7. Next Steps – Transition to Module 4](#7-next-steps--transition-to-module-4)


# 1. Introduction

Rede Gazeta, one of the leading communication groups in Espírito Santo, faces significant challenges in pricing its advertising spaces in the radio environment. The current model shows little flexibility to accommodate seasonal variations, demand fluctuations, and external factors that directly influence inventory occupancy. This limitation can lead to revenue losses, idle media spaces, and difficulty in offering more competitive commercial conditions for different advertiser profiles.

## 1.1 Project Objective
The Dynamic Pricing with AI project, developed in partnership with Rede Gazeta, aims to create an intelligent and automated solution for dynamic pricing of advertising spaces on the group's radio stations. The proposal involves using predictive models based on machine learning to adjust advertising insertion prices in real-time, taking into account factors such as occupancy history, seasonality, projected demand, and external market variables.

With this, it is expected not only to optimize the occupancy of the advertising inventory but also to provide greater agility to the commercial team, offer more competitive conditions to advertisers, and increase the revenue of Rede Gazeta. In the long term, the solution may also be integrated with other channels of the group, such as television, newspapers, and digital media, expanding the strategic impact of the proposal.

## 1.2 Problem Contextualization
Traditional pricing of media spaces at Rede Gazeta is predominantly fixed, not taking into account demand fluctuations over time, specific seasonality (such as high season on the coast or elections), or changes in advertiser behavior. This rigidity negatively impacts the profitability of the operation, as it results in idle spaces during periods of low demand and undervaluation during periods of high demand.

At the same time, there is a cultural and operational challenge: many advertisers and team members are accustomed to traditional negotiation practices and may resist the adoption of automated technologies. This resistance, coupled with the technological complexity of the proposed solution, required a period fully dedicated to a deep understanding of the business, involved users, and the commercial rules governing the current company model.

## 1.3 Approach and Methodology Used
In continuity with the business understanding and technical foundation laid out in Modules 1 and 2, Module 3 emphasized the practical construction of data-driven solutions, focusing on the modeling, evaluation, and visualization of a dynamic pricing system.

The first sprint concentrated on the planning and refinement of the module's scope. Roles were reaffirmed, the roadmap was reviewed, and tasks were aligned with the expected deliverables. From the second sprint onward, the team began the development of distinct pricing and occupancy models, utilizing historical data from Rede Gazeta's commercial operation.

The module began with data preparation and exploratory analysis, leading to the development of classification models capable of predicting the acceptance or rejection of proposed advertising prices. The results provided actionable insights for the sales team, allowing price suggestions to be guided by historical behavior and improving negotiation strategy.

The combination of machine learning, business alignment, and visual delivery positioned the system as a powerful tool to enhance decision-making. With a functional pipeline in place, the project now transitions to Module 4, where efforts will focus on system refinement, interface enhancement, and full integration into Rede Gazeta’s operational workflow.

# 2. Project Planning and Structure

## 2.1 Team and Roles
The project was developed by a team of four students from the Institute of Technology and Leadership (Inteli): Izabella Faria, Mariana Silva, Livia Coutinho, and Mateus Neves. Although the Scrum methodology was adopted as the organizational base, with roles such as Product Owner, Scrum Master, and Developers initially defined, the team adopted a collaborative approach in which all members actively participated in the construction of strategic artifacts, with a clear and balanced division of responsibilities.

## 2.2 Sprint Roadmap
The development of Module 3 was divided into five bi-weekly sprints, organized as follows:

- **Sprint 1**: Planning and structuring, including team role definition, project roadmap review, detailed plan setup, and organization of tasks for subsequent sprints.
- **Sprint 2**: Initial development and modeling, kicking off multiple pricing models and defining the success metrics for evaluation.
- **Sprint 3**: Model analysis and selection, with comparative evaluation of approaches and selection of the best-performing model to advance to optimization.
- **Sprint 4**: Optimization and dashboard initiation, focusing on hyperparameter tuning to refine accuracy and starting the first version of the visualization dashboard.
- **Sprint 5**: Final dashboard and reports, completing the initial dashboard to ensure result visibility and suggested prices, and preparing performance and progress reports for the module.

## 2.3 Alignment with the Partner
Throughout the third module, the team continued close coordination with the Rede Gazeta representative to support ongoing data receipt, interpretation, and validation. This collaboration remained vital for correctly understanding dataset structure and semantics, with timely clarifications on business rules, internal data flows, and fields critical to the pricing strategy. The continuous interaction enabled the team to validate assumptions, resolve questions about data formats and provenance, and refine processing steps to reflect real operational constraints. Building on Module 2, these touchpoints were especially important in Module 3 to compare and select pricing models, perform hyperparameter optimization, and ensure that the first version of the visualization dashboard accurately surfaced results and recommended prices for stakeholders.

# 3. Data Preparation and Exploratory Analysis

## 3.1 Data Cleaning and Feature Engineering
In the data cleaning process, all column names are converted to snake_case and duplicates are removed. Next, the airing dates are converted to datetime objects, enriched with year, month, and weekday attributes, and only then are the original date columns dropped to avoid type conflicts. Financial values undergo regional formatting cleanup (removal of thousands separators and swapping commas for periods), imputation of missing values using the median, and standardization via z-score. Finally, textual fields such as market, format, program, client, executive, and status are normalized—with removal of diacritics, conversion to lowercase, and trimming of whitespace—and categorical variables receive one-hot encoding in a sparse format.

## 3.2 Dataset Description

### Original Variables
- `data` → Date the ad placement aired (format `YYYY-MM-DD`).
- `rp` → Reference/record number of the placement in the commercial system.
- `praça` → Identification of the radio station and region where it aired (e.g., Vitória, Colatina, Linhares).
- `formato` → Type of advertising placement (spot, live endorsement, jingle, rotation, etc.).
- `dur.` → Duration of the commercial in seconds.
- `título` → Name of the campaign/creative aired.
- `valor_tabela` → Full list price (official rate card) of the placement.
- `valor_negociado_bruto` → Gross amount agreed after negotiation, before discounts/allowances.
- `valor_liquido` → Amount actually paid by the client (final price).
- `situação` → Status of the placement (e.g., Aired, Canceled).
- `publicidade` → Binary flag (1 = advertising, 0 = institutional/PSA).

### Temporal Variables
- `ano` → Year of the placement (extracted from `data`).
- `mes` → Month of the placement (1–12).
- `dia_semana` → Day of the week (0=Monday to 6=Sunday).
- `trimestre` → Quarter of the year (1 to 4).

### Time Variables Derived from Format
- `periodo_format` → Period category extracted from the format (morning, afternoon, night, overnight, undefined).
- `faixa_06_22` → Binary flag (1 if the placement falls within 06:00–22:00, 0 otherwise).
- `faixa_07_19` → Binary flag (1 if the placement falls within 07:00–19:00, 0 otherwise).
- `faixa_22_06` → Binary flag (1 if the placement falls within 22:00–06:00, 0 otherwise).

### Business Variables derived
- `preco_por_segundo` → Price normalized by time: `preco_por_segundo = valor_liquido / dur`.
- `desconto` → Average discount percentage granted: `desconto = (valor_tabela – valor_liquido) / valor_tabela`.
- `bruto_liquido_diff` → Difference between gross and net amounts: `bruto_liquido_diff = valor_negociado_bruto – valor_liquido`.
- `zerado` → Binary flag (1 if `valor_liquido == 0`, 0 otherwise).

### Categorical Variables Encoded by Mean (Target Encoding)
- `cliente_mean_valor` → Historical mean of `valor_liquido` by client.
- `programa_mean_valor` → Historical mean of `valor_liquido` by program.
- `executivo_mean_valor` → Historical mean of `valor_liquido` by sales executive.

# 4. Predictive Modeling

## 4.1 Price Acceptance Model
Description and objective. We attempted to train a classifier (LightGBM) to predict whether a price would be accepted (occupied = 1) or not (0). Since the dataset contains only aired insertions (class 1), the model yielded trivial metrics (accuracy/precision/recall = 100%, ROC-AUC = NaN, confusion matrix with only class 1). Conclusion: there is still no contrast to learn acceptance; the objective remains to predict the ex-ante probability of acceptance, but it depends on collecting real negatives (not sold, canceled, refused).

Most relevant features (ex-ante planning). Structural (format, market/station, duration), seasonal (month, day of week, time band), and client/program/executive clusters—exactly block C, which has already shown strong gains in the price models. To avoid leakage, do not use negotiation/history variables in ex-ante training.

Performance metrics (when 0/1 are available). Primary: ROC-AUC, PR-AUC (better with imbalance), and Brier score (calibration). Secondary: accuracy, precision/recall, and F1 by segment (client, program, market) and by decision threshold.

ROC curve and interpretation. As of now it does not exist (single class). With 0/1 collected, the ROC will show the trade-off between TPR and FPR; the cutoff should be chosen to maximize expected revenue, not just precision (e.g., apply different cut points by time band/program).

## 4.2 Occupancy Estimation Model
Objective and motivation. While there are no acceptance labels, we estimate future occupancy using a proxy derived from the price model’s error: the closer the suggested price is to a coherent historical reference, the higher the chance of occupancy.

Input/Output. Inputs: suggested price ppseg_sugerido (from the ex-ante pricing model, RF — Block C) and a lagged historical reference. Transformations: absolute/normalized error and the exponential function prob_ocupacao = exp(-k * erro_norm) to increase contrast. Outputs: prob_ocupacao (0–1) and receita_esperada = preço × prob_ocupacao.

Metrics/findings. Since the price model fits very well (high R²), the mean error is small and prob_ocupacao tends to be close to 1; even so, the exponential transformation creates useful variation in the tail. In the −20% / 0% / +20% simulations, the average expected revenue was ≈ −0.001 / 0.047 / −0.002 (relative units), indicating 0% (suggested price) as the optimal point

## 4.3 Model Interpretation and Business Alignment
How preco_sugerido is generated/adjusted. The price originates from the ex-ante pricing model (Random Forest — Block C: structural + seasonal + clusters) and is blended with a lagged historical anchor (means by client/program/executive, with no leakage). The blend weights model confidence against historical stability. Next, business rules are applied (floors/ceilings by format/band, rate-card roundings, outlier guardrails) and an expected-revenue optimization step based on the prob_ocupacao proxy, testing discount/markup scenarios to choose the best operating point.

How the sales team interprets the “chance of acceptance.” The current probability is a confidence signal (proxy): high values indicate a price aligned with the historical behavior of that context; medium values suggest a moderate price adjustment or schedule repositioning; low values call for a proposal review (band/program) or an alternative package. As we begin to log not-sold/refused cases, this proxy will evolve into a calibrated classifier (with ROC/PR-AUC and Brier), enabling objective thresholds by segment and governance of pricing decisions.

## 4.4 Elasticity Modeling - Price Sensitivity and Optimal Range Estimation

### Objective

The elasticity model aims to estimate how variations in price affect the expected occupancy rate and, consequently, the expected revenue of advertising slots.  
Unlike the previous models — which focused on predicting an absolute price or classifying occupancy — this model introduces a *continuous behavioral relationship* between price and demand, allowing the commercial team to identify price intervals that maximize utilization and profitability.

### Methodology

The construction of this model integrates two complementary datasets:

- **Historical insertions dataset:** containing actual sales data (price paid, duration, format, and station);
- **Reference price table:** representing the standard rates for each time range (e.g., *06:00/22:00 - Rotativo*, *07:00/19:00 - Rotativo*).

The datasets were preprocessed to align time ranges (*faixas horárias*) and radio stations (*praças*), creating a unified table associating:

- Each real insertion,
- Its historical price and effective occupancy,
- And the corresponding reference (suggested) price.

For each time range and duration, the model calculates:

- **Average historical price** (`preco_medio_hist`);
- **Proportion of unsold inventory (calhaus)** as a proxy for non-occupied slots;
- **Estimated occupancy rate** (`1 - calhau_rate`).

### Outputs and Interpretation

For each station and time range, the model derives:

- **Price elasticity coefficient (β):** indicates whether the demand is elastic (|β| > 1) or inelastic (|β| < 1);
- **Expected revenue curve (R = P × O):** product of price and occupancy, showing the revenue-maximizing point;
- **Recommended price range (Pmin–Pmax):** an interval around the optimal price (typically ±10–20%) that balances sales volume and margin.

This results in a **consultation table** for the commercial area, suggesting:

| Praça | Faixa Horária | Duração | Preço Mínimo | Preço Ótimo | Preço Máximo |
|--------|----------------|----------|----------------|---------------|----------------|
| RÁDIO LITORAL LINHARES | 06:00/22:00 | 30” | 150.00 | 165.00 | 180.00 |
| RÁDIO LITORAL CACHOEIRO | 07:00/19:00 | 45” | 220.00 | 235.00 | 255.00 |

These values can later be dynamically adjusted considering contextual variables such as client type, seasonality, or campaign priority.

---

### Business Application

This elasticity approach allows:

- Defining **flexible price ranges** instead of fixed values;
- Simulating how changes in price would affect sales and occupancy;
- Supporting the **creation of dynamic dashboards** that visualize optimal points and sensitivity curves for each advertising slot type.

By combining econometric insight and real commercial data, this model provides a more actionable framework for **data-driven pricing decisions** — balancing profitability and inventory utilization.


# 5. Dynamic Pricing Strategy

## 5.1 Price Suggestion Logic
The suggested price is generated by a predictive engine that estimates price per second from structural and seasonal variables and cluster profiles (client, program, executive). For ex-ante quoting, we use a Random Forest that captures non-linear interactions; the result is combined with a lagged historical anchor. The weight between prediction and history varies according to confidence/data volume, ensuring robustness even in cold start.

Since there are not yet acceptance labels (0/1), the “occupancy chance” is a proxy derived from the error between the suggested price and history, transformed by an exponential function. With this probability, we simulate expected revenue across scenarios (e.g., −20%, 0%, +20%) and choose the point that maximizes revenue, while respecting floors/ceilings and commercial rules. In tests, the model’s price was close to the optimum. Commercially, high probabilities call for defending the price; intermediate ones, small adjustments; low ones, repositioning. As future logs of unaccepted/canceled proposals become available, this proxy will evolve into a calibrated classifier, maintaining governance with temporal validation and leakage prevention.

## 5.2 Adjustment Rules and Thresholds
Price suggestions are applied within operating bands defined by floor and ceiling per format, market/station, time band, and program. These limits are derived from the lagged history and internal benchmarks and act as “rails” to prevent suboptimal or distorted offers: below the floor, only exceptions justified by package/volume or a tactical occupancy objective are allowed; above the ceiling, evidence of demand is required (strong seasonality, scarce inventory, program performance). The final price also undergoes rate-card rounding and an outlier guardrail: if the suggested value deviates substantially from the historical interquartile range for that client/program, the proposal is flagged for manual review. During high-season periods, the anchor is multiplied by a controlled factor, while in cold start the weight shifts to the cluster/program and limits become more conservative.

There are special conditions by client and portfolio that modulate the negotiation range. Strategic accounts or long-term agreements operate with narrower bands and predetermined maximum discounts; price-sensitive clients may have a wider adjustment window, provided expected revenue remains above the base scenario. Any floor/ceiling overrun requires justification and escalation, and the decision considers the proxy acceptance probability, the elasticity observed in simulations (−10% / 0% / +10%), and margin targets. All exceptions are logged to feed back into the limits, which are recalibrated periodically based on model error, win rate by band, and drift signals.

## 5.3 Impact Simulation
With the models applied, the scenarios indicate that projected occupancy—estimated via the exponential proxy of the error—remains high in most cases and varies mainly in the tails, as we move away from the reference price. This means the average occupancy gain is marginal when operating near the suggested price, but the probability falls more quickly with aggressive discounts or increases, reflecting the sensitivity observed in history. In revenue terms, the optimal operating point coincides with the suggested price itself: in the −20%, 0%, and +20% simulations, the average expected revenue was approximately −0.001, 0.047, and −0.002 (relative units), reinforcing that dynamic pricing centered on the predicted value maximizes return under current constraints.

Visually, the adjustment is well captured by a concave curve of expected revenue as a function of price variation: the peak occurs around 0% (model price) and drops as we move either below or above it. This shape summarizes the algorithm’s behavior: the suggested price results from the blend between context (structural, seasonal, and cluster) and the historical anchor, and its robustness appears when we test price shocks and the solution remains at the top of the curve. For presentation purposes, I included a chart that reconstructs this relationship from the three reported scenarios—it shows the fitted curve and the simulated points, making it easier for the sales team to read.

# 6. Evaluation and Results

## 6.1 Metrics Overview
Despite the labeling challenges (all insertions in the dataset were aired, i.e., single class), we were able to develop and test two complementary models:

**Pricing Model:** the Random Forest (Block C) achieved high explanatory power with an \(R^2\) above 0.90, indicating strong adherence between predicted prices and historical realized prices, especially when considering structural variables (format, market/station), seasonal variables (time band, month), and client/program/executive groupings.

**Occupancy Proxy:** derived from the pricing model’s error, applying an exponential function to estimate the probability of acceptance. This proxy enabled simulation of different price scenarios (−20%, 0%, +20%) and resulted in maximum expected revenue at the 0% point, reinforcing confidence in the base model.

Although we tested different models for pricing and occupancy, we faced an important structural limitation: the absence of negative data—that is, refused proposals, non-aired insertions, or canceled campaigns. As a result, the models showed seemingly perfect performance metrics (e.g., accuracy and recall close to 100%), but these merely reflect the ability to reproduce patterns already observed in the past, and not necessarily to predict new behaviors. The outcome was a model highly adherent to history but with low predictive capacity in new contexts or under strategy changes.

In light of this, we began using the current engine as an analytical tool, supporting commercial decisions through visualization and interpretation of historical data. In parallel, we are shifting to an elasticity-based approach, simulating different price variations and observing their expected impacts on occupancy and revenue. This type of model does not rely solely on binary labels; it combines structural and seasonal factors to suggest the “ideal price” in different scenarios, offering the sales team a more flexible tool aligned with the real dynamics of negotiation.

---

## 6.2 Business Impact
The forecasts aim to bring new information to the quoting process, replacing exclusive reliance on fixed rate cards and executive intuition with price suggestions based on historical and contextual variables. In the absence of negative data (such as formal proposal refusals), the current system allows simulation of suggested prices with high consistency only relative to past behavior. This would offer a starting point for negotiations but still falls short of the ideal impact expected from the application; therefore, we expect the evolution toward elasticity to bring greater positive impact to the sales process.

Even so, the initial pricing and occupancy models already allow incorporating an occupancy probability—even if based only on historical error. This indicator could begin to support decision-making by indicating when to defend a price, apply discounts, or reposition the offer. The introduction of this predictive layer inaugurates a new, data-grounded approach that can be refined as new records are included.

The dashboards to be developed will amplify this impact by enabling real-time scenario simulation, aiming to provide the sales executive with:
- A suggested price close to the ideal;
- The estimated probability of occupancy, guiding strategic adjustments;
- The potential revenue impact when applying discounts or increases.

This interface reduces subjectivity, empowers the team with visual insights, and promotes a more transparent, cohesive, and scalable process.

Finally, the introduction of simulations with elasticity curves seeks to make the process more effective, allowing the sales team to explore future scenarios and understand how different prices affect estimated occupancy. With continuous data collection—especially refusals and exceptions—it will be possible to evolve toward more refined predictive models personalized by client, time band, and period, making the negotiation process more scalable, strategic, and data-driven.

---

## 6.3 Lessons Learned
Throughout the development of this module, one of the main learnings was that data quality and diversity are decisive for the success of predictive models. The absence of negative labels—such as refused proposals, unsold items, or canceled campaigns—significantly limited the models’ ability to learn real acceptance contrasts, leading to inflated metrics and predictions that overly adhere to history. This scenario reinforced the importance of a solid data collection and governance strategy that also includes cases of commercial failure, which are essential for calibrating classifiers and assessing elasticity more accurately.

Another important lesson was understanding that high statistical performance does not necessarily translate into business value. Models with high \(R^2\) or low error rates proved efficient at reproducing the past but were still limited in projecting new scenarios. The experience highlighted the need to balance technical performance with interpretability and practical applicability, ensuring that forecasts are truly useful in guiding commercial decisions.

The value of an iterative approach between technical and business areas also became evident. Meetings with Rede Gazeta representatives were fundamental to validate hypotheses, interpret results, and adjust modeling to operational reality. This continuous interaction showed that building an effective predictive model goes beyond technique—it involves translating data learnings into understandable and actionable insights for the sales team.

Finally, the module reinforced the importance of treating the current model as an evolving analytical tool. The use of occupancy proxies and elasticity simulations proved a strategic intermediate step, allowing the system to continue generating value while new data are incorporated. This learning paves the way for the next module, which will focus on consolidating an elasticity-based model and on integrating forecasts and visualizations so they are directly useful to Rede Gazeta’s operational flow, bringing technology ever closer to commercial decision-making.

# 7. Next Steps – Transition to Module 4

In Module 4, the focus will be on refining the models and developing the system’s final interface for internal use and direct support in commercial negotiations.

We will maintain constant alignment with the team, tracking metrics and incorporating improvement suggestions to pursue the project’s ultimate goal. In addition, we will deliver comprehensive documentation covering everything developed during the process and the usage of the final system to be delivered.

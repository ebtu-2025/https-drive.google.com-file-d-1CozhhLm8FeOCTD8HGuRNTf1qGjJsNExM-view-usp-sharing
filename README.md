# https-drive.google.com-file-d-1CozhhLm8FeOCTD8HGuRNTf1qGjJsNExM-view-usp-sharing
This project leverages Bayesian change point detection to link Brent oil price structural breaks with major global events. It provides actionable insights for investors, policymakers, and analysts through statistical modeling and an interactive dashboard, enabling better decision-making in an unstable energy market.
Brent Oil Price Change Point Analysis Project Report
Date: July 31, 2025

Task 1: Data Analysis Workflow & Understanding the Model
Overview
This project investigates how major political and economic events impact Brent crude oil prices using Bayesian change point detection.

Workflow
Data Preparation: Load and clean Brent oil prices from May 20, 1987 to September 30, 2022. Convert date fields, sort data, and check for missing values.

Exploratory Data Analysis (EDA): Plot raw prices over time to visualize trends and shocks. Calculate log returns (log(price_t) - log(price_t-1)) to stabilize variance and better detect volatility.

Event Data Compilation: Research and compile a dataset of 10-15 key geopolitical, economic, sanction, and OPEC policy events relevant to the oil market. Include approximate start dates and descriptions.

Bayesian Modeling: Use PyMC3 to implement a change point detection model on the log return series, aiming to identify structural breaks in price behavior.

Insights & Reporting: Link detected change points to the compiled real-world events, quantify impacts on average returns and volatility, and communicate findings.

Dashboard & Communication: Develop an interactive dashboard and clear reports for stakeholders including investors, policymakers, and analysts.

Assumptions
Log returns are approximately stationary, allowing change point modeling.

Initial model assumes a single change point; extensions can model multiple.

Detected correlations do not prove causation; market reactions may lag or lead events.

Volatility is assumed constant in the simple model.

Sample Key Events
Date	Event	Type	Description
2008-09-15	Global Financial Crisis	Economic	Collapse of Lehman Brothers, global recession
2010-12-17	Arab Spring Begins	Geopolitical	Political upheaval in Middle East & North Africa
2014-11-27	OPEC Refuses Output Cut	OPEC Policy	OPEC declines to cut production, causing price drops
2020-04-20	Oil Futures Turn Negative	Market Shock	WTI futures fall below zero amid oversupply
2022-02-24	Russia Invades Ukraine	Geopolitical	Conflict threatens oil supply, increasing volatility

Communication Plan
Investors: Interactive dashboard for exploring price dynamics and event impacts

Policymakers: Executive summaries for strategy formulation

Analysts: Technical notebooks with modeling details

Public: Infographics and blog posts to increase transparency

Task 2: Change Point Modeling and Insight Generation
Bayesian Change Point Model Overview
A discrete uniform prior models the unknown change point 
𝜏
τ within the data range.

Separate normal priors represent mean log returns before (
𝜇
1
μ 
1
​
 ) and after (
𝜇
2
μ 
2
​
 ) the change point.

A single standard deviation 
𝜎
σ (half-normal prior) models noise, assumed constant.

The likelihood connects the observed log returns with these parameters.

Markov Chain Monte Carlo (MCMC) sampling estimates posterior distributions for 
𝜏
τ, 
𝜇
1
μ 
1
​
 , 
𝜇
2
μ 
2
​
 , and 
𝜎
σ.

Example Interpretation
The model may detect a change point around March 2020, aligning with the COVID-19 pandemic and the unprecedented oil futures collapse.

For example, the average daily log return shifts from 
−
0.0005
−0.0005 (before) to 
0.0012
0.0012 (after), indicating a regime change.

Quantifying impact: This corresponds to a roughly 340% increase in mean log returns post-event, signaling increased volatility and market disruption.

Advanced Extensions
Multiple Change Points: Hierarchical Bayesian models can detect several breaks over time.

Additional Variables: Incorporate macroeconomic indicators like GDP, inflation, exchange rates to explain variance better.

Alternative Models: Markov Switching models to capture “calm” vs. “volatile” market regimes, or Gaussian processes for nonlinear trends.

Event Detection Automation: Use natural language processing (NLP) to integrate real-time news and detect emergent events dynamically.

Task 3: Interactive Dashboard Development
Architecture Overview
Backend: Flask application exposes REST API endpoints serving price data, event metadata, and model output (change points, parameter estimates).

Frontend: React application visualizes Brent oil prices, detected change points, and event timelines interactively using charting libraries such as Recharts.

Data Storage: Historical price and event data stored as CSV/JSON files, with model outputs serialized similarly for API serving.

Key API Endpoints
Endpoint	Purpose
/api/prices	Return raw price and log return time series
/api/events	Provide details of geopolitical, economic, and OPEC events
/api/change-points	Return Bayesian model outputs (tau, means, volatility)
/api/summary	Serve downloadable executive summary or model report

Frontend Components
Price & Log Return Charts: Time series visualization with zoom and pan capabilities.

Change Point Markers: Vertical lines highlighting statistically significant change points.

Event Timeline: Annotated key events linked to price movements.

Filters: Date range selectors and toggles to show/hide events or volatility regimes.

Download Reports: Ability to export summaries or data subsets as PDF for offline review.

Future Enhancements
Regime switching visualization to highlight calm and volatile periods.

Integration of live data feeds and model updates through orchestration tools like Dagster or Airflow.

AI-powered event explanation bot using Retrieval-Augmented Generation (RAG) to interpret changes.

Scenario simulation tools (“What if OPEC cuts production?”).

Summary
This project leverages Bayesian change point detection to link Brent oil price structural breaks with major global events. It provides actionable insights for investors, policymakers, and analysts through statistical modeling and an interactive dashboard, enabling better decision-making in an unstable energy market.


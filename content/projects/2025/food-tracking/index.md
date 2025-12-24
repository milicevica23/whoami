---
title: Food Tracking & Health Impact Analysis
summary: A personal health analytics system that tracks food consumption and correlates ingredients/allergens with health outcomes.
date: 2025-12-24
authors:
  - aleks
tags:
  - Project
  - Data Engineering
  - Dagster
  - dbt
  - DuckDB
  - Health Analytics
links:
  - icon: brands/github
    name: repository
    url: "https://github.com/milicevica23/food-tracking"
  - name: data-input
    url: "https://docs.google.com/forms/d/e/1FAIpQLSc0_qS9dJ4lBwpG3ThMBWqbUr8Fe__Wrn2b6xy4aDTdctWlBA/viewform"
  - name: data-visualization
    url: "https://milicevica23.github.io/food-tracking-serving/" 

---
## Overview
Few years back I realized that after eating certain food sometimes I feel bad, have headaches or get very sleepy. After a discussion with a colleague he advised me to start to track my food intake and how I feel. For the first few weeks I was dooing it in an excel and then decided to use my knowledge and build something fun. This project servers to better understand food impact on my healt and also as a playground for new technologies, processes and architectures (e.g. I tried for the first time to code with AI assistance - Claude code)

**you can try it out if you want but be aware that data is publicly available and not properly secured or backed up**

## Architecture
Idea is very simple: collect data with a user interface, save data to a database, enrich data, visualize and extract insights.

(Welcome to data engineering :)

## Components
### [Food collection survey](https://docs.google.com/forms/d/e/1FAIpQLSc0_qS9dJ4lBwpG3ThMBWqbUr8Fe__Wrn2b6xy4aDTdctWlBA/viewform)

### [Visualisation dashboard](https://milicevica23.github.io/food-tracking-serving/)

## Rules I am following
- log all food consumed in one meal in a single row
- add self-assessment 1-2 hours after the meal
- avoid eating other food for at least 3-4 hours after the meal

## Status:
I will from time to time update status and direction of the project here.

### 2025-12-24 - init
#### Overall
The general idea was to setup initial ui for data collection, basic dagster,dbt and motherduck integration (I know about dagster and dbt from my work) and have a basic dashboard with few metrics and visualizations.
I had few things in my mind what I want to learn with the first iteration:
- how to use google forms as a data collection ui (I was suprised with out of box features like saving and editing entries in google sheets, sending email confirmations)
- try to code with ai assistance (done) -> claude code blew my mind few times 
- deploy dagster on self hosted kubernetes cluster with self hosted runner (done but it was harder then expected)
- connect and explore motherduck as I wanted to get back to duckdb
- learn a new visualization tools (I decided for evidence because it already had a dagster integration that I now think is not mature and needs a bit of improvement that I ll try to contribute)

#### Learnings
- process around building docker images and deployment in self hosted runners on self hosted kubernetes cluster need a lot of 
knowledge that we often think is granted as we have devops colleagues 
- start simple with visible business value is more important then sophisticated tooling. For example I use now google forms to collect data instead of building custom UI in rust :D (I started and stopped at least 3 times)
- having for the first time a working e2e solution was very motivating and helps extend and improve it further
- it is hard to collect data and be precise. What is exactly in the meal? How do you really feel from 1 to 10? 
#### Next Steps
- create more dashboards and visualizations from the existing data
- enrich collected data with AI generated ingredients from food name and picture
- trying to find more friends who are willing to try this out
- trying soap for secrets and fluxcd for kubernetesdeployment
- trying to improve dagster-evidence component integration
- making refreshes automatically running on schedule

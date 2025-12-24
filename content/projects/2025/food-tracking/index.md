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
A few years ago, I realized that after eating certain foods, I sometimes feel bad, have headaches, or get very sleepy. After discussing this with a colleague, he advised me to start tracking my food intake and how I feel. For the first few weeks, I was doing it in Excel and then decided to use my knowledge and build something fun. This project serves to better understand the impact of food on my health and also as a playground for new technologies, processes, and architectures (e.g., I tried for the first time to code with AI assistance - Claude Code).

I hope this project can help you as it helped me. Happy to receive feedback and ideas.

**You can try it out if you want, but be aware that data is publicly available and not properly secured or backed up.**

## Architecture
The idea is very simple: collect data with a user interface, save data to a database, enrich data, visualize, and extract insights.

(Welcome to data engineering :)

## Components
### [Food collection survey](https://docs.google.com/forms/d/e/1FAIpQLSc0_qS9dJ4lBwpG3ThMBWqbUr8Fe__Wrn2b6xy4aDTdctWlBA/viewform)
You can enter as many entries as you have meals per day. The only personal information required is an email, which you can fake if you want to stay anonymous.
I normally submit a new entry with only the food name and picture, then after 1-2 hours I add a self-assessment of the health impact. You will receive a confirmation email after the first submission and can edit it later. 

#### Rules I follow
- Log all food consumed in one meal in a single row
- Add self-assessment 1-2 hours after the meal
- Avoid eating other food for at least 3-4 hours after the meal

### [Visualization dashboard](https://milicevica23.github.io/food-tracking-serving/)
Your email is hashed, and you can find your hash with the following statement
```
SELECT sha256('123@gmail.com') as user_hash_id;
```
You can then search for your user and click in the table to get to your personal dashboard.

The dashboard needs a bit more love and will get it soon.

## Status
I will update the status and direction of the project here from time to time.

### 2025-12-24 - Init
#### Overall
The general idea was to set up an initial UI for data collection, basic Dagster, dbt, and MotherDuck integration (I know about Dagster and dbt from my work), and have a basic dashboard with a few metrics and visualizations.
I had a few things in mind that I wanted to learn with the first iteration:
- How to use Google Forms as a data collection UI (I was surprised by the out-of-the-box features like saving and editing entries in Google Sheets, and sending email confirmations)
- Try to code with AI assistance - Claude Code blew my mind a few times
- Deploy Dagster on a self-hosted Kubernetes cluster with a self-hosted runner (it was harder than expected)
- Connect and explore MotherDuck as I wanted to get back to DuckDB
- Learn a new visualization tool (I decided on Evidence because it already had a Dagster integration, though I now think it's not mature and needs improvement that I'll try to contribute)

#### Learnings
- The process around building Docker images and deployment with self-hosted GitHub runners on a self-hosted Kubernetes cluster requires a lot of knowledge that we often take for granted when we have DevOps colleagues
- Starting simple with visible business value is more important than sophisticated tooling. For example, I now use Google Forms to collect data instead of building a custom UI in Rust (I started and stopped at least 3 times)
- Having a working end-to-end solution for the first time was very motivating and helps extend and improve it further
- It is hard to collect data and be precise. What exactly is in the meal? How do you really feel on a scale from 1 to 10?

#### Next Steps
- Create more dashboards and visualizations from the existing data
- Enrich collected data with AI-generated ingredients from food name and picture
- Find more friends who are willing to try this out
- Try SOPS for secrets and FluxCD for Kubernetes deployment
- Try to improve the Dagster-Evidence component integration
- Make refreshes run automatically on a schedule

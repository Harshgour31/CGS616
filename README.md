# Estimating the Causal Effect of Doomscrolling on Task Avoidance

**Course:** CGS 616: Human Centered Computing  
**Author:** Harsh Gour (Roll No: 230444)  
**Institution:** Indian Institute of Technology (IIT) Kanpur  

---

## 📌 Project Overview
This repository contains the Python implementation and causal analysis for the final assignment of CGS 616. The project investigates the cognitive and behavioral mechanisms of "doomscrolling" and its direct impact on academic procrastination (task avoidance). 

Rather than relying on simple observational correlation—which is heavily biased by how "boring" a task is—this project employs **Pearl’s Do-Calculus** and the **Backdoor Adjustment Formula** to mathematically isolate the true causal effect of short-form video consumption on executive control.

## 🧠 Causal Inference Framework
The analysis is structured around a specific Directed Acyclic Graph (DAG) with a known backdoor path:

* **$X$ (Intervention/Cause):** Doomscrolling session > 20 minutes. *(Note: A custom-built classification model was used to determine if a session transitioned from controlled usage to compulsive doomscrolling).*
* **$Y$ (Outcome):** Task Avoidance (delaying academic work by > 1 hour).
* **$Z$ (Confounder):** Task Boredom / Aversiveness.

Because boredom ($Z$) causes both the desire to scroll ($X$) and the desire to avoid the task ($Y$), the observational probability $P(Y | X)$ is artificially inflated. This script manually calculates $P(Y | do(X))$ to sever the backdoor path $X \leftarrow Z \rightarrow Y$.

## 📂 Repository Contents
* `CGS616_Assignment4.ipynb`: The main Python script containing the Exploratory Data Analysis (EDA), NetworkX DAG visualization, and manual Do-Calculus math.
* `self_data (1).xlsx`: The behavioral dataset (40 observations over 10 days) tracking epochs, locations, task types, boredom states, and scroll durations.
* `section1_eda.png`: Visualizations of scroll durations, avoidance rates by location, and platform distribution.
* `section2_dag.png`: The visual representation of the causal graph.
* `section3_docalculus.png`: The final mathematical breakdown of the Average Causal Effect (ACE).

## 🚀 How to Run the Code

**1. Install Dependencies** Ensure you have Python installed along with the required data science libraries:
```bash
pip install pandas numpy matplotlib seaborn networkx openpyxl

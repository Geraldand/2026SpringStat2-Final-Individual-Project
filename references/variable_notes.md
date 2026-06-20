# Data Dictionary (Codebook) for YRBS 2007 Analysis

**Project:** Predicting Youth Violence and Weapon Behaviors Through School Safety Concerns and Layered Contexts
**Description:** This document outlines the definitions, original survey questions, and data recoding logic for all variables used in our statistical inference (OLS Multiple Linear Regression) and Exploratory Data Analysis (EDA). Invalid responses and missing values (NaN) were entirely excluded during the data cleaning process.

---

## Part 1: Core Variables for Regression Analysis

### 1. School Safety Insecurity (Main Explanatory Variable / X)
* **Recoded Variable Name:** `Safety_Days_Missed`
* **Original YRBS Question:** "During the past 30 days, on how many days did you not go to school because you felt you would be unsafe at school or on your way to or from school?" (SafetyConcernsAtSchool)
* **Coding Logic (Continuous Scale):**
    * `0.0`: 0 days
    * `1.0`: 1 day
    * `2.5`: 2 or 3 days
    * `4.5`: 4 or 5 days
    * `6.0`: 6 or more days

### 2. Comprehensive Violence & Weapon Behavior (Response Variable / Y)
* **Recoded Variable Name:** `Violence_Risk_Score`
* **Original YRBS Variables Combined:** 1.  `WeaponCarrying`: "During the past 30 days, on how many days did you carry a weapon such as a gun, knife, or club?"
    2.  `WeaponCarryingAtSchool`: "During the past 30 days, on how many days did you carry a weapon such as a gun, knife, or club on school property?"
    3.  `PhysicalFighting`: "During the past 12 months, how many times were you in a physical fight?"
    4.  `PhysicalFightingAtSchool`: "During the past 12 months, how many times were you in a physical fight on school property?"
* **Coding Logic (Composite Score: 0 to 4):**
    * Each of the 4 behaviors above was first binarized (`1` if the student engaged in the behavior 1 or more times/days, `0` if 0 times/days).
    * `Violence_Risk_Score` is the sum of these 4 indicators.
    * **Scale Interpretation:** * `0`: No violent or weapon-carrying behaviors.
        * `1 - 4`: Cumulative index representing the diversity and severity of the student's risk profile (higher scores indicate participation in multiple forms of violence/weapon possession).

---

## Part 2: Demographic & Psychological Control Variables

### 3. Biological Sex (Control Variable / Dummy)
* **Recoded Variable Name:** `Is_Male`
* **Original YRBS Question:** "What is your sex?" (WhatIsYourSex)
* **Coding Logic:**
    * `1`: Male
    * `0`: Female

### 4. Depressive Affect & Psychological Distress (Control Variable / Dummy)
* **Recoded Variable Name:** `Is_Sad`
* **Original YRBS Question:** "During the past 12 months, did you ever feel so sad or hopeless almost every day for two weeks or more in a row that you stopped doing some usual activities?" (SadOrHopeless)
* **Coding Logic:**
    * `1`: Felt sad or hopeless.
    * `0`: Did not feel sad or hopeless.

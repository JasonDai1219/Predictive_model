# A Predictive model on recipe's rating score
This is a project of DSC 80 at University of California San Diego that analyzes the relationship among average ratings of recipes and times required of recipes conducted by Jason Dai and Kelly Gong.

---
## Framing the Problem -- Problem Identification

1. **Prediction question** : in this analysis, we are trying to predict the `rating` score of a recipe using data provided in the `merged_head` dataframe. 

2. **Type** : classification. We chose this type of predicition model is because `rating` is a numerical data column in the orginal dataset, however, it only has 5 unique values which classifies each recipe into a level of popularity.

3. **Binary Classification**: we believe the ratings below or equal to 3 is generally low that people would not prefer to choose while those with ratings of 4 or 5 are considered good and popular recipes, so we choose to apply binary classification, and it is unnecessary to use multiclass classification.

4. **Response variable** : `rating`. We chose this variable because the prediction could help people who want to post their unique food recipes to know whether the audience would like it or not.

5. **Metric**: **accuracy**. It reveals the accuracy of our prediction model. Moreover, we think that **accuracy** is highly interpretable, thus allows us to better understand how different our predictions are compared to the real data.

---

---
## Baseline model

---

---
## Final model

---

---
## Fairness Analysis
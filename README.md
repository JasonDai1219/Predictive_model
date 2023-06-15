# A Predictive model on recipe's rating score
This is a project of DSC 80 at University of California San Diego that train a predictive model to predict a given recipe's rating score by Jason Dai and Kelly Gong.

---
## Framing the Problem -- Problem Identification

1. **Prediction question** : in this analysis, we are trying to predict the `rating` score of a recipe using data provided in the `merged_head` dataframe. 

2. **Type** : classification. We chose this type of predicition model is because `rating` is a numerical data column in the orginal dataset, however, it only has 5 unique values which classifies each recipe into a level of popularity.

3. **Multiclass classification**: we think all possible `rating` scores in this dataset are : `1`, `2`, `3`, `4`, and `5`. Therefore, using a multiclass classification would give recipe posters more accurate predictions on what score their recipe potentially could get.

4. **Response variable** : `rating`. We chose this variable because the prediction could help people who want to post their unique food recipes to know whether the audience would like it or not.

5. **Metric**: **accuracy**. It reveals the accuracy of our prediction model. Moreover, we think that **accuracy** is highly interpretable, thus allows us to better understand how different our predictions are compared to the real data.

**Further Data Cleaning**
`tags` and `description` are the two columns related to `rating`. For instance, people may prefer the recipes that are **"easy"** (appears in `tags`) or **"delicious"** (appears in `description`). In this way, we clean our data further by including the columns indicating whether each row contains the targeted words. Furthermore, looking at the `nutrition` column, people may prefer recipes with less calories, so we extract the **calories** of each recipe, which is the first element in the nutrition list of every list.

---

---
## Baseline model

**Model Description**: We build our baseline model based on two features, `tags` and `description`, which are the two categorical columns, because the information in the two columns are different from each other, and both contains some elements that people may prefer or not. We choose to include **"easy"**, **"breakfast"**, **"lunch"**, and **"dinner"**, which appear in `tags`, and **"delicious"**, which appears in `description` as the targeted words based on the further data cleaning in the previous part.

---

---
## Final model

---

---
## Fairness Analysis

### In 2012, the revolutionary iPhone makes people's access to internet easier and ubiquitous, we would like to see our model's performance in these groups:

1. Group X : recipes on the website published prior to 2012.

2. Group Y : recipes on the website published after and in 2012.

3. Evaluation metric : `Precision`. The reason to use `precision` here is that we would like to see low `precision` metric in this predictive model as the `false positive` would imply that the user making the recipe should actually spend energy on making other recipes.

---

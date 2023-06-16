# A Predictive Model on Recipes' Rating Scores
This is a project of DSC 80 at University of California San Diego that train a predictive model to predict a given recipe's rating score by Jason Dai and Kelly Gong.

---
## Framing the Problem -- Problem Identification

1. **Prediction question** : in this analysis, we are trying to predict the `rating` score of a recipe using data provided in the `merged_head` dataframe. 

2. **Type** : classification. We chose this type of predicition model is because `rating` is a numerical data column in the orginal dataset, however, it only has 5 unique values which classifies each recipe into a level of popularity.

3. **Multiclass classification**: we think all possible `rating` scores in this dataset are : `1`, `2`, `3`, `4`, and `5`. Therefore, using a multiclass classification would give recipe posters more accurate predictions on what score their recipe potentially could get.

4. **Response variable** : `rating`. We chose this variable because the prediction could help people who want to post their unique food recipes to know whether the audience would like it or not.

5. **Metric**: **accuracy**. It reveals the accuracy of our prediction model. Moreover, we think that **accuracy** is highly interpretable, thus allows us to better understand how different our predictions are compared to the real data.

**Further Data Cleaning**: 
`tags` and `description` are the two columns related to `rating`. For instance, people may prefer the recipes that are **"easy"** (appears in `tags`) or **"delicious"** (appears in `description`). In this way, we clean our data further by including the columns indicating whether each row contains the targeted words. Furthermore, looking at the `nutrition` column, people may prefer recipes with less calories, so we extract the **calories** of each recipe, which is the first element in the nutrition list of every list.

---

---
## Baseline model

**Model Description**: The dataset we are working on contains 2 quantitative columns, which are `minutes` and `n_ingredients`, 1 ordinal columns, which is `rating`, the one we want to predict, and the rest are categorical. 

We build our baseline model mainly based on two features, `tags` and `description`, which are the two categorical columns, because the information in the two columns are different from each other, and both contains some elements that people may prefer or not. We choose to include **"easy"**, **"breakfast"**, **"lunch"**, and **"dinner"**, which appear in `tags`, and **"delicious"**, which appears in `description` as the targeted words based on the further data cleaning in the previous part. 

We applied one-hot encoding to the above two categorical features while also keep the original value of `calories` : numerical, `minutes` : numerical, `n_steps` : numerical, and `n_ingredients` : numerical in the model since we expect that they may contribute to the rating score.

**Model Performance**: We use train/test split to test the mode, and its performance is generally good because it reaches an accuracy more than 0.5 while performing on the testing group.

---

---
## Final model

**Added Features**: We decide to include another feature for our final model, the `year`s of the creation of the recipes, which is extracted from the submission dates, `submitted` because it is likely that people would rate on the more recent recipes due to the increasing access to the internet.

Moreover, based on the data cleaning and our baseline model, we improved the transformation of two features, `calories` and `minutes`. In order to indicate whether the `calories` is high or low, we binarize it and set the threshold to be 500, which is a typical healthy meal level.

Furthermore, `minutes` are useful as a feature as less preparation time may be favored. Since we found the preparation time ranges wide, we decided to standardized the `minutes` feature so that we can understand it on a standardized scale. 

**Algorithm Description**: The modeling algorithm we chose is a RandomForestClassifier, which is robust to overfitting and works well with a mixture of numerical and categorical features. 

**Best Hyperparameters**: The hyperparameter included in the model is `max_depth`, which means the larger the value is, the more complex the model is. However, if the depth is too high, it may lead to an overfit of the training data and perform poorly on the testing data. Therefore, we use `GridSearchCV` to select the best hyperparameters. By comparing the performance of every possible depth with cross validation, the method help choose the depth with the highest mean score on the validation sets, which is 2.

**Final Model Performance**: After adding more features in our final model, the performance is significantly improved by about 10% approaching an accuracy of 0.7. Additionally, finding the best `max_depth` by `GridSearchCV` and using it to train the final model, the performance is further improved.

---

---
## Fairness Analysis

In 2012, the revolutionary iPhone makes people's access to internet easier and ubiquitous. We would like to see our model's accuracy in these groups:

Group X:
> Recipes published prior to 2012.

Group Y:
> Recipes published in and after 2012.

**Evaluation metric**: `Precision`. The reason to use `Precision` here is that we would like to see low `precision` metric in this predictive model as the `false positive` would imply that the user making the recipe should actually spend energy on making other recipes.

Null Hypothesis: 
> Our model is fair. Its precision on recipes published prior to 2012 and recipes published in or after 2012 are roughly the same, and any differences are due to random chance.

Alternative Hypothesis: 
> Our model is unfair. Its precision on recipes published prior to 2012 is greater than that of recipes published in or after 2012.

**Test statistic**: The signed difference between the accuracies of two groups. Specifically, accuracy of recipes published prior to 2012 group minus the accuracy of recipes published in or after 2012.

**Significance level**: 0.05

**P-value**: 0.0

**Conclusion**: Since the p-value of 0.0 is smaller than the significance level of 0.05, we reject the null hypothesis, and probably, the accuracy of recipes published prior to 2012 group is significantly greater than that of recipes published in or after the year 2012 in our analysis.

---

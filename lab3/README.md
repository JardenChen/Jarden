# Lab 3 - Modelling

## Ipython notebooks

* facebook_regression.ipynb and facebook_classification.ipynb contain the code used in the lecture.

## Lab Exercises
    
* Create a new ipython notebook called bank_classification.ipynb
	
* Check the bank dataset
	* ``bank-additional-full.csv``
	* [https://archive.ics.uci.edu/ml/datasets/Bank+Marketing](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)
	
* In the Ipython notebook you created

- [ ] Load the data from `bank-additional-full.csv`
- [ ] Data preprocessing:
    * Use LabelEncoder to convert the label into numbers.
    * Convert to dummies using `df_dummies = pd.get_dummies(df)`
    * Column "duration" must be deleted
    * Check if there are any missing values in the dataset. If there are, drop the rows.
    * Plot histogram of the label and calculate the imbalance in the dataset.
- [ ] Let's model the data:
    * Using the `train_test_split` function in scikit-learn, separate your dataset into a training and a test set, with a test size of 20% and random_state=50. Make sure the train/test split is stratified (and check that it is!). Stratified means that the percentages of classes in each fold remains constant.
    * Report the results of 10-fold stratified cross-validation on the training set using a random forest classifier with 100 trees and depth=3. **Ensure you're using an appropriate metric** (Use `sorted(sklearn.metrics.SCORERS.keys())` to see what are the valid options).
    * Compare the results of your classifier with that of a dummy classifier.
    * Use `GridSearchCV` to find a better set of parameters for your random forest.
    * Print the cross-validation metric (whichever you previously chose) that you obtain for the random forest for the best parameters found with GridSearchCV
    * What are the top 3 features?
    * Report the generalisation error (still using the same metric) on your test set.    
- [ ] Make sure you save your changes in Github and do the Unit lab's quiz on Moodle!


Attribute Information of the Bank Marketing dataset:

~~~
Input variables:
# bank client data:
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
# related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone') 
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
# other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
# social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric) 
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric) 
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')

~~~

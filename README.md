# Motivation¶
Identifying and classifying features that influence an offer completion. It would be interesting to understand who and why complete a certain offer and what insights does this dataset carry

CONCLUSION
Data Understanding

Here is the schema and explanation of each variable in the files:

portfolio.json

id (string) - offer id
offer_type (string) - type of offer ie BOGO, discount, informational
difficulty (int) - minimum required spend to complete an offer
reward (int) - reward given for completing an offer
duration (int) - time for offer to be open, in days
channels (list of strings)
profile.json

age (int) - age of the customer
became_member_on (int) - date when customer created an app account
gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
id (str) - customer id
income (float) - customer's income
transcript.json

event (str) - record description (ie transaction, offer received, offer viewed, etc.)
person (str) - customer id
time (int) - time in hours since start of test. The data begins at time t=0
value - (dict of strings) - either an offer id or transaction amount depending on the record
Data Cleaning Portfolio

1. Cleaned the channels field to include one entry for every row
2. Cleaned the 
Profile

1. Cleaned the age for records greater than or equal to 118
2. Cleaned gender for null and income imputed with mean for null
3. Chose a subset based on age < 80 as it made sense
4. Showed age, gender and income based distribution
Transcript

1. Cleaned the value field to get the offer id and associated amount and reward
2. dummy variable for event
Data Preparation

1. Combine the resultant profile, transcript and portfolio information
2. Aggregating to create one record per person
3. Analyze distibution of offer completed by Gender and Income
4. Create dummies for gender and offer Id 
Modeling

1. Creation of training and testing datasets using the final output data
2. Train a Random forest model Decision tree model followed by an ADA boost classifier 
3. Fit the model onto the test data 
4. tree-based models as I wanted to check feature importance
5. GridSearchCV() to find the best parameters for my model
Evaluation

1. used F1 score for measurement of accuracy
2. Decision tree comes back with an accuracy of 92% with the test data
3. Random Forest comes in with a 94 % 
4. ADABoost classifier comes back with an accuracy of 94% with the test data 
Result

1. This is a pretty good score, we are able to zero in on specific factors that influence the offer completion
2. Female population looks more likely to complete an offer
3. Higher percentage of interest to social media based offers
4. People with a higher median in icome usually tend to complete the offers especially females
5. Most popular offer type is dicount & BOGO
Next

Improvements - probably add new features and see how they can influence the offers

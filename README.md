# credit-risk-prediction

In this Project, we have built two strategies in one is Conservative, and the other is Aggressive.
We have used 0.3 threshold as the conservative strategy and 0.5 threshold as the aggressive strategy.
For these thresholds, we have calculated the default rates and revenue from train sample and test ( test1, test2) samples.



<img width="994" alt="image" src="https://github.com/mrohan2203/credit-risk-prediction/assets/70047636/b2c69616-0c51-452c-b3f8-0b8c507e144c"><br>




In this Credit Risk model, the time frame chosen for aggregation is 13 months spanning from March 2017 to April 2018.
This timeframe is enough to collect customers’ data portraying their different economic scenarios.
Our initial merge of train_data and 20% of train_labels yielded 1107082 observations and 192 features. The unique customers were extracted and that turned out to be 91783.
The train_data and train_labels are from the Kaggle repository: https://www.kaggle.com/competitions/amex-default-prediction/data <br>

Delinquency variables: indication if the payment was late or not. It is used to estimate credit behavior.
Balance variables: indication of the debt incurred by the borrower. It is an indication of how well the borrower is managing his or her’s finances.
Risk variables: the amount of risk involved in lending to a particular borrower.
Spend variables:  spending patterns of the borrower, which indicates lifestyle and financial behavior of the same.
Payment variables: frequency and consistency of the payments. <br>



<img width="420" alt="image" src="https://github.com/mrohan2203/credit-risk-prediction/assets/70047636/277ea468-5299-4334-a880-16b088ca8063"><br>



XGB model:
Grid search resulted in 72 models, all tested for AUC.
Increasing the number of trees by 300 in the search allows us to capture complex trends in data.
A higher learning rate (0.5) allows smaller datasets to capture new information quickly.
By setting a tree depth limit of 4, we prevent overfitting, thereby avoiding complex trees and improving accuracy.
Subsampling at a rate of 0.5 introduces a degree of randomness in the sample and also avoids having the possibility of overfitting, which is quite common at higher learning rates.
Sample weights allow us to ensure that all imbalances in the dataset are reduced, resulting in a robust and accurate model. <br>



<img width="507" alt="image" src="https://github.com/mrohan2203/credit-risk-prediction/assets/70047636/9deb3539-930e-4d83-b25d-ef1b878593db"> <br>



NN model:
Number of hidden layers regulates the complexity of model.
Number of nodes also regulates complexity of model.
Activation function tanh output range is [-1,1], while relu output range is [0, inf].
Dropout specifies the percentage of nodes in the hidden layers that drop from the model to prevent overfitting.
Batch size is the size of each sample processed during an epoch. Larger batch size leads to faster processing times, but also overfitting. <br>



<img width="401" alt="image" src="https://github.com/mrohan2203/credit-risk-prediction/assets/70047636/32f960ed-d3a9-41b6-8a39-cc7f2a690973"><br>



We predict future balance and spending values for each customer using historical average of these variables.
Use xgb model and the strategy function to calculate the default rate for each threshold.
Default rate (4.22%) means 30% of observations will have a default rate lower than 4.22%. <br>



<img width="939" alt="image" src="https://github.com/mrohan2203/credit-risk-prediction/assets/70047636/e2e4fbd0-cc9d-4eae-9ebc-394a8a4c5980"><br>

Annual Revenue for 1 Customer = (B_Ave*0.02 + S_Ave*0.001) * (12)









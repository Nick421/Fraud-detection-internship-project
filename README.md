# Fraud detection project
A unsupervised machine learning model trained for fraud detection of loyalty point card system.
This project is undertaken under Siam Piwat & 4PLUS Consulting internship.

For privacy purposes:
  * Lots of empty string exist in the code as they are table's column names. 
  * Lots of information is taken out to protect the company privacy.
  * All output is taken out to protect sensitive informations.

## Background
### Obtaining data and data preprocessing 
* Data is obtained through excel file that was imported from the main database.
* Data is also obtained through SQL querying the database.
* Data are stored in pandas frame and aggregated on to obtain the features.
* We normalised each feature to get rid of obvious anomaly which are not fraudulent behaviour.

### DBSCAN & K-NN Algorithm
* We utilise DBSCAN clustering algorithm to find anomalies, if a point is far from its neighbour it is consider an anomaly.
* We tested with different parameters with epsilon going from 0.05 to 0.5 increasing in 0.05 each time.
* We also found out from trial & error that with epsilon = 1.5 and minimum sample of 100, we obtained 2 cluster with minimum number of noise.
* We then seperate the 2 clusters as train and test data for K-NN algorithm.
* Train data is any point that is not an anomaly from DBSCAN result.
* While test data is all data with both normal and anomaly points.
* We then find average distance of 5 nearest neighour of each points.
* We then rank each points based on how far their average distance is from closet cluster.

### Autoencoder
* I followed the approach listed in the acknowledgement where we use the same train and test data as this is unsupervised learning.
* 1 hidden layer is used.
* We then use MSE(Mean square error) of each data points to determine if a point is fraudulent or not. The higher the MSE the more chance it could be a fraud.

### DBSCAN VS Autoencoder
* We then select top 30 data points from both approach.
* Compare the rank of each points.
* Conclusion: lots of points overlaps in top 30 but Autoencoder starts to differ from DBSCAN a lot from top 100 onwards. Thus more data cleaning is needed and maybe better feature selections.

## Acknowledgements
* https://weiminwang.blog/2017/06/23/credit-card-fraud-detection-using-auto-encoder-in-tensorflow-2/
* https://towardsdatascience.com/credit-card-fraud-detection-using-autoencoders-in-h2o-399cbb7ae4f1
* Anyone from Siam Piwat and 4PLUS Consulting that helped me complete this project.
* For more info, please privately message me as to protect any legal issue.

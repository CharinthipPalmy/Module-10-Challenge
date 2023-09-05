# Module 10 Challenge: Crypto Clustering

![Decorative image.]([Images/10-5-challenge-image.png](https://git.bootcampcontent.com/Monash-University/MONU-VIRT-FIN-PT-06-2023-U-LOLC/-/raw/main/10-Unsupervised-Learning/Homework/Instructions/Images/10-5-challenge-image.png))


## Background

In this Challenge, you’ll assume the role of an advisor at one of the top five financial advisory firms in the world. Competitors are fierce, so you want to propose a novel approach to assembling investment portfolios that are based on cryptocurrencies. Instead of basing your proposal on only returns and volatility, you want to include other factors that might impact the crypto market&mdash;leading to better performance for your portfolio.

When you present the idea, your manager loves it! So, you’re asked to create a prototype for submitting your crypto portfolio proposal to the company board of directors.

## What in the Creating

I've created a Jupyter notebook that clusters cryptocurrencies by their performance in different time periods. Then plot the results so that I can visually show the performance to the board.

The CSV file that’s provided for this Homework contains the price change data of cryptocurrencies in different periods.


### Find the Best Value for k Using the Original Data

In this section, I use the elbow method to find the best value for k.

1. Code the elbow method algorithm to find the best value for k. Use a range from 1 to 11.

2. Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

3. Answer the following question: What is the best value for k?
    **Answer:** k = 4

![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/Elbow%20curve%20by%20k.png?raw=true)

### Cluster Cryptocurrencies with K-means Using the Original Data

In this section, I use the K-means algorithm with the best value for k (found in the previous section) in order to cluster the cryptocurrencies according to the price changes of cryptocurrencies provided.

1. Initialize the K-means model with four clusters by using the best value for k.

2. Fit the K-means model using the original data.

3. Predict the clusters to group the cryptocurrencies using the original data. View the resulting array of cluster values.

4. Create a copy of the original data and add a new column with the predicted clusters.

5. Using hvPlot, create a scatter plot by setting `x="price_change_percentage_24h"` and `y="price_change_percentage_7d"`. Color the graph points with the labels found using K-means. Then, add the crypto name in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.

![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/scatter%20plot%20by%20k.png?raw=true)

### Optimize Clusters with Principal Component Analysis

In this section, I perform a principal component analysis (PCA) and reduce the features to three principal components.

1. Create a PCA model instance and set `n_components=3`.

2. Use the PCA model to reduce to three principal components. View the first five rows of the DataFrame.

3. Retrieve the explained variance to determine how much information can be attributed to each principal component.
**Answer** array([0.3719856 , 0.34700813, 0.17603793])

4. Answer the following question: What is the total explained variance of the three principal components?
**Answer:** 0.89503166

6. Create a new DataFrame with the PCA data. Be sure to set the `coin_id` index from the original DataFrame as the index for the new DataFrame. Review the resulting DataFrame.
![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/Image%205-9-2023%20at%204.00%20pm.jpg?raw=true)


### Find the Best Value for k Using the PCA Data

In this section, I use the elbow method to find the best value for k by using the PCA data.

1. Code the elbow method algorithm and use the PCA data to find the best value for k. Use a range from 1 to 11.

2. Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

3. Answer the following questions: What is the best value for k when using the PCA data? Does it differ from the best k value found using the original data?

**Answer:** The best value for `k` when using the PCA data is 4.
**Answer:** the best k values are the same as using the original data.

### Cluster Cryptocurrencies with K-means Using the PCA Data

In this section, you will use the PCA data and the K-means algorithm with the best value for k (found in the previous section) in order to cluster the cryptocurrencies according to the principal components.

1. Initialize the K-means model with four clusters by using the best value for k.

2. Fit the K-means model by using the PCA data.

3. Predict the clusters to group the cryptocurrencies by using the PCA data. View the resulting array of cluster values.

4. Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.

![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/Image%205-9-2023%20at%204.07%20pm.jpg?raw=true)

5. Using hvPlot, create a scatter plot by setting `x="PC1"` and `y="PC2"`. Color the graph points with the labels found using K-means. Then, add the crypto name in the `hover_cols` parameter to identify the cryptocurrency represented by each data point.

![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/PCA%20scatter.png?raw=true)

### Visualize and Compare the Results

In this section, you will visually analyze the cluster analysis results by observing the outcome with and without using the optimization techniques.

1. Create a composite plot using hvPlot and the plus (`+`) operator to compare the elbow curve that you created to find the best value for k with the original data and the PCA data.
![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/2Elbows.png?raw=true)
![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/Elbow_in_1.png?raw=true)
3. Create a composite plot using hvPlot and the plus (`+`) operator to compare the cryptocurrencies clusters using the original data and the PCA data.
![Alt text](https://github.com/CharinthipPalmy/Module-10-Challenge/blob/main/2Scatters.png?raw=true)
4. Answer the following question: After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data by using K-means?

  * **Answer:** When we use fewer features, you are essentially reducing the dimensionality of your data. This can result in a loss of information, as some important characteristics or patterns in the data may be encoded in the features that you are omitting. Therefore, the clusters formed based on a reduced set of features(Scatter Plot by PCA) may not capture the complete structure of the data. The interpretability of the clusters may be affected by the choice of features. If you remove features that are highly relevant to the interpretation of the clusters, it can make it harder to explain and understand the results

  * On the flip side, using fewer features can lead to simpler and more interpretable clusters. If some features are noisy or less relevant for the clustering task, removing them can help to focus on the most important aspects of the data. Using fewer features may reduce the risk of overfitting, especially if the original dataset has a high feature-to-sample ratio. Overfitting occurs when the model captures noise in the data instead of true patterns, and reducing features can help mitigate this.

  * In summary, experimentation, visualization, and domain knowledge can help to determine whether using fewer features enhances or hinders the quality and interpretability of clustering results.



---

Copyright 2022 2U. All Rights Reserved.

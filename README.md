# Cryptocurrencies

![image](https://user-images.githubusercontent.com/90650562/152713362-e6f73910-8889-4dec-a495-e25e6e6c4e84.png)

## Overview
This project was initiated with the intention to identify the cryptocurrencies available in the market and to classify them into groups based on the algorithm, proof type, the supply and the amount mined. The dataset was cleaned and the classification was done using an unsupervised machine learning technique: K Means clustering

## Analysis
- The dataset was obtained from cryptocompare [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist) and select values were taken into consideration: CoinName, Algorithm, ProofType, IsTrading, TotalCoinsMined, and TotalCoinsSupply
- The dataset containing details of 1252 cryptocurrencies was filtered to contain only cryptocurrencies that are currently **being traded**, and ones that have a valid algorithm. This resulted in 1144 cryptocurrencies
- The Istrading column was then dropped since it was not required for further analysis
- The dataset was then cleaned further to remove rows with blank values in any of the columns. This resulted in 685 cryptocurrencies
- Next, the dataset was filtered to narrow it down to cryptocurrencies that have been **traded atleast once**. This resulted in 532 cryptocurrencies
- The coinname column was then split and stored in a separate dataframe since it was not required for the clustering
- From the resultant four columns, the two text columns Algorithm and Proof Type were converted to binary values using the get dummies function. This was considered as X and used for further analysis
- The data was scaled using **Standard Scaler** method
- The 98 dimensions were then reduced to 3 using **PCA** with a attribution of 0.03,0.02,0.02 for PC 1, PC 2, and PC 3 respectively
- The PCA data was stored in a dataframe and used for further analysis 
- To identify the number of clusters, an **elbow curve** was generated. From the curve, the number was clusters was narrowed down to 4

![image](https://user-images.githubusercontent.com/90650562/152714960-1a43335a-0da3-4a6a-a896-52a2342d350c.png)

- This value was applied to **KMean clustering** and the resultant labels were obtained
- The initial data, the PCA results and the results from clustering were stored in a dataframe

## Visualization
- The data from PCA was visualized as 3D scatter plot using plotly. From the visualization we can see that there are two predominant clusters

![image](https://user-images.githubusercontent.com/90650562/152719955-7b1afbca-9334-4def-b9fc-36ba6365c011.png)

- For easier analysis, the dataframe was converted to an interactive table with the provision to sort and select using **hvplot.table**

![image](https://user-images.githubusercontent.com/90650562/152720233-7796763f-9ed1-4879-b910-a07663e73fe9.png)

- To represent the data in 2D, two parameters, TotalCoinsMined and TotalCoinsSupply, were considered. The data was scaled using **MinMaxScaler** and displayed using hvplot

![image](https://user-images.githubusercontent.com/90650562/152720587-3ead0711-8880-4a1b-a44d-8cca79cdaa9b.png)





# Using Thematic Analyis and Sentiment Analysis to Predict Categorical Variables

## Project Overview and Hypothesis

<p>The goal of this project was to expand my abilities in analyzing qualitative data, specifically free-form text responses. Using Kaggle, I found a dataset that consists of approximately 42,000 free-form text reviews of three Disneyland parks that were webscrapped from the Trip Advisor website. My hypothesis was that I could use thematic analysis and sentiment analysis to create a K Nearest Neighbors model that could predict an associated categorical ranking assigned by the reviewer with reasonable accuracy.</p>

## Analysis Overview

<p>My analysis was completed in five main steps: Exploratory Data Analysis, Data Cleaning, Thematic Analysis & Sentiment Analysis, Preprocessing, and Modeling.</p>

## Exploratory Data Analysis

<p>The dataset from Kaggle consisted of approximately 42,000 records and 6 variables. Only two of the six variables included in the dataset, Rating and Review_Text, were relevant for the purposes of the analysis. Rating is a categorical variable that the reviewer picked when submitting their review on the Trip Advisor website where a 1 indicates that the visit was unsatisfactory and a 5 indicates that the visit was satisfactory.</p>

<p align="center">
<img width="400" alt="figure 1" src="https://github.com/JDRitenour/GMU-AIT664/assets/78283026/05249c41-f451-4323-8e21-facabc652134"><br />
Fig 1: Vertical Bar Chart of the Number of Reviews per Rating generated using Matplotlib in Python
</p>

<p>The Review_Text variable is the free-form text review that was written by the reviewer. The Rating variable was the target variable for the K Nearest Neighbor Model. Therefore, it was important to explore the distribution of the Rating variable across the dataset. Figure 1 above shows the distribution of the Rating Variable. From the graph, it is clear that the dataset contains an uneven distribution of the target variable with over half of the dataset containing a Rating of 5. This tells the modeler that they will need to take steps to even out the distribution of the target variable during preprocessing.</p>

## Data Cleaning

<p>To clean the data for this analysis, the dataset needed to be evaluated for missing values and duplicate values prior to performing the thematic analysis and the sentiment analysis. One of the challenges I ran into when evaluating the dataset for missing values is that the owner of the Kaggle dataset had imputed the null values with the string ‘missing’. This means when I searched the dataset for null values using the pandas isnull() function it returned no missing values. However, upon further exploration I discovered the use of the ‘missing’ value and used that to remove records with missing values from the dataset. The next goal was to remove duplicate values from the dataset. I used the drop_duplicates() function from pandas to remove the duplicate rows from the dataset. Prior to removing duplicate rows and rows with missing values, the dataset contained 42,656 records. After removing duplicate rows and rows with missing values, the dataset consisted of 40,014 records that would be used to generate data for the model.</p>

## Thematic Analysis & Sentiment Analysis

<p align="center">
<img width="400" alt="figure 2" src="https://github.com/JDRitenour/GMU-AIT664/assets/78283026/5902814f-b8f4-4b65-8335-8d47a0c0bb61"><br />
Fig 2: Unstacked Vertical Bar Chart of the number of Reviews per Rating and Dominant Theme generated using Seaborn in Python
</p>

<p>To generate data for the K Nearest Neighbor Model, I performed a thematic analysis and a sentiment analysis on the Review_Text column. For the thematic analysis, I used the LatentDirichletAllocation() model from Scikit-Learn to generate the five themes based on the dataset, and then evaluated each individual review to determine how much each review fit into each theme. The theme with the highest percentage match was then determined to be the review's dominant theme. Figure 2 above shows the distribution of the dominant themes across the dataset broken down by the Rating variable.</p>

<p>Next, I used the SentimentIntensityAnalyzer() model from NLTK to determine the amount of positive sentiment, neutral sentiment, and negative sentiment in each review. The SentimentIntensityAnalyzer() model also provides a sentiment compound score where -1 means the record is completely negative and +1 means the record is completely positive. The histogram in Figure 3 below shows the distribution of sentiment across the dataset which shows that the dataset is skewed positive. This is consistent with the findings in Figure 1 that shows that most of the reviews have a Rating of 5.</p>

<p align="center">
<img width="400" alt="figure 3" src="https://github.com/JDRitenour/GMU-AIT664/assets/78283026/be1b252c-2cd9-41af-a3b6-5e611e3e59d9"><br />
Fig 3: A Histogram of the Sentiment Score of the Reviews generated using Matplotlib in Python
</p>

## Preprocessing

<p>The next step of the analysis was to clean the new data created by the thematic analysis and the sentiment analysis, as well as preprocess the data for the model. To clean the data created by the thematic analysis and the sentiment analysis, I focused on removing outliers and multicollinearity from within the dataset. Removing outliers and multicollinearity is important because it removes noise from the dataset that can skew the results of a model.</p>

<p>To preprocess the data for modeling, I applied resampling techniques to even the distribution of the dataset. Ultimately, I used the resample() function from Scikit-Learn to apply an oversampling technique to increase the records in Ratings 1 - 4. Figure 4 below shows the distribution of the dataset after resampling.</p>

<p align="center">
<img width="400" alt="figure 4" src="https://github.com/JDRitenour/GMU-AIT664/assets/78283026/391e6c91-adc4-4e9c-a9b3-4d6d8812a040"><br />
Fig 4: A Bar Chart that shows the distribution of classes after Resampling was applied generated using Matplotlib in Python
</p>

## Modeling

<p>For my model, I built a k nearest neighbors model to try to predict the categorical Ranking associated with each review. To find the optimal k for the model, I ran the model on a range of k values from 1 to 50 (the results for each of these models can be seen in figure 5 below). I used k-fold cross-validation with k defined as 5. This means that the dataset was split into training and test sets 5 times using different data for each of the splits. The model is run on each of the splits and then the results are average together to get the results of the model. This process was performed for each value of k.</p>

## Model Accuracy

<p align="center">
<img width="600" alt="figure 5" src="https://github.com/JDRitenour/GMU-AIT664/assets/78283026/50395e05-0123-423b-b8be-11509af75919"><br />
Fig 5: A Line Plot showing the Accuracy for each K Value generated using Seaborn in Python
</p>

<p>Figure 5 above shows the accuracy score for each of the k values tested on the model. The optimal value for k was found to be 37 which produced an accuracy score of 60.5% My hypothesis was that a k-nearest-neighbor model could use data generated from a thematic analysis and a sentiment analysis to predict an associated categorical variable with reasonable accuracy. In order to evaluate the performance of my hypothesis, the definition of reasonable accuracy must be determined. An acceptable accuracy level for a model can vary widely depending on the model topic. However, generally models are considered reasonably accurate about 70%. Therefore, my model with an accuracy score of 60.5% did not predict the associated categorical variable with reasonable accuracy. Therefore, my hypothesis is incorrect.</p>

#### References

<p>Chillar, A. (n.d.). Disneyland Reviews. Kaggle. Retrieved October 27, 2023, from https://www.kaggle.com/datasets/arushchillar/disneyland-reviews</p>

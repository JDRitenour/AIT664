## Using Thematic Analyis and Sentiment Analysis to Predict Categorical Variables - Deliverable 1

### Focus Area

<p>For this project, I would like to explore what kind of knowledge can be gained from free-form text. When discussing data analytics, and specifically data visualizations, Natural Language Processing (NLP) is often left out of the conversation. This is because it can be very difficult to glean information from free-form text responses and convert that information into actionable knowledge. If a data analyst can develop their Natural Language Processing skills, however, they can be an asset to their team. When Natural Language Processing is done well, it can provide the decision maker with a clear understanding of either what is or is not working depending on the context of the review.</p>

<p>In an effort to develop my Natural Language Processing skills, I will be using topic modeling, word frequency analysis, and sentiment analysis to glean information from free-from text responses. Once the information has been extracted, it can be summarized in visualizations that are utilized to internalize the information and produce knowledge.</p>

### Dataset

<p>I have found a dataset on Kaggle that consists of 42,000 free-from text reviews of Disneyland California, Disneyland Paris, a Dinseyland Hong Kong that were webscrapped from Trip Advisor. Having grown up in Florida, most of my family vacations included a stop at the one and only Disney World park. However, I have never visited a Disneyland park. I am curious about what I can learn from the experiences of other visitors.</p>

<p>
The dataset consists of 6 variables that will assist in performing this analysis.
<ol>
  <li>The <strong>Review_ID</strong> variable is a unique numeric identifier that is assigned to each review./li>
  <li>The <strong>Rating</strong> variable is a categorical variable that is represented by a numeric value. The table below provides the definition of each category.</br>
<table>
  <tr>
    <th>5</th>
    <th>4</th>
    <th>3</th>
    <th>2</th>
    <th>1</th>
  </tr>
  <tr>
    <th>Satisfied</th>
    <th>Somewhat Satisfied</th>
    <th>Neutral</th>
    <th>Somewhat Unsatisfied</th>
    <th>Unsatisfied</th>
  </tr>
</table>
</li>
<li>The <strong>Year_Month</strong> variable indicates the year and the month that the review was posted on. This variable can be used to complete a time series analysis to see how the topics and the sentiment of the reviews change over time. It can also be used to set a baseline that can be used to compare new reviews against as tehy come in.</li>
  <li>The <strong>Reviewer_Location</strong> variable indicates the reviewer's country of origin. This can be used to compare topics and sentiment across different countries and regions.</li>
  <li>The <strong>Review_Text</strong> variable is the actual review left by the reviewer. It will be used for sentiment ana analysis, topic modeling, and word frequency analysis.</li>
  <li>Lastly, the <strong>Branch</strong> variable indicates the Disneyland branch that the review was left on.</li>
</ol>
</p>

<p>At first glance, the dataset appears to be very clean and well structured. Since this analysis will rely on Natural Language Processing, care will need to be taken during pre-processing to remove text that will not be beneficial to the analysis like special characters.</p>

### Initial Requirements

<p>This type of analysis could be utilized by the decision makers within the Disney organization. Free-form text responses allow decision makers to hear directly from the customer. Decision makers can use that information to reinforce what is working or as a starting point to launch initiatives to fix what is not.</p>

<p>My goal for this project is to explore the following questions:
<ul>
  <li>What are the top 5 topics mentioned in the reviews?</li>
  <li>How do the top 5 topics change based on the region the reviewer originates from, the numerical ranking associated with the review, and the park that the reviewer visited?</li>
  <li>How does the word frequency of review change based on the region the review originates from, the numerical ranking associated with the review, and the park that the reviewer visited?</li>
  <li>How does the sentiment of a review change based on the region the review originates from, the numerical ranking associated with the review, and the park that the reviewer visited?</li>
  <li>How does the top 5 topics, the word frequency or the sentiment change year over year or month over month?</li>
  <li>Does the sentiment of a review correlate with the numerical ranking?</li>
</ul></p>

### Hypothesis

<p>My hypothesis for this analysis is that using topic modeling we will be able to identify opportunities to improve the visitor experience in an attempt to reduce negative reviews in the future. I believe that we will be able to determine differences in topics and sentiments based on the date the review was left and the origin location of the reviewer. Lastly, I believe that we will see a correlation between the ranking variable and the sentiment of the review.</p>

### References

<p>Chillar, A. (n.d.). Disneyland Reviews. Kaggle. Retrieved October 27, 2023, from https://www.kaggle.com/datasets/arushchillar/disneyland-reviews</p>

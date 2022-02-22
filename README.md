# Twitter Sentment Analysis

![intro_img](./images/logos.JPG)

**Authors**: Czarina Luna, Marcelo Scatena, Piotr Czolpik, Ross McKim

## Overview

We are digital brand advisors that have been hired by South by Southwest. Our goal in this analysis is to do a proof of concept measure of the effect of the Apple pop up tent on twitter sentiment at the 2011 SXSW festival. In 2011 Apple released the Ipad 2 at the SXSW festival which makes this an ideal situation for analyzing first impressions of a small group of people.

* Atendees of technology festivals usually have a strong social presence
* First impressions of products can influence a great deal in sale numbers
* Sentiment analysis can help companies understand what they're doing right, and what they need to improve
***

## Business Problem

South by Southwest is primarily a film and music event and may not have expertise in analyzing social media postings but this measure of sentiment could help determine how much the event charges for booths, advertisements, and other commercial exposures. We are examining how effectively we can measure sentiment during such an event.
To accomplish this task we used a Machine Learning model that uses Natural Language Processing and distinguishes between positive, negative, or neutral sentiment in a tweet. The focus though is on being able to classify the highest amount of Negative sentiments, since they are the ones that may influence others that are still undecided on purchasing a product.
***

## Data

The information we have is regarding the 2011 South by Southwest festival that introduced the Ipad2. It is in data.world and can be found [here](https://data.world/crowdflower/brands-and-product-emotions). It contains over 9,000 tweets from users talking about the festival and it's products, and the sentiment of the tweet has been categorized by it being either positive, negative, neutral or unable to tell.
There is a big imbalance of results in that regard, and another one when taking into consideration which products those sentiments are regarding.

***

## Methods & Evaluation Metrics
 
 * The dataset contains only three features: one is the text from the tweet, one our target, one a product that the tweet regarded. This is a perfect example of where Natural Language Processing can be used.

 The text data from the tweet are not very easily understandable. A lot of tweets don't follow a proper english phrase sequencing, and they're filled with hashtags, mentions, links, tags, retweets, and other occurances that we had to take into account in our preprocessing. 
 This eare some of the methods we used in the cleaning process:
  - Lower casing
  - Removal of non-ascii characters
  - Removal of urls
  - Removal of tagging
  - Removal of punctuation and special characters
  - Removal of common stopwords
  - Removal of specific stopwords
  - Lemmatization

As far as our evaluation metric goes, we first chose a baseline mode in regards to it's accuracy, then chose first to focus on Precision, since it cares about the number of False Negatives we get. Given this multi classification problem though, we decided that finding out thos tweets with negative sentiment towards your brand is the most important thing, and chose to adopt that as a metric.
***
## Results

* Models performance by accuracy

<img src="./images/skyler_graph.JPG" alt="models performances" height="420"/>

The overall accuracy of the models doesn't change all that much from the baseline. We managed to accrue and improvement from around 65% in the baseline to 71% in the tuned SGD. We've chosen to use the tuned Extra Trees model though, given it's lower ratio for mislabeling Negative Sentiment as Positive.

* Confusion Matrix for Extra Tree model

<img src="./images/extra_trees_cm.JPG" alt="confusion matrix for extra trees model" height="420"/>

Here we have reduced to only around 7% the model mislabeling of Negative Sentiment as Positive ones, and that while maintaining an around 37% correct labeling of Positive Sentiment as Positive, which is another important factor given our reccommendation of retweeting Positive Sentiment tweets.

* Below we can see Word Clouds of the positive and negative sentiments from the whole dataset, and the ones regarding sentiment towards Apple and Google

<img src="./images/positive_wordcloud.JPG" alt="positive cloud" height="400"/>  <img src="./images/negative_wordcloud.JPG" alt="negative cloud" height="400"/>



<img src="./images/apple_wordcloud.JPG" alt="drawing" height="390"/>  <img src="./images/google_wordcloud.JPG" alt="drawing" height="390"/>



* We've also created word clouds of positive and negatives sentiments towards Apple and Google, to give us an insight on what people are and are not liking about the companies:

 <img src="./images/apple_positive.JPG" alt="apple positive cloud" height="370"/>  <img src="./images/apple_negative.JPG" alt="apple negative cloud" height="370"/> 

 <img src="./images/google_positive.JPG" alt="google positive cloud" height="390"/>  <img src="./images/google_negative.JPG" alt="google negative cloud" height="390"/> 


* Latent Dirichlet Allocation
We performed LDA to see how it would cluster the data given our specifications. Below you can see the graph with all our data, where Google and Ipad where slected by the lda as our two latent topics, and the words with the highest likelihoods of pointing towards one of those clusters.

<img src="./images/lda.JPG" alt="lda" height="420"/>

The full notebook on LDA can be found [here](./LDA.ipynb)

***

## Conclusions

Given our sentiment results, we have the following reccommendations for South by Southwest:

* Give brands feedback on their negative sentiments
  - When a brand has information on what are the products and features people have negative sentiment towards, they can make more targeted research and propose changes to those products. This would give the company a first layer of feedback so they can follow with more research.
* Retweet positive tweets
  - The more people positive comments can reach, the better. A team of people retweeting relevant tweets could significantly increase their reach. We'd also suggest prioritizing accounts that have a large amount of followers and are more active online than not.
* Investigate negative tweets
  - Are these directed at a specific product? A Brand? A flaw in the organization of the festival? Finding the answers to those questions should open venues for improvement.
***
## Next Steps

Following the delivery of our model, we suggest South by Southwest:
* Conduct sentiment analysis prior and after an event
  - Gauging sentiment towards a brand or product before and after an event can give the company an estimation on how positive or negative that event was for that brand or product, allowing them to make changes to future events based on these findings.
* Correlate sentiment analysis with product sales
  - Companies can see if sentiment towards a certain product have a correlation with said product sales. If it does, that could give them another tool to predict future sales based on sentiment.

## For More Information

Please review our full analysis in [our Jupyter Notebook](./final_notebook.ipynb) or our [presentation](./final_presentation.pdf).

For any additional questions, please contact<br />
Czarina Luna: [LinkedIn](https://www.linkedin.com/in/czarinaluna/) | Email: czarinagarcialuna@gmail.com<br />
Marcelo Scatena: [LinkedIn](https://uk.linkedin.com/in/marcelo-scatena) | Email: marcelo.oddo@gmail.com<br />
Ross McKim: [LinkedIn](https://www.linkedin.com/in/ross-mckim) | Email: rmckim@gmail.com<br />
Piotr Czolpik: [LinkedIn](https://www.linkedin.com/in/piotr-czolpik-803119111) | Email: Piotrczo1992@gmail.com<br />

## Repository Structure

```
├──────────individual_notebooks ├─ Marcelo_Notebook.ipynb
├── README.md                   ├─ Czarina_EDA_Modeling.ipynb  
├── final_notebook.ipynb        ├─ Piotr_Notebook.ipynb
├── final_presentation.pdf      ├─ Ross_Notebook.ipynb
├── GridSearchCV.ipynb
├── Clustering.ipynb
├── lda.ipynb
├── data                                
└── images                              
```

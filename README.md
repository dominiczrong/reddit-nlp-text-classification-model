# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Reddit NLP Text Classification Model

### Problem Statement

Being part of the Data Science Marketing Team of a coding bootcamp, I am interested in finding out what popular topics and keyword jargons belong to the fields of Data Science and Software Engineering. Conducting analysis on Reddit posts will allow me to craft online content and advertisements to better target people interested in Data Science or Software Engineering.

The main objective of this project is to scrape two subreddits: `Software Engineering` and `Data Science` through a webscrapper, leveraging on Reddit's API. The scraped data from the two subreddits will then be passed through various classification models, `CountVectorizer/TfidVectorizer` with `Naive Bayes Classifier`, `LogisticRegression`, `Random Forest`, `KNeighbours` and `Support Vector Classifier` that will assign each observation to the most likely class of subreddit. The models should help the data science marketing team of my company identify what makes the respective subreddit posts unique from one another.

In this process, the subreddit posts will undergo preprocessing and EDA. The success of the models that we decide on will be determined through the highest accuracy based on the scores obtained.

---

### Executive Summary

Natural Language Processing, or NLP for short, involves using specialized machine learning techniques to make predictions about the text in a body of documents, including things like authorship attribution, sentiment analysis, text generation, and in some cases the appearance of something resembling semantic understanding.

Career paths like Software Engineering and Data Science have become the most in-demand fields for many people in this rapidly changing world. Within these career paths, there are many terms and topics that are similar given the cross-sectionality of both jobs. However, there are still some aspects in Data Science jobs that differ from Software Engineering jobs and vice versa.

In this project, I would like to further explore the key similarities and differences between Data Science and Software Engineering in terms of the current discussions and topics that people are discussing on Reddit. Reddit, in recent times, have become a popular avenue for people all over the world to ask one another about different career prospects and experiences. As such, scraping Subreddit Posts gives us an interesting source of data that we can analyze to understand what are the popular topics in these respective career fields.

The web scraping portion of this project is covered in another notebook. In this notebook, I will be covering the steps taken to clean and analyze the data collected, as well as further steps taken to pre-process the text data, visualize the data, use different models to find the optimal model and analyze misclassified posts.

---

### Contents

- [Data Collection](#Data-Collection)
- [Data Cleaning](#Data-Cleaning)
- [Explanatory Data Analysis](#Explanatory-Data-Analysis)
- [Pre-Processing](#Pre-Processing)
- [Data Visualization](#Data-Visualization)
- [Modelling](#Modelling)
- [Evaluation](#Evaluation)
- [Conclusion](#Conclusion)
- [Recommendations](#Recommendations)

---

### Explanatory Data Analysis

Word Cloud Plots - Most Common Words in Data Science and Software Engineering Subreddit Posts

<img src="https://github.com/dominiczrong/dsiprojects/blob/master/project_3/images/wordcloud_ds.png" width="600" height="400"/>

<img src="https://github.com/dominiczrong/dsiprojects/blob/master/project_3/images/wordcloud_swe.png" width="600" height="400"/>


Cross-Intersection Overview of Most Common Words among both Subreddits

<img src="https://github.com/dominiczrong/dsiprojects/blob/master/project_3/images/Venn_Diagram.png" width="400" height="400"/>

---

### Summary of Results

<img src="https://github.com/dominiczrong/dsiprojects/blob/master/project_3/images/Summary_Results.png" width="800" height="400"/>

1. After running our data through 10 possible model combinations, I managed to achieve the **highest accuracy (testing) score of 88.8%** in predicting which subreddit a post came from using the `MultinomialNB` - `CvecVectorizer` model combination. The rest of the model scores are as follows:
    - **Specificity**: 92.8%
    - **Precision**: 83.7%
    - **Misclassification Rate**: 11.2%
    - **ROC/AUC Score**: 93.8%


2. Using GridSearchCV, the best hyperparameters for this particular model is:
    - 'cvec__max_df': 0.6,
    - 'cvec__max_features': 2000,
    - 'cvec__min_df': 2,
    - 'cvec__ngram_range': (1, 1),
    - 'nb__alpha': 0.25}


3. Our model has successfully classified most of the cases to the correct subreddit, in fact, up to 88.8% of the subreddit posts. However, I also have discussed on the importance of reducing the number of False Negative (Type-II error), but the reduction has to be done at the cost increasing False Positive (Type-I error). The trade-off can be seen from our AUC-ROC Curve Diagram. With 88.8% accuracy, our data science marketing team will be able to better target people interested in these topics using certain prominent keywords that appear more frequently in one subreddit over the other and vice versa.


4. From our Data Visualizations and Misclassified Post Analysis, we have identified Data Science Subreddit to have key words like `model`, `scientist`, `python`, `question`. On the other hand, Software Engineering Subreddit appears to have key words like `code`, `develop`, `start`, `engin`. Understanding the importance of these words in subreddit posts allows the models to better predict which posts belong to which subreddits.

---

### Conclusion and Recommendations

1. When it comes to modelling, have more rows of data will improve our modelling accuracy scores. To increase our data size, one other area where we can scrape mmore text data is scraping the comments section of subreddit threads. This can be done using other APIs.


2. To reduce our misclassification rate for our models, we can identify common words that appear within both subreddits that contribute to the misclassification of posts and remove such words during our pre-processing stage when cleaning our data. This was not done in the scope of this project but could be done to further improve our model scores in the future.

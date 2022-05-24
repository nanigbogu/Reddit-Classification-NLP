# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Reddit

## Executive Summary

HelloFrezh is a meal delivery kit service that offers food plans for different lifestyles but now wants to target different diets, including ketogenic and vegan diets. Keto is a high fat, moderate protein, and low carbohydrate diet that forces the body to use fat as its main energy source instead of carbohydrates. Most people go on this diet for weight loss purposes but sometimes doctors prescribe it to children with epilepsy. Veganism is the practice of abstaining from all animal products including eggs and dairy. It is a plant based lifestyle and typically is followed for nutritional, religious, ethical, and/or environmental purpose. If you want to learn more about either diet, click [here](https://www.eatingwell.com/article/7874433/vegan-vs-keto-how-do-these-two-diets-compare/).

HelloFrezh is launching new food plans to cater to Keto and Vegan diets. They want to build a marketing plan and create a slogan that aligns with each diet community. We will explore the titles and posts from keto and vegan subreddits to determine what language is more likely to be used in each community and test if it is possible to get accurate classifications for each slogan before launching. Success will be defined by the accuracy score and proper classification of a given slogan.
    
In order to create a model that will classify slogans and predict an accuracy score higher than the baseline, we need to collect and prepare the data. Data was gathered using PushShift Reddit API with a total of 6,000 keto posts and 12,000 vegan posts. Data was cleaned of null values from selftext column, removed posts, emojis and conjoined lines were separated which reduced DataFrame to 3,550 entries. A column that combined titles and posts was feature engineered to be used as the independent variable. Now that the data is cleaned, it is time to make a model. The classifiers used to find the best model include logistic regression, k-nearest neighbors, random forest, and ADABoost in combination with a CountVectorizer transformer. Each classifer was able to beat the baseline accuracy score of 53%. The best model for this problem utilized Logistic Regression because it showed little variance, had an accuracy score of 96%, and was able to classify the given slogan into the respective subreddit. The hyperparamters were tuned through trial and error to achieve the best score on accuracy rate. 
    
Although there were a few models that performed successfuly, the CountVectorizer + Logistic Regression model produced the highest accuracy score with proper classification of the given slogans which is going to help optimize HelloFrezh's marketing plan for their target audience. The company will utilize some of the top 10 features from this model that show a strong correlation with each class in their final marketing plan. Some of these words include keto, carbs, vegan, and animal. When developing further slogan's they should test whether their slogan would classify with either keto or vegan subreddits to ensure the language aligns with the community. If they wish to improve the model, they can do further data cleaning such as removing urls or polls, use a RandomSearchCV or GridSearchCV to tune hyperparameters, and test other models such as Naive Bayes or create an ensemble. 

---

### Datasets

#### Train and Test Datasets

* [`Keto.csv`](./data/keto.csv): Keto dataset 
* [`Vegan.csv`](./data/vegan.csv): Vegan dataset
* [`Keto_Vegan.csv`](./data/keto_vegan.csv): Keto and Vegan dataset combined


---

### Data Dictionary

|Feature|Type|Datasets|Description|
|---|---|---|---|
|**subreddit**|*object*|vegan & keto & keto_vegan|Respective subreddits/ our classes| 
|**title**|*object*|vegan & keto & keto_vegan|Title of respective subreddit post|  
|**selftext**|*object*|vegan & keto & keto_vegan|The actual subreddit post or content|  
|**created_utc**|*integer*|vegan & keto & keto_vegan|The time the subreddit post was created|   
|**title_posts**|*object*|keto_vegan|The title and selftext columns combined|
|**title_length**|*integer*|keto_vegan|Length of title by character|  
|**post_length**|*integer*|keto_vegan|Length of post by character|  

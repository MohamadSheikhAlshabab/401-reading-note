# Readings: Machine Learning Intro [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read16.md)

## Data Science Primer:

  - ## Chapter 1: Bird's Eye View:
    - ![img](https://elitedatascience.com/wp-content/uploads/2018/05/What-Goes-Into-a-Successful-Model.jpg) 
    - This data science primer will cover exploratory analysis, data cleaning, feature engineering, algorithm selection, and model training. 
    - What makes machine learning so special?
      - Machine learning is the practice of teaching computers how to learn patterns from data, often for making decisions or predictions.
      - Model - a set of patterns learned from data.
      - Algorithm - a specific ML process used to train a model.
      - Training data - the dataset from which the algorithm learns the model.
      - Test data - a new dataset for reliably evaluating model performance.
      - Features - Variables (columns) in the dataset used to train the model.
      - Target variable - A specific variable you're trying to predict.
      - Observations - Data points (rows) in the dataset.
      - __Machine Learning Tasks__:Academic machine learning starts with and focuses on individual algorithms.
      - However, in applied machine learning, you should first pick the right machine learning task for the job.
      - categories of tasks are supervised learning and unsupervised learning.
      - __The Blueprint__:
          - 1 - Exploratory Analysis: First, "get to know" the data. This step should be quick, efficient, and decisive.
          - 2 - Data Cleaning: Then, clean your data to avoid many common pitfalls. Better data beats fancier algorithms.
          - 3 - Feature Engineering: Next, help your algorithms "focus" on what's important by creating new features.
          - 4 - Algorithm Selection: Choose the best, most appropriate algorithms without wasting your time.
          - 5 - Model Training: Finally, train your models. This step is pretty formulaic once you've done the first 4.
      - there are other situational steps as well:
          - S - Project Scoping: Sometimes, you'll need to roadmap the project and anticipate data needs.
          - W - Data Wrangling: You may also need to restructure your dataset into a format that algorithms can handle.
          - P - Preprocessing: Often, transforming your features first can further improve performance.
          - E - Ensembling: You can squeeze out even more performance by combining multiple models.
     - ## Chapter 2: Exploratory Analysis:
        - Why explore your dataset upfront?
        - The purpose of exploratory analysis is to "get to know" the dataset. 
        - in 3 main ways:
          - You’ll gain valuable hints for Data Cleaning (which can make or break your models).
          - You’ll think of ideas for Feature Engineering (which can take your models from good to great).
          - You’ll get a "feel" for the dataset, which will help you communicate results and deliver greater impact.
        -  exploratory analysis for machine learning should be quick, efficient, and decisive... not long and drawn out!
        - Start with Basics:
          - How many observations do I have?
          - How many features?
          - What are the data types of my features? Are they numeric? Categorical?
          - Do I have a target variable?
        - __Plot Categorical Distributions__:
          - Categorical features cannot be visualized through histograms. Instead, you can use bar plots.
          - In particular, you'll want to look out for sparse classes, which are classes that have a very small number of observations.
          - By the way, a "class" is simply a unique value for a categorical feature. 
          - ![img](https://elitedatascience.com/wp-content/uploads/2017/06/grouping-sparse-classes-before.png)
          - when building models.
            - In the best case, they don't influence the model much.
            - In the worse case, they can cause the model to be overfit.
        - __Plot Segmentations__:
          - The median transaction price (middle vertical bar in the box) for Single-Family homes was much higher than that for Apartments / Condos / Townhomes.
          - The min and max transaction prices are comparable between the two classes.
          - In fact, the round-number min ($200k) and max ($800k) suggest possible data truncation...
          - ...which is very important to remember when assessing the generalizability of your models later!
          - ![img](https://elitedatascience.com/wp-content/uploads/2017/06/boxplot-segmentation-example.png)
          ---
       - ## Chapter 3: Data Cleaning
         - Proper data cleaning is the “secret” sauce behind machine learning.
         - Better data beats fancier algorithms…
         -  If you have a clean dataset, even simple algorithms can learn impressive insights from it!
       - ## Chapter 4: Feature Engineering:
         - In a nutshell, “feature engineering” is creating new model input features from your existing ones.
         - To start, feature engineering is very open-ended. There are literally infinite options for new features to create.
         - Plus, you’ll need domain knowledge to add informative features instead of more noise.
       - ## Chapter 5: Algorithm Selection:
         - our goal is to explain a few essential concepts (e.g. regularization, ensembling, automatic feature selection) that will teach you why some algorithms tend to perform better than others.
         - In applied machine learning, individual algorithms should be swapped in and out depending on which performs best for the problem and the dataset.
         - We have two main goals:
           - 1 - To explain powerful mechanisms in modern ML.
           - 2 - To introduce several algorithms that use those mechanisms.
      - ## Chapter 6: Model Training:
        - data scientists actually do spend most their time on the earlier steps:
           - 1 - Exploring the data.
           - 2 - Cleaning the data.
           - 3 - Engineering new features.
        - Now you'll learn how to maximize model performance while safeguarding against overfitting.
        - Plus, you'll learn how to automatically find the best parameters for each algorithm.
    ---
     # Python Data Wrangling Tutorial: Cryptocurrency Edition:
       - Step 1: Set up your environment.
         - installed on your computer:
           - 1 - Python 2.7+ or Python 3
           - 2 - Pandas
           - 3 - Jupyter Notebook (optional, but recommended)
       - Step 2: Import libraries and dataset.
         - <pre># Pandas for managing datasets</pre>
         - <pre>import pandas as pd</pre>
         - Data Dictionary (for code GWA_BTC):
           -  Date: The day on which the index values were calculated.
           -  Open: The day's opening price index for Bitcoin in US dollars.
           -  High: The highest value for the price index for Bitcoin in US dollars that day.
           -  Low: The lowest value for the price index for Bitcoin in US dollars that day.
           -  Close: The day's closing price index for Bitcoin in US dollars.
           -  Volume: The volume of Bitcoin traded that day.
           -  VWAP: The volume weighted average price of Bitcoin traded that day.
           -  TWAP: The time-weighted average price of Bitcoin traded that day.
         - Step 3: Understand the data.
           - Generally, all observations should be equivalent in granularity and in units.
           - Equivalence in Granularity
           - Equivalence in Units
           - __MWA__ stands for "market-weighted average," and they show regional prices. 
           - There are multiple MWA codes for each cryptocurrency, one for each local fiat currency.
           - On the other hand, GWA stands for "global-weighted average," which shows globally indexed prices.
           - __GWA__ is thus an aggregation of MWA and not equivalent in granularity.
         - Step 4: Filter unwanted observations.
           - One of the simplest yet most useful data wrangling techniques is removing unwanted observations.
         - Step 5: Pivot the dataset.
         - Step 6: Shift the pivoted dataset.
           - we can use Pandas's shift method.
           - This function shifts the index of the dataframe by some number of periods. 
         - Step 7: Melt the shifted dataset.
         - Step 8: Reduce-merge the melted data.
         - Step 9: (Optional) Aggregate with group-by.
   ---
   # Hello World - Machine Learning Recipes #1
     - Open source libraries:
       - 1 - scikit-learn
       - 2 - TensorFlow
    - Supervised learning: create a classifier by finding patterns in examples you want to solve.
    - Supervised learning recipe:
      - 1 - ollect training data
      - 2 - train classifier.
      - 3 - make predictons.
    - features are input to the classifier.
    - labels are the output we want.
    
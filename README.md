
# Comparing Google and Apple Store's reviews


<p align="center">
  <img width="600" height="300" src="https://www.mobileaction.co/blog/wp-content/uploads/2014/07/app-store-vs-google-play.jpg?x38980">
</p>

## 1. Introduction:

Did Apple Store apps receive better reviews than Google Play apps?

## Stages of the project

1. Sourcing and loading 
    * Load the two datasets
    * Pick the columns that we are going to work with 
    * Subsetting the data on this basis 
 
 
2. Cleaning, transforming and visualizing
    * Check the data types and fix them
    * Add a `platform` column to both the `Apple` and the `Google` dataframes
    * Changing the column names to prepare for a join 
    * Join the two data sets
    * Eliminate the `NaN` values
    * Filter only those apps that have been reviewed at least once
    * Summarize the data visually and analytically (by the column `platform`)  
  
  
3. Modelling 
    * Hypothesis formulation
    * Getting the distribution of the data
    * Permutation test 


4. Evaluating and concluding 
    * What is our conclusion?
    * What is our decision?

## 2. Datasets: Sourcing and Loading

The source is Kaggle. The data from the Apple Store can be found [here](https://www.kaggle.com/ramamet4/app-store-apple-data-set-10k-apps) and the data from Google Store can be found [here](https://www.kaggle.com/lava18/google-play-store-apps).

<p align="center">
  <img width="1000" height="200" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img1.png">
</p>

## 3. Cleaning, transforming and visualizing

**Checking the data types for both Apple and Google, and fixing them**

Types are crucial for data science in Python. Let's determine whether the variables we selected in the previous section belong to the types they should do, or whether there are any errors here. 

<p align="center">
  <img width="1000" height="800" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img2.png">
  <img width="1000" height="800" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img3.png">
</p>

**Add a `platform` column to both the `Apple` and the `Google` dataframes**

Let's add a new column to both dataframe objects called `platform`: all of its values in the Google dataframe will be just 'google', and all of its values for the Apple dataframe will be just 'apple'. 

The reason we're making this column is so that we can ultimately join our Apple and Google data together, and actually test out some hypotheses to solve the problem in our brief. 

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img4.png">
</p>

**Changing the column names to prepare for our join of the two datasets**

Since the easiest way to join two datasets is if they have both:
- the same number of columns
- the same column names
we need to rename the columns of `Apple` so that they're the same as the ones of `Google`, or vice versa.

In this case, we're going to change the `Apple` columns names to the names of the `Google` columns. 

This is an important step to unify the two datasets!

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img5.png">
</p>

**Joining the two datasets**

Let's combine the two datasets into a single data frame called `df`.

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img6.png">
</p>

**Eliminating the NaN values**

As you can see there are some `NaN` values. We want to eliminate all these `NaN` values from the table.

<p align="center">
  <img width="1000" height="500" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img7.png">
</p>


**Filtering the data so that we only see whose apps that have been reviewed at least once**

Apps that haven't been reviewed yet can't help us solve our brief. 

So let's check to see if any apps have no reviews at all. 

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img8.png">
</p>

**Summarizing the data visually and analytically (by the column `platform`)**

What we need to solve our brief is a summary of the `Rating` column, but separated by the different platforms.

<p align="center">
  <img width="1500" height="1000" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img9.png">
</p>

## 3. Modeling

**Hypothesis formulation**

Our **Null hypothesis** is just:

**H<sub>null</sub>**: the observed difference in the mean rating of Apple Store and Google Play apps is due to chance (and thus not due to the platform).

The more interesting hypothesis is called the **Alternate hypothesis**:

**H<sub>alternative</sub>**: the observed difference in the average ratings of apple and google users is not due to chance (and is actually due to platform)

We're also going to pick a **significance level** of 0.05. 

**Getting the distribution of the data**

Now that the hypotheses and significance level are defined, we can select a statistical test to determine which hypothesis to accept. 

There are many different statistical tests, all with different assumptions. You'll generate an excellent judgement about when to use which statistical tests over the Data Science Career Track. But in general, one of the most important things to determine is the **distribution of the data**.   

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img10.png">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img11.png">
</p>

**Permutation test**

Since the data aren't normally distributed, we're using a *non-parametric* test here. This is simply a label for statistical tests used when the data aren't normally distributed. These tests are extraordinarily powerful due to how few assumptions we need to make.  

Check out more about permutations [here.](http://rasbt.github.io/mlxtend/user_guide/evaluate/permutation_test/)


<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img12.png">
</p>

## 4.  Evaluating and concluding

<p align="center">
  <img width="600" height="400" src="https://raw.githubusercontent.com/mohamedziane/Google-Vs.-Apple-Reviews-Statistical-Inference-Tests/main/images/img13.png">
</p>

So actually, zero differences are at least as extreme as our observed difference!

So the p-value of our observed data is 0. 

It doesn't matter which significance level we pick; our observed data is statistically significant, and we reject the Null.

We conclude that platform does impact on ratings. Specifically, we should advise our client to integrate **only Google Play** into their operating system interface. 

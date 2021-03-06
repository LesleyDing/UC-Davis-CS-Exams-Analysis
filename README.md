# Probabilistic and Statistical Modeling Project
## Detailed Description:
[Click Here](https://github.com/KangboLu/UC-Davis-CS-Exams-Analysis/blob/master/ECS132_TermProject.pdf)

![Word Cloud for ECS132 Exams](https://github.com/KangboLu/UC-Davis-CS-Exams-Analysis/blob/master/ECS132.jpeg "WordCloud")

## First release of 132 term project:
* ProblemA.R accomplished statistical analysis on ECS132, ECS145, and ECS154 students' quiz average from University of California at Davis.
* ProblemB.R gathered, cleaned, and organized training data (previous exams) into document term matrix for creating 9 logistic models for 9 courses. The 9 models are used to predict which course does the test data (exam) belongs to.

## Task A

Here you will do some statistical analysis on my undergrad quiz data, with a Description goal. Here are the details:

*   I have made available [data](ProblemAData/) on the following for each student:
    *   Course name. We will have ECS 132, 145 and 158.

    *   Year/quarter offered. E.g. 2012.1 is Winter 2012, 2015.3 is Fall 2015\. This data will be used to determine whether there has been some time trend in my quiz grades in recent years.

    *   Student major (CS, CSE only).

    *   Overall quiz average.

    Please note: A very important part of your job will be to take the data in the form I provide it, and create one big R data frame, with columns 'course name', 'year offered', 'major' and 'quiz average'. Use R's **read.table()** or some other R function to read the original data from our Web site, then other R code to create the data frame and work with it. **You are required to use R for all aspects of this, and explain in your report what you did in this regard.**

*   Do the following analyses:
    *   Assuming no time trend, find approximate 95% confidence intervals for the population mean quiz average for each of the four courses. Comment.

    *   Assuming no time trend, find an approximate 95% confidence interval for the difference in population mean quiz averages for ECS 132 and 145\. Comment.

    *   Assuming no time trend, find an approximate 95% confidence interval for the difference in population mean quiz averages in ECS 145 between the two majors. Comment.

    *   Fit a linear regression model in which quiz average is predicted from year, course and major. For the last two, create dummy variables (Sec. 21.12). Use this to determine whether there is a substantial time trend. Also use it to compare ECS 132 and 145, and CS majors to CSE. (This is different from above, because now we are adjusting for a possible time trend.)

    *   Do an analysis of your choice (justified!) that investigates whether there is a time trend in the proportion of CS majors in our department, based on this data.

## Task B

Here you will do some predictive modeling (machine learning), involving text data. One active branch of this field is text classification, e.g. sentiment analysis. We will be less ambitious here, but the principles are the same. Here are the details.

*   The data consists of all files in [my course Web page site](http://heather.cs.ucdavis.edu/~matloff/) with names of the form **1*/*Exams/*tex** , **2*/*Exams/*tex** or **50/*Exams/*tex** . (Go into one directory level within ***Exams**).

*   As in Problem A, provide and explain your complete R code for fetching the data and for your analyses.

*   This will be a classification problem, as in Chapter 16\. The classes here will be...classes! You will predict the class, i.e. one of ECS 50, 132, 145, 152A, 154A, 154B, 156, 158, 188 and 256 from the words present in an exam.

*   You will use the _logistic_ model, fitting 10 logit models, one for each class. The predictor variables are counts of specific words. For a given new case, you plug the word counts into the logit function, giving you an estimated conditional probability of that class. Whichever class has the highest conditional probability, you guess this case to be in that class.

*   The criterion here is prediction accuracy: What proportion of new cases is predicted correctly? To simulate having new cases, it is customary to divide one's data into a _training_ set and a _test_ set. We fit our models to the training set, then predict the test test, pretending that we don't know the classes of the test set. We of course do know their classes, so we can evaluate the proportion of our predictions that come out correct. There are something like 293 exams in the above directories; you will choose 50 at random for your test set (sometimes called the _holdout_ set).

*   You will use R's **glm()** function to fit the logit models, as in Chapter 11\. Your data will consist of an R matrix or data frame, one row per exam in the training set. All but one of the columns will be word counts, with the remaining one being an indicator variable for the class of interest (1 for being in the class, 0 not).

*   A major issue is how to get the word counts. You will use R's **tm** package, which removes punctuation, white space etc. You can get counts from the output. You will decide what to remove and what not, including the issue of whether to remove the LaTeX keywords. There are lots of tutorials on **tm** on the Web. Explain your decision on this thoroughly in your report.

*   The other major issue is _which_ words to use. This is hard. A rough rule of thumb is to use no more than sqrt(n) predictor variables, where n is the number of cases in the training set, thus no more than sqrt(n) word counts here. But which ones? Explain your decision on this thoroughly in your report.

*   This is another of those assignments in which you at first will have little or no idea as to what to do. Give it a lot of thought, and discuss it vigorously in your group. Your solution will gradually take shape. Of course, feel free to ask Robin or me if you get stuck and you are not sure about something.

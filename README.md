# Missing Data Imputation Using misForest Algorithm

## Abstract
These days, data acquisition based on cutting-edge technology is often confronting the missing data issue. Algorithms commonly used in the analysis of such large-scale data often depend on a complete set. Missing data imputation methods suggest a solution to this problem. However, most available imputation methods are restricted to one type of variable only: continuous or categorical. For mixed-type data, the different types are usually handled separately. Therefore, these methods ignore possible relations between variable types. “missForest” is used to impute missing values, particularly in mixed-type data.

This study evaluates an iterative imputation method based on a random forest (RF). Using the built-in out-of-bag error estimates of random forest, we can estimate the imputation error without the need for a test set. Evaluation is performed on three real data sets with artificially introduced missing values ranging from 10% to 30%. This study also compares the missForest performance to the Multiple Imputation Chained Equation (MICE) by [Van Buuren and Oudshoorn (1999)](https://stefvanbuuren.name/publications/Flexible%20multivariate%20-%20TNO99054%201999.pdf) on three data sets. The results show that missForest can successfully handle missing values, particularly in datasets including different types of variables. The out-of-bag imputation error estimates of missForest prove to be adequate in all settings. Additionally, missForest exhibits attractive computational efficiency and can cope with high-dimensional data, while the MICE has some difficulties. In comparison, missForest outperforms the MICE method of imputation, especially in data settings where complex interactions and non-linear relations are suspected.

## Introduction
In most scientific investigations involving data analysis, presence of missing data is a common issue, and determining the right approach to mitigate this often becomes a major challenge. If the researcher does not appropriately handle the missing values, then he/she may end up drawing an inaccurate inference about the data.

To handle missing values, one can use deletion techniques wherein certain records containing variables with missing values are not considered for analysis. In order to avoid this, various kinds of imputation methods have been proposed such as [missForest algorithm](https://academic.oup.com/bioinformatics/article/28/1/112/219101) based on a [Random Forest](https://www.researchgate.net/publication/228451484_Classification_and_Regression_by_RandomForest) machine learning method.

This study is motivated to examine a method of imputation which can handle any type of input data and makes as few as possible assumptions about structural aspects of the data. Random forest is able to deal with mixed-type data and as a non-parametric method it allows for interactive and non-linear (regression) effects.

The main focus of this study is on missForest algorithm performance. The comparative part is considered to compare missForest and MICE algorithms with a view to discovering strong aspect of missForest. The comparative part of the study helps to define the organization structure of the subjects.

The study is organized as follows: Section I is a brief introduction to the problem. Section II presents the review of existing literature dealing with missing data, Section III presents the methods that are using in this study, Section IV details out the results and findings, Section V concludes the study. The last section is also the references. The vast majority of content has been removed. For more detail, please contact the author (me).

## Mixed-type Variable Data set
In the following, three datasets with mixed-type variables (continuous and categorical) are selected to implement the missForest algorithm on them.
- **hprice**
- **iris**
- **import85**

The analysis is done in *R software version 1.4.1106* with the help of the missForest, MICE, and faraway packages mainly. In the first step, some values are eliminated at random from 10%, 20%, and 30%. Missing at Random (MAR) is a mechanism to get rid of some values from the data set in this study. Next, the missForest function is employed to estimate the missing values and assess the quality of imputations. Then, imputation errors are derived through the OOBerror value. In MICE procedure, mice function is used to estimate the missing values. The imputed data sets are evaluated by the mixError function. This function computes imputation error, particularly in the case of mixed-type data.

## Conclusion
missForest allows for missing value imputation on basically any kind of data. In particular, it can handle multivariate data consisting of continuous and categorical variables simultaneously. MissForest does not need tuning parameters, nor does it require assumptions about distributional aspects of the data. However, the number of trees necessary for good performance grows with the number of predictors. For selecting the number of trees, the default is the root square of predictors’ numbers. We tried the default, half of the default, and twice the default. In our data sets, the results do not change meaningfully. Even when the number of trees considered as 1, it gave an outstanding performance.

In a comparative part, the missForest results were compared with MICE to show that missForest is an excellent strategy to deal with missing values; however, MICE is also a good method to handle mixed-type missing values. Moreover, while missForest can be applied to high-dimensional datasets and provides excellent imputation results, other algorithms like MICE may fail to do so.



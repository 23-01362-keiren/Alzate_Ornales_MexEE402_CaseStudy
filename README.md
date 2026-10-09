# Alzate_Ornales_MexEE402_CaseStudy

# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Alzate, Sheremel Keiren | 23-01362 | MEXE 4101 |
| Ornales, Rovic Ythan Gabrielle | 23-07559 | MEXE 4101 |

## Notebook links

| Chapter | Alzate | Ornales |
|---|---|---|
| Ch1_2_3 | [link](https://colab.research.google.com/drive/17QZ9Z8kWKwYlLnQS3yCXBJOFUIKd1oKR?usp=sharing) | |
| Ch4 | [link](https://colab.research.google.com/drive/1Sr-ljDMZwB59uQCDqPJLVgzUJYiQDxPR?usp=sharing) | |
| Ch5 | [link](https://colab.research.google.com/drive/16S3w4XIEJs-u6ErJMp6Dfrsb-oYrwgnr?usp=sharing) | |
| Ch6 | [link](https://colab.research.google.com/drive/11NRetqfN2xYlq9BAfDRvD5o1S1p4i8Kc?usp=sharing) | |
| Ch7 | | [link](https://colab.research.google.com/drive/14Qxj4-2XJgMjaiTTzx7VBU_gEBWhU4U8?usp=sharing) |
| Ch8 | | [link](https://colab.research.google.com/drive/1Tmn1idnmReD9JQyp1MLM38hqXb7sQAsW?usp=sharing) |
| Ch9 | | [link](https://colab.research.google.com/drive/1tM5n-nGxbiD-kb2SL2OsRaYG2UjnIDPH?usp=sharing) |

## What we learned

**Ch1_2_3:** These chapters showed us that raw data is messy and needs cleaning before a model can use it. We learned to inspect a dataset with head(), info(), and describe(), and to deal with missing values by either deleting them or filling them in. The surprise was that Rank got dropped: it only repeats the order of Global_Sales, so it tells us nothing new.

**Ch4:** Here we learned that we can give a model better inputs by building new features, such as dividing lemonade sold by temperature, or grouping temperatures into labels. We also learned when to use each kind of encoding: one-hot encoding for categories with no natural order, and ordinal encoding for those that have one. What surprised us was how much a simple division could do. Two plain columns became a single feature that makes days far easier to compare.

**Ch5:** This chapter explained that features with larger numbers can overpower smaller ones, and scaling brings them onto a similar level. StandardScaler centers the data around 0, while MinMaxScaler squeezes it into a range between 0 and 1. The surprise was that scaling isn't always necessary, since some models, like decision trees, don't care about the size of the numbers at all.

**Ch6:** We learned that outliers are values sitting far from the rest of the data, and that the Z-score method and the IQR method can both find them. Once found, they can be removed or replaced, depending on whether they're mistakes. What surprised us most was that in our small dataset, the Z-score method missed the value 100 because its score was only about 2.62, while the IQR method caught it.

**Ch7:** This chapter taught us how to select the most important features in a dataset using different methods, such as Filter, RFECV, and LassoCV. We learned that removing unnecessary features can make a model simpler and more efficient.

**Ch8:** We learned how preprocessing pipelines can combine steps like filling in missing values and scaling numerical data into one organized process. We also learned how ColumnTransformer applies different preprocessing steps to specific columns.

**Ch9:** This chapter showed us how to prepare data using techniques such as imputation, encoding, scaling, and discretization. We learned that continuous values, such as Age, can be grouped into categories to make them easier to analyze.

## Errors we found

| Chapter | Error Description | Original Code | Corrected Code | Explanation |
|---|---|---|---|---|
| 6: Outliers | Z-score failed to detect `100`. | `np.abs(z_scores) > 3` | `np.abs(z_scores) > 2` | A threshold of 2 detects `100`, whose Z-score is about 2.62. |
| 7: Feature Selection | `RFECV` produced an undefined R² warning. | `RFECV(estimator, step=1, cv=5)` | `RFECV(estimator, step=1, cv=3)` | Fewer folds may help with small datasets, but the warning may persist. |
| 9: Discretization | Original Age values were overwritten. | `data['Age'] = pd.cut(data['Age'], bins=bins, labels=labels)` | `age_before = data['Age'].copy()` | Preserve the original values before discretization for comparison. |
| 9: Discretization | Wrong column and label used for the pre-discretization plot. | `plt.hist(titanic_preprocessed[:,2], alpha=0.5, label='After discretization')` | `plt.hist(titanic_preprocessed[:,0], alpha=0.5, label='Before discretization')` | Column 0 represents the transformed Age feature before discretization, assuming Age is the first numerical feature. |


## Note on AI tools

We used Claude, an AI tool, while working on this notebook. We used it to explain concepts, check what our code outputs meant, and help draft and simplify our written answers. We ran the code in Colab ourselves and reviewed the answers before putting them in.

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.

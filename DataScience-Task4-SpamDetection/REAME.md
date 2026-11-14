# Email Spam Detection with Machine Learning

**Oasis Infobyte Data Science Internship | Task 4**

## Objective
Build a natural language processing classifier that separates spam messages from legitimate (ham) ones.

## Dataset
SMS Spam Collection from Kaggle: about 5,000 text messages after removing duplicates, labelled as ham (genuine) or spam. Roughly 87% are ham and 13% are spam.

## Steps
1. Loaded the data and checked the class distribution
2. Removed duplicate messages
3. Preprocessed the text: lowercase, removed punctuation and numbers, removed stopwords
4. Converted the text to numbers with a TF-IDF vectoriser
5. Split the data 80/20 (stratified so both sets keep the same share of spam)
6. Trained Multinomial Naive Bayes and Logistic Regression
7. Evaluated both with accuracy, precision, recall, F1-score and confusion matrices

## Results
| Model | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| Multinomial Naive Bayes | 0.967 | 0.990 | 0.748 | 0.852 |
| Logistic Regression | 0.957 | 0.989 | 0.672 | 0.800 |

## Key Insights
- Multinomial Naive Bayes is the best model, ahead of Logistic Regression on accuracy, recall and F1.
- Both models are very precise (about 0.99): on the test set, Naive Bayes wrongly flagged only 1 genuine message out of 903 as spam.
- Recall is the weak spot. Naive Bayes caught 98 of 131 spam messages (33 missed) and Logistic Regression caught 88 (43 missed), so a noticeable share of spam would still reach the inbox.
- The dataset is imbalanced, so accuracy alone looks better than the model really is. Precision, recall and F1 give a fairer picture.

## Limitations
The text cleaning removes numbers and punctuation, which can carry spam signals (for example prices and phone numbers). Keeping them could improve recall.

## How to Run
1. Install the libraries: `pip3 install pandas numpy matplotlib seaborn scikit-learn jupyter`
2. Open `spam_detection.ipynb` in VS Code or Jupyter
3. Click Run All

## Screenshots
See the `screenshots` folder.
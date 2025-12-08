# Main

# Phase 1 Data Acquisition & Understanding

```python
# load all base imports
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
# load data
df = pd.read_csv('Exploratory_Data_Analysis_on_Amazon’s_Diwali_Campaign_Performance_2025.csv')
```

```python
# top 5 rows
df.head()
```

**Output:**
```
    Order_ID        Date Customer_ID Product_Category  Product_Name  Quantity  \
0  ORD100000  25-01-2025    CUST2796   Home & Kitchen  Cookware Set         2   
1  ORD100001  28-08-2025    CUST9669           Beauty    Hair Dryer         1   
2  ORD100002  27-02-2025    CUST5808      Electronics        Tablet         3   
3  ORD100003  24-02-2025    CUST5889      Electronics    Headphones         5   
4  ORD100004  15-06-2025    CUST9005         Clothing         Saree         5   

   Unit_Price_INR  Total_Sales_INR    Payment_Method Delivery_Status  \
0        25574.41         51148.82       Credit Card        Returned   
1        19361.41         19361.41        Debit Card        Returned   
2        38476.22        115428.66  Cash on Delivery       Delivered   
3        38145.72        190728.60       Credit Card       Delivered   
4        45940.98        229704.90               UPI       Delivered   

   Review_Rating         Review_Text      State Country  
0              1      Waste of money     Sikkim   India  
1              5  Excellent product!  Telangana   India  
2              3           Fair deal   Nagaland   India  
3              5   Highly recommend!      Assam   India  
4              5   Highly recommend!     Odisha   India  
```

```python
# last 5 rows
df.tail()
```

**Output:**
```
        Order_ID        Date Customer_ID Product_Category      Product_Name  \
14995  ORD114995  12-04-2025    CUST2822           Beauty          Lipstick   
14996  ORD114996  29-08-2025    CUST6143           Beauty           Shampoo   
14997  ORD114997  27-01-2025    CUST6747            Books  Science Textbook   
14998  ORD114998  21-06-2025    CUST2748           Beauty        Hair Dryer   
14999  ORD114999  07-08-2025    CUST9174   Home & Kitchen     Mixer Grinder   

       Quantity  Unit_Price_INR  Total_Sales_INR    Payment_Method  \
14995         4        36421.54        145686.16               UPI   
14996         4        18158.02         72632.08        Debit Card   
14997         1        38864.05         38864.05               UPI   
14998         3        32658.62         97975.86  Cash on Delivery   
14999         5        45005.57        225027.85  Cash on Delivery   

      Delivery_Status  Review_Rating                 Review_Text  \
14995       Delivered              1          Never buying again   
14996       Delivered              4  Satisfied with the product   
14997       Delivered              1              Waste of money   
14998         Pending              3                Okay product   
14999         Pending              4                Good quality   

                  State Country  
14995           Gujarat   India  
14996         Meghalaya   India  
14997            Sikkim   India  
14998  Himachal Pradesh   India  
14999             Bihar   India  
```

```python
# random 5 rows
df.sample(5)
```

**Output:**
```
       Order_ID        Date Customer_ID Product_Category    Product_Name  \
1514  ORD101514  06-01-2025    CUST1314   Home & Kitchen  Water Purifier   
1703  ORD101703  24-06-2025    CUST7750         Clothing        Sneakers   
4689  ORD104689  14-05-2025    CUST3374      Electronics      Headphones   
7971  ORD107971  15-09-2025    CUST1170         Clothing        Sneakers   
8208  ORD108208  16-10-2025    CUST4368   Home & Kitchen       Air Fryer   

      Quantity  Unit_Price_INR  Total_Sales_INR    Payment_Method  \
1514         1         6706.36          6706.36        Debit Card   
1703         4        49964.18        199856.72               UPI   
4689         3        37380.64        112141.92  Cash on Delivery   
7971         2        26050.70         52101.40       Credit Card   
8208         3        13156.39         39469.17       Credit Card   

     Delivery_Status  Review_Rating         Review_Text         State Country  
1514         Pending              5           Loved it!  Chhattisgarh   India  
1703        Returned              3     Could be better     Jharkhand   India  
4689         Pending              5  Excellent product!         Bihar   India  
7971       Delivered              2       Not satisfied        Odisha   India  
8208       Delivered              1    Very bad product  Chhattisgarh   India  
```

###### metadata

```python
# get rows and columns size: (rows, columns)
# df.shape
print(f"(rows, columns) : {df.shape}")

# '''
# what to analyze:
#
# - how many rows and columns are there?
# - suppose columns are 100 and rows are 50 it hard to analyze this data, it called "curse of dimensionality"
# '''
```

**Output:**
```
(rows, columns) : (15000, 14)

```

```python
# list all column name
print("Columns name:")
print("-"*50)
print(df.columns)

# '''
# what to analyze:
#
# - check label/name of columns is there any whitespace in start of end
# like. " Sales" or any else fix this whitespaces
# '''
```

**Output:**
```
Columns name:
--------------------------------------------------
Index(['Order_ID', 'Date', 'Customer_ID', 'Product_Category', 'Product_Name',
       'Quantity', 'Unit_Price_INR', 'Total_Sales_INR', 'Payment_Method',
       'Delivery_Status', 'Review_Rating', 'Review_Text', 'State', 'Country'],
      dtype='object')

```

```python
# to get a summary of dataframe
print("Summary of dataframe:")
print("-"*50)
df.info

# """
# what to analyze :
#
# range-index: tell total number of entry
# non-null-count: if i have 1000 rows and 800 are non-null than i 200 empty rows
# dtype(data-type):
#     int64 / float64 = Numbers.
#     object = Text/String (or mixed numbers and text).
#     datetime64 = Dates.
# trap: suppose if a column tells if shows age but that column data type is object, then it means there is a typo in a row
# """
```

**Output:**
```
Summary of dataframe:
--------------------------------------------------

```

**Output:**
```
<bound method DataFrame.info of         Order_ID        Date Customer_ID Product_Category      Product_Name  \
0      ORD100000  25-01-2025    CUST2796   Home & Kitchen      Cookware Set   
1      ORD100001  28-08-2025    CUST9669           Beauty        Hair Dryer   
2      ORD100002  27-02-2025    CUST5808      Electronics            Tablet   
3      ORD100003  24-02-2025    CUST5889      Electronics        Headphones   
4      ORD100004  15-06-2025    CUST9005         Clothing             Saree   
...          ...         ...         ...              ...               ...   
14995  ORD114995  12-04-2025    CUST2822           Beauty          Lipstick   
14996  ORD114996  29-08-2025    CUST6143           Beauty           Shampoo   
14997  ORD114997  27-01-2025    CUST6747            Books  Science Textbook   
14998  ORD114998  21-06-2025    CUST2748           Beauty        Hair Dryer   
14999  ORD114999  07-08-2025    CUST9174   Home & Kitchen     Mixer Grinder   

       Quantity  Unit_Price_INR  Total_Sales_INR    Payment_Method  \
0             2        25574.41         51148.82       Credit Card   
1             1        19361.41         19361.41        Debit Card   
2             3        38476.22        115428.66  Cash on Delivery   
3             5        38145.72        190728.60       Credit Card   
4             5        45940.98        229704.90               UPI   
...         ...             ...              ...               ...   
14995         4        36421.54        145686.16               UPI   
14996         4        18158.02         72632.08        Debit Card   
14997         1        38864.05         38864.05               UPI   
14998         3        32658.62         97975.86  Cash on Delivery   
14999         5        45005.57        225027.85  Cash on Delivery   

      Delivery_Status  Review_Rating                 Review_Text  \
0            Returned              1              Waste of money   
1            Returned              5          Excellent product!   
2           Delivered              3                   Fair deal   
3           Delivered              5           Highly recommend!   
4           Delivered              5           Highly recommend!   
...               ...            ...                         ...   
14995       Delivered              1          Never buying again   
14996       Delivered              4  Satisfied with the product   
14997       Delivered              1              Waste of money   
14998         Pending              3                Okay product   
14999         Pending              4                Good quality   

                  State Country  
0                Sikkim   India  
1             Telangana   India  
2              Nagaland   India  
3                 Assam   India  
4                Odisha   India  
...                 ...     ...  
14995           Gujarat   India  
14996         Meghalaya   India  
14997            Sikkim   India  
14998  Himachal Pradesh   India  
14999             Bihar   India  

[15000 rows x 14 columns]>
```

```python
# basic statical summary
df.describe()

#
# what to analyze :
#
# count: total numbers of rows
# mean: average of that column
# min/max: look for impossible values (like age -5, price -2, etc any like)
# 50%(median): if mean is very different from medium than data is skewed
#
```

**Output:**
```
           Quantity  Unit_Price_INR  Total_Sales_INR  Review_Rating
count  15000.000000    15000.000000     15000.000000   15000.000000
mean       2.984667    24955.313715     74544.120233       3.040133
std        1.422826    14401.316925     59369.654155       1.411048
min        1.000000      202.570000       204.050000       1.000000
25%        2.000000    12512.937500     27087.852500       2.000000
50%        3.000000    24878.755000     57293.570000       3.000000
75%        4.000000    37496.170000    112188.600000       4.000000
max        5.000000    49994.430000    249955.500000       5.000000
```

```python
df.describe(include='object')

# '''
# what to analyze:
#
#unique: how many unique categories are there
#top: what is the most frequent category
#freq: how often does the top category appear
# '''
```

**Output:**
```
         Order_ID        Date Customer_ID Product_Category     Product_Name  \
count       15000       15000       15000            15000            15000   
unique      15000         365        7259                5               25   
top     ORD100000  26-05-2025    CUST4795      Electronics  Children's Book   
freq            1          59           8             3036              636   

          Payment_Method Delivery_Status                 Review_Text   State  \
count              15000           15000                       15000   15000   
unique                 4               3                          25      28   
top     Cash on Delivery       Delivered  Satisfied with the product  Sikkim   
freq                3827            5075                         658     596   

       Country  
count    15000  
unique       1  
top      India  
freq     15000  
```

```python
# Phase 2 Data Cleaning & Preprocessing
```

```python
# here datatype of the date column is object instead of int, this is because date represents in different formats it not follows one format
print("Date datatype before conversion: ", df['Date'].dtype)

# convert datatype of date object(str/text) to int

df['Date'] = pd.to_datetime(df['Date'], dayfirst=True)

# let's print datatype now again to check
print("Date datatype after conversion: ", df['Date'].dtype)
```

**Output:**
```
Date datatype before conversion:  object
Date datatype after conversion:  datetime64[ns]

```

```python
# handle missing values
print(df.isnull().sum())
df['Review_Text'] = df['Review_Text'].fillna("No Written Review")
```

**Output:**
```
Order_ID            0
Date                0
Customer_ID         0
Product_Category    0
Product_Name        0
Quantity            0
Unit_Price_INR      0
Total_Sales_INR     0
Payment_Method      0
Delivery_Status     0
Review_Rating       0
Review_Text         0
State               0
Country             0
dtype: int64

```

```python
# checking duplicates and handle them

# first count all duplicates
duplicate_count = df.duplicated().sum()
print(f"Nuber of duplicate rows: {duplicate_count}")

# remove duplicates if exists
if duplicate_count > 0:
    df.drop_duplicates(inplace=True)
    print("Duplicate rows removed!")
```

**Output:**
```
Nuber of duplicate rows: 0

```

```python
# validating categorical data

print("payment methods: ", df['Payment_Method'].unique())
print("product category: ", df['Product_Category'].unique())
print("delivery status: ", df['Delivery_Status'].unique())

text_cols = ["Product_Category", "Payment_Method", "Delivery_Status", "Review_Text"]

for col in text_cols:
    df[col] = df[col].str.strip()
    df[col] = df[col].str.title()
```

**Output:**
```
payment methods:  ['Credit Card' 'Debit Card' 'Cash on Delivery' 'UPI']
product category:  ['Home & Kitchen' 'Beauty' 'Electronics' 'Clothing' 'Books']
delivery status:  ['Returned' 'Delivered' 'Pending']

```

```python
# EDA : Exploratory Data Analysis
```

```python
# specific stats for sales and rating
print("Average Order Value(AOV): ", df['Total_Sales_INR'].mean())
print("Minimum Order Value: ", df['Total_Sales_INR'].min())
print("Maximum Order Value: ", df['Total_Sales_INR'].max())

print("\nAverage Rating: ", df['Review_Rating'].mean())
```

**Output:**
```
Average Order Value(AOV):  74544.12023333333
Minimum Order Value:  204.05
Maximum Order Value:  249955.5

Average Rating:  3.0401333333333334

```

```python
# grouping and aggregation
# which product category generates most revenue

# group by category and sum the sales
category_sales = df.groupby("Product_Category")['Total_Sales_INR'].sum().sort_values(ascending=False)

print(category_sales)

# which state gets the most orders
state_orders = df.groupby('State')['Order_ID'].count().sort_values(ascending=False).head()

print(state_orders)
```

**Output:**
```
Product_Category
Beauty            2.274896e+08
Electronics       2.265649e+08
Books             2.249992e+08
Clothing          2.224093e+08
Home & Kitchen    2.166987e+08
Name: Total_Sales_INR, dtype: float64
State
Sikkim          596
Rajasthan       568
Tamil Nadu      567
Meghalaya       559
Chhattisgarh    556
Name: Order_ID, dtype: int64

```

```python
# Time-based analysis (feature engineering)
df['Month'] = df['Date'].dt.month_name()

monthly_sales = df.groupby('Month')['Total_Sales_INR'].sum()

order = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']

monthly_sales = monthly_sales.reindex(order)

print(monthly_sales)
```

**Output:**
```
Month
January      92051785.03
February     84995760.62
March        93064349.39
April        91388990.14
May          97195848.48
June         89730685.72
July         95176904.42
August       97576563.09
September    91225555.74
October      93478344.05
November     94809186.29
December     97467830.53
Name: Total_Sales_INR, dtype: float64

```

```python
# Data Visualization
```

```python
sns.set_style("whitegrid")
plt.figure(figsize=(10, 6))
```

**Output:**
```
<Figure size 1000x600 with 0 Axes>
```

**Output:**
```
<Figure size 1000x600 with 0 Axes>
```

```python
# vertical charts

cat_sales = df.groupby('Product_Category')['Total_Sales_INR'].sum().reset_index()

cat_sales['Sales_Crore'] = cat_sales['Total_Sales_INR']/10000000

plt.figure(figsize=(10, 5))
ax = sns.barplot(data=cat_sales, x='Product_Category', y='Sales_Crore', hue='Product_Category', legend=False, palette='viridis')

plt.title("Total Sales bby Product Category", fontsize=16)
plt.ylabel("Sales in Crore", fontsize=12)
plt.xlabel("Product Category", fontsize=12)

for i in ax.containers:
    ax.bar_label(i, fmt='%.2f', padding=3)

plt.show()
```

**Output:**
```
<Figure size 1000x500 with 1 Axes>
```

```python
# horizontal bar charts

top_states = df['State'].value_counts().head(10).reset_index()

top_states.columns = ['State', 'Order_Count']

plt.figure(figsize=(10, 6))

sns.barplot(data=top_states, x='Order_Count', y='State', hue="State",legend=False , orient='h', palette='magma')

plt.title("Top 10 States with Most Orders", fontsize=16)
plt.xlabel("Order Count", fontsize=12)
plt.ylabel("State", fontsize=12)

plt.show()
```

**Output:**
```
<Figure size 1000x600 with 1 Axes>
```

```python
# line charts

month_order = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']

monthly_sales = df.groupby('Month')['Total_Sales_INR'].sum().reindex(month_order).reset_index()
plt.figure(figsize=(12, 6))
sns.lineplot(data=monthly_sales, x='Month', y='Total_Sales_INR', marker='o', color='b', linewidth=2.5)

plt.title("Monthly Sales Trend (2025)", fontsize=16)
plt.xlabel("Month", fontsize=12)
plt.ylabel("Total Sales", fontsize=12)

plt.xticks(rotation=45)
plt.grid(True)

plt.show()
```

**Output:**
```
<Figure size 1200x600 with 1 Axes>
```

```python
# Advanced Insight (Correlation & Relationships)
```

```python
# """
# correlation matrix
#
# correlations measure the relationships between two numbers on a scale of -1 to 1
#
# 1: strong positive correlation
# 0: no correlation
# -1: strong negative correlation
# """

numerical_cols = df[['Unit_Price_INR', 'Total_Sales_INR', 'Quantity', 'Review_Rating']]

corr_matrix = numerical_cols.corr()

plt.figure(figsize=(8, 6))
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Heatmap', fontsize=16)
plt.show()

# """
# what look here:
#
# look at the box Unit_Price_INR meets Review_Rating. if the number is close to 0, it means price has no effect on customer happiness. if it positive, expensive items are more likely to be rated highly.
# """
```

**Output:**
```
<Figure size 800x600 with 2 Axes>
```

```python
# Scatter plot (Price vs Rating)
# heatmap gives us number but scatterplot let us see the pattern

plt.figure(figsize=(10, 6))

sns.scatterplot(data=df, x="Unit_Price_INR", y="Review_Rating", alpha=0.3, color="purple")

plt.title("Does price affect rating?", fontsize=16)
plt.xlabel("Unit Price (INR)", fontsize=12)
plt.ylabel("Review Rating(1-5)", fontsize=12)

plt.show()
```

**Output:**
```
<Figure size 1000x600 with 1 Axes>
```

```python
df.to_csv('Cleaned_Sales_Data.csv', index=False)
print("File saved successfully!")
```

**Output:**
```
File saved successfully!

```

# MACHINE LEARNING


Preprocessing (Encoding)

machine learning models cannot understand text like beauty, credit card, etc. we first convert this data into number which called data preprocessing in ml

here,
input(X): Product_Category, Unit_Price_INR, Quantity, Payment_Method
target(y): Review_Rating


```python
# basic imports
from sklearn.model_selection import train_test_split
# cause this is a classification problem
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report
```

```python
# 1. select the feature we want to use
X = df[['Product_Category', 'Unit_Price_INR', 'Quantity', 'Payment_Method', 'Total_Sales_INR']]
```

```python
# select the target (the label we wanna predict)
y = df['Review_Rating']
```

```python
# now i gonna convert text into numbers (One-Hot Encoding)
X = pd.get_dummies(X, drop_first=True)
# this turns 'Category' into 'Category_Beauty', 'Category_Electronics' (True/False or 0/1)
```

```python
# Let's look at the new data format
print(f"Feature shape: {X.shape}")
X.head()
```

**Output:**
```
Feature shape: (15000, 10)

```

**Output:**
```
   Unit_Price_INR  Quantity  Total_Sales_INR  Product_Category_Books  \
0        25574.41         2         51148.82                   False   
1        19361.41         1         19361.41                   False   
2        38476.22         3        115428.66                   False   
3        38145.72         5        190728.60                   False   
4        45940.98         5        229704.90                   False   

   Product_Category_Clothing  Product_Category_Electronics  \
0                      False                         False   
1                      False                         False   
2                      False                          True   
3                      False                          True   
4                       True                         False   

   Product_Category_Home & Kitchen  Payment_Method_Credit Card  \
0                             True                        True   
1                            False                       False   
2                            False                       False   
3                            False                        True   
4                            False                       False   

   Payment_Method_Debit Card  Payment_Method_Upi  
0                      False               False  
1                       True               False  
2                      False               False  
3                      False               False  
4                      False                True  
```

## Splitting the data

now let's split our data into training and testing set
training set(80%): used to train our model
testing set(20%): used to test our model


```python
# random state=42 ensures we get the same split everytime (42 is a standard convention)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

print(f"Training Data : {X_train.shape}")
print(f"Testing Data : {X_test.shape}")
```

**Output:**
```
Training Data : (12000, 10)
Testing Data : (3000, 10)

```

## Training the model
for a train model I will use here radom forest classifier

```python
# let's initialize the model first
model = RandomForestClassifier(n_estimators=100, random_state=42)
# n_estimators=100 it means we use 100 trees in our forest
```

```python
# now we gonna train our model,machine learning will happen here
print("Training the model... this might take a few seconds.")
model.fit(X_train, y_train)

print("Training complete")
```

**Output:**
```
Training the model... this might take a few seconds.
Training complete

```

## Making Predictions & Evaluation

```python
# Let's first make a prediction on the test data
y_pred = model.predict(X_test)

# now let calculate the accuracy (how did it get exactly right)
accuracy = accuracy_score(y_test, y_pred)
print(f"Model Accuracy: {accuracy * 100:.2f}%")

# Detailed Report
print("\nClassification Report:")
print(classification_report(y_test, y_pred))
```

**Output:**
```
Model Accuracy: 20.10%

Classification Report:
              precision    recall  f1-score   support

           1       0.23      0.24      0.23       578
           2       0.19      0.18      0.18       624
           3       0.19      0.19      0.19       584
           4       0.20      0.20      0.20       602
           5       0.20      0.19      0.19       612

    accuracy                           0.20      3000
   macro avg       0.20      0.20      0.20      3000
weighted avg       0.20      0.20      0.20      3000


```

```python
# Let's visualize feature importance
feature_imp = pd.Series(model.feature_importances_, index=X.columns).sort_values(ascending=False).head(10)
plt.figure(figsize=(8, 6))
sns.barplot(x=feature_imp, y=feature_imp.index,hue=feature_imp.index, legend=False, palette='viridis')
plt.title("What drives the Customer Rating?")
plt.xlabel("Importance Score")
plt.show()
```

**Output:**
```
<Figure size 800x600 with 1 Axes>
```

* we can say here ml model is failed because we only get ~20% accuracy because data is very random and model did not find any patterns there (we can also see that in scatter plot we cannot see any patterns there)
* so predicting rating failed now i gonna try to predict sales
* before we predicted a category(Classification) where we failed
* now we gonna predict number(Regression) of sales
* total_sales = price * quantity

```python
# let first import required modules
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score
```

```python
# now our new target is Total_Sales_INR
X = df[['Unit_Price_INR', 'Quantity', 'Product_Category']]
y = df['Total_Sales_INR']
```

```python
# let's convert text into numbers again
X = pd.get_dummies(X, drop_first=True)
```

```python
# let's split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

```python
# now let's train the model (now we use regression, not classification)
model_reg = RandomForestRegressor(n_estimators=100, random_state=42)
model_reg.fit(X_train, y_train)
print("model trained.")
```

**Output:**
```
model trained.

```

```python
# let's make predictions now
y_pred = model_reg.predict(X_test)
```

```python
# let's check accuracy (R2 score)

score = r2_score(y_test, y_pred)
print(f"Model Accuracy(R2 Score): {score:.4f}")
# """
# r2 scores 1.0 means perfect prediction,
# 0.0 means the model gives random guessing
# """
```

**Output:**
```
Model Accuracy(R2 Score): 1.0000

```

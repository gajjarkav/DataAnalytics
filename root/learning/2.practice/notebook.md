# Main

```python
# here I am using zomato dataset from kaggle you can download it from: https://www.kaggle.com/datasets/himanshupoddar/zomato-bangalore-restaurants
```

```python
# let's import base libraries first
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
# load data
df = pd.read_csv('zomato.csv', encoding='latin-1')
```

let check first last and random rows

```python
print("first 3 rows of data: ")
df.head(3)
```

**Output:**
```
first 3 rows of data: 

```

**Output:**
```
                                                 url  \
0  https://www.zomato.com/bangalore/jalsa-banasha...   
1  https://www.zomato.com/bangalore/spice-elephan...   
2  https://www.zomato.com/SanchurroBangalore?cont...   

                                             address             name  \
0  942, 21st Main Road, 2nd Stage, Banashankari, ...            Jalsa   
1  2nd Floor, 80 Feet Road, Near Big Bazaar, 6th ...   Spice Elephant   
2  1112, Next to KIMS Medical College, 17th Cross...  San Churro Cafe   

  online_order book_table   rate  votes                           phone  \
0          Yes        Yes  4.1/5    775  080 42297555\r\n+91 9743772233   
1          Yes         No  4.1/5    787                    080 41714161   
2          Yes         No  3.8/5    918                  +91 9663487993   

       location            rest_type  \
0  Banashankari        Casual Dining   
1  Banashankari        Casual Dining   
2  Banashankari  Cafe, Casual Dining   

                                          dish_liked  \
0  Pasta, Lunch Buffet, Masala Papad, Paneer Laja...   
1  Momos, Lunch Buffet, Chocolate Nirvana, Thai G...   
2  Churros, Cannelloni, Minestrone Soup, Hot Choc...   

                         cuisines approx_cost(for two people)  \
0  North Indian, Mughlai, Chinese                         800   
1     Chinese, North Indian, Thai                         800   
2          Cafe, Mexican, Italian                         800   

                                        reviews_list menu_item  \
0  [('Rated 4.0', 'RATED\n  A beautiful place to ...        []   
1  [('Rated 4.0', 'RATED\n  Had been here for din...        []   
2  [('Rated 3.0', "RATED\n  Ambience is not that ...        []   

  listed_in(type) listed_in(city)  
0          Buffet    Banashankari  
1          Buffet    Banashankari  
2          Buffet    Banashankari  
```

```python
print("last 3 rows of data: ")
df.tail(3)
```

**Output:**
```
last 3 rows of data: 

```

**Output:**
```
                                                     url  \
51714  https://www.zomato.com/bangalore/plunge-sherat...   
51715  https://www.zomato.com/bangalore/chime-sherato...   
51716  https://www.zomato.com/bangalore/the-nest-the-...   

                                                 address  \
51714  Sheraton Grand Bengaluru Whitefield Hotel & Co...   
51715  Sheraton Grand Bengaluru Whitefield Hotel & Co...   
51716  ITPL Main Road, KIADB Export Promotion Industr...   

                                                    name online_order  \
51714  Plunge - Sheraton Grand Bengaluru Whitefield H...           No   
51715  Chime - Sheraton Grand Bengaluru Whitefield Ho...           No   
51716                       The Nest - The Den Bengaluru           No   

      book_table    rate  votes           phone                    location  \
51714         No     NaN      0             NaN                  Whitefield   
51715        Yes  4.3 /5    236    080 49652769  ITPL Main Road, Whitefield   
51716         No  3.4 /5     13  +91 8071117272  ITPL Main Road, Whitefield   

                rest_type                    dish_liked  \
51714                 Bar                           NaN   
51715                 Bar  Cocktails, Pizza, Buttermilk   
51716  Bar, Casual Dining                           NaN   

                                     cuisines approx_cost(for two people)  \
51714                             Finger Food                       2,000   
51715                             Finger Food                       2,500   
51716  Finger Food, North Indian, Continental                       1,500   

                                            reviews_list menu_item  \
51714                                                 []        []   
51715  [('Rated 4.0', 'RATED\n  Nice and friendly pla...        []   
51716  [('Rated 5.0', 'RATED\n  Great ambience , look...        []   

      listed_in(type) listed_in(city)  
51714   Pubs and bars      Whitefield  
51715   Pubs and bars      Whitefield  
51716   Pubs and bars      Whitefield  
```

```python
print("random 3 rows of data: ")
df.sample(3)
```

**Output:**
```
random 3 rows of data: 

```

**Output:**
```
                                                     url  \
6498   https://www.zomato.com/bangalore/bhaiya-ji-foo...   
34158  https://www.zomato.com/bangalore/skywalk-resto...   
16039  https://www.zomato.com/bangalore/vegan-heat-ko...   

                                                 address  \
6498   Next To Ulsoor Metro Station, Vivekananda Road...   
34158  169, 80 Feet Road, Koramangala 1st Block, Bang...   
16039  178/10, 3rd B Cross, Venkatapura Main Road, Ko...   

                       name online_order book_table    rate  votes  \
6498   Bhaiya Ji Food Court           No         No   3.0/5     16   
34158      Skywalk Restobar           No         No  3.3 /5      5   
16039            Vegan Heat          Yes         No   4.1/5    314   

                                  phone               location  \
6498   +91 7406275093\r\n+91 8904934581                 Ulsoor   
34158    +91 8095095550\n+91 9500122544  Koramangala 1st Block   
16039                      080 48513973  Koramangala 1st Block   

                rest_type                         dish_liked  \
6498          Quick Bites                                NaN   
34158  Casual Dining, Bar                                NaN   
16039  Takeaway, Delivery  Burgers, Pancakes, Waffles, Salad   

                         cuisines approx_cost(for two people)  \
6498    North Indian, Street Food                         150   
34158  North Indian, South Indian                         700   
16039         Healthy Food, Salad                         650   

                                            reviews_list menu_item  \
6498   [('Rated 5.0', "RATED\n  Nice good food and se...        []   
34158  [('Rated 5.0', 'RATED\n  Polite and friendly s...        []   
16039  [('Rated 4.0', 'RATED\n  Hi, Had ordered yum y...        []   

      listed_in(type)        listed_in(city)  
6498         Dine-out           Brigade Road  
34158        Dine-out  Koramangala 6th Block  
16039        Delivery                    HSR  
```

```python
df.info()
```

**Output:**
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 51717 entries, 0 to 51716
Data columns (total 17 columns):
 #   Column                       Non-Null Count  Dtype 
---  ------                       --------------  ----- 
 0   url                          51717 non-null  object
 1   address                      51717 non-null  object
 2   name                         51717 non-null  object
 3   online_order                 51717 non-null  object
 4   book_table                   51717 non-null  object
 5   rate                         43942 non-null  object
 6   votes                        51717 non-null  int64 
 7   phone                        50509 non-null  object
 8   location                     51696 non-null  object
 9   rest_type                    51490 non-null  object
 10  dish_liked                   23639 non-null  object
 11  cuisines                     51672 non-null  object
 12  approx_cost(for two people)  51371 non-null  object
 13  reviews_list                 51717 non-null  object
 14  menu_item                    51717 non-null  object
 15  listed_in(type)              51717 non-null  object
 16  listed_in(city)              51717 non-null  object
dtypes: int64(1), object(16)
memory usage: 6.7+ MB

```

```python
df.describe()
```

**Output:**
```
              votes
count  51717.000000
mean     283.697527
std      803.838853
min        0.000000
25%        7.000000
50%       41.000000
75%      198.000000
max    16832.000000
```

```python
df.columns
```

**Output:**
```
Index(['url', 'address', 'name', 'online_order', 'book_table', 'rate', 'votes',
       'phone', 'location', 'rest_type', 'dish_liked', 'cuisines',
       'approx_cost(for two people)', 'reviews_list', 'menu_item',
       'listed_in(type)', 'listed_in(city)'],
      dtype='object')
```

first we gonna drop unnecessary columns which we do not use it on analysis

```python
df.drop(['url', 'address', 'phone', 'menu_item', 'reviews_list'], axis=1, inplace=True)
```

now let rename few long title names

```python
df.rename(columns={"approx_cost(for two people)": "cost", "listed_in(type)": "type", "listed_in(city)": "city"}, inplace=True)
df.head()
```

**Output:**
```
                    name online_order book_table   rate  votes      location  \
0                  Jalsa          Yes        Yes  4.1/5    775  Banashankari   
1         Spice Elephant          Yes         No  4.1/5    787  Banashankari   
2        San Churro Cafe          Yes         No  3.8/5    918  Banashankari   
3  Addhuri Udupi Bhojana           No         No  3.7/5     88  Banashankari   
4          Grand Village           No         No  3.8/5    166  Basavanagudi   

             rest_type                                         dish_liked  \
0        Casual Dining  Pasta, Lunch Buffet, Masala Papad, Paneer Laja...   
1        Casual Dining  Momos, Lunch Buffet, Chocolate Nirvana, Thai G...   
2  Cafe, Casual Dining  Churros, Cannelloni, Minestrone Soup, Hot Choc...   
3          Quick Bites                                        Masala Dosa   
4        Casual Dining                                Panipuri, Gol Gappe   

                         cuisines cost    type          city  
0  North Indian, Mughlai, Chinese  800  Buffet  Banashankari  
1     Chinese, North Indian, Thai  800  Buffet  Banashankari  
2          Cafe, Mexican, Italian  800  Buffet  Banashankari  
3      South Indian, North Indian  300  Buffet  Banashankari  
4        North Indian, Rajasthani  600  Buffet  Banashankari  
```

here rate column is an object datatype we fix it to convert into float

```python
def clean_rate(value: str) -> float:
    if pd.isna(value):
        return np.nan
    if value == "NEW" or value == "-":
        return np.nan
    value = str(value).replace('/', '')[0]
    return float(value)

df['rate'] = df['rate'].apply(clean_rate)

df['rate'].fillna(df['rate'].mean())

print(df['rate'].dtype)
df['rate'].head()
```

**Output:**
```
float64

```

**Output:**
```
0    4.0
1    4.0
2    3.0
3    3.0
4    3.0
Name: rate, dtype: float64
```

checking unique value to check mess in data

```python
df['cost'].unique()
```

**Output:**
```
array(['800', '300', '600', '700', '550', '500', '450', '650', '400',
       '900', '200', '750', '150', '850', '100', '1,200', '350', '250',
       '950', '1,000', '1,500', '1,300', '199', '80', '1,100', '160',
       '1,600', '230', '130', '50', '190', '1,700', nan, '1,400', '180',
       '1,350', '2,200', '2,000', '1,800', '1,900', '330', '2,500',
       '2,100', '3,000', '2,800', '3,400', '40', '1,250', '3,500',
       '4,000', '2,400', '2,600', '120', '1,450', '469', '70', '3,200',
       '60', '560', '240', '360', '6,000', '1,050', '2,300', '4,100',
       '5,000', '3,700', '1,650', '2,700', '4,500', '140'], dtype=object)
```

```python
def clean_cost(value: str) -> float:
    if pd.isna(value):
        return np.nan
    if isinstance(value, str):
        value = value.replace(",", "")
    return float(value)

df['cost'] = df['cost'].apply(clean_cost)

df.dropna(subset=['cost'], inplace=True)

print(df['cost'].dtype)
```

**Output:**
```
float64

```

since we have many missing data, if we drop it, we will lose much of data, so we verify that data and also drop duplicates

```python
df['dish_liked'].fillna("Unknown")
df.drop_duplicates(inplace=True)
```

```python
df.info()
```

**Output:**
```
<class 'pandas.core.frame.DataFrame'>
Index: 51265 entries, 0 to 51716
Data columns (total 12 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   name          51265 non-null  object 
 1   online_order  51265 non-null  object 
 2   book_table    51265 non-null  object 
 3   rate          41345 non-null  float64
 4   votes         51265 non-null  int64  
 5   location      51265 non-null  object 
 6   rest_type     51061 non-null  object 
 7   dish_liked    23461 non-null  object 
 8   cuisines      51246 non-null  object 
 9   cost          51265 non-null  float64
 10  type          51265 non-null  object 
 11  city          51265 non-null  object 
dtypes: float64(2), int64(1), object(9)
memory usage: 5.1+ MB

```

## EDA : Exploratory Data Analysis
now we gonna move one more step upward we gonna perform eda here

```python
numerical_cols = df[['rate', 'cost', 'votes']]

corr = numerical_cols.corr()

plt.figure(figsize=(8, 6))
sns.heatmap(corr, annot=True, cmap="coolwarm", fmt=".2f")
plt.title('Correlation: cost vs rate vs votes')
plt.show()
```

**Output:**
```
<Figure size 800x600 with 2 Axes>
```

```python
# boxplots
plt.figure(figsize=(14, 6))

# plot1 online order vs rate
plt.subplot(1, 2, 1)
sns.boxplot(x='online_order', y='rate', hue='online_order', legend=True, data=df, palette='Set2')
plt.title("Does online order affect rating?")

# plot2 book-table vs rate
plt.subplot(1, 2, 2)
sns.boxplot(x='book_table', y='rate', hue='book_table', legend=True, data=df, palette='Set2')
plt.title("Does table booking affect rating?")
```

**Output:**
```
Text(0.5, 1.0, 'Does table booking affect rating?')
```

**Output:**
```
<Figure size 1400x600 with 2 Axes>
```

```python
# let's find the foodie hubs

plt.figure(figsize=(12, 6))
top_locations = df['location'].value_counts().head(10)
sns.barplot(x=top_locations.index, y=top_locations.values, palette='viridis', hue=top_locations.index, legend=True)
plt.title("Top 10 locations of most restaurants in Bangalore")
plt.xticks(rotation=45)
plt.show()
```

**Output:**
```
<Figure size 1200x600 with 1 Axes>
```

```python
df_clean = df[df['cuisines'].notnull()]
# let use a lambda function to split cuisine column into a list
all_cuisines = df_clean['cuisines'].apply(lambda x: x.split(','))

from collections import Counter
cuisine_list = []
for row in all_cuisines:
    for item in row:
        cuisine_list.append(item.strip())

cuisine_counts = Counter(cuisine_list)

top_cuisines = pd.DataFrame.from_dict(cuisine_counts, orient="index").reset_index()
top_cuisines.columns = ['Cuisines', 'Count']

top_cuisines = top_cuisines.sort_values('Count', ascending=False).head(10)

print(top_cuisines)
```

**Output:**
```
        Cuisines  Count
0   North Indian  20922
2        Chinese  15421
7   South Indian   8579
14     Fast Food   8058
21       Biryani   6459
11   Continental   5700
20      Desserts   5586
4           Cafe   5245
13     Beverages   4692
6        Italian   3353

```

```python
plt.figure(figsize=(12, 6))
sns.barplot(data=top_cuisines, x='Cuisines', y='Count', hue='Cuisines', legend=False, palette='magma')
plt.title("Top 10 Most Popular Cuisines in Bangalore", fontsize=16)
plt.xlabel("Numbers of Restaurants")
plt.show()
```

**Output:**
```
<Figure size 1200x600 with 1 Axes>
```

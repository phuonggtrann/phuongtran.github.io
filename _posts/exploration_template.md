## GoBike System Data

*By: Phuong Tran*
*06/16/2020*

### Introduction
**Investigation Overview**

> The goal of this project is to dig into the bike data to understand about different factors that is affecting bike trip durations

**Dataset Overview**

> The dataset is from Bay Wheel's trip data and it is available for public use. It contains trip informations and bikers' subscribe status. This data set is taken from Lyft's website for year of 2017


```python
## Import all
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

%matplotlib inline
```

### What is the structure of your dataset?

> There are 13 variables (columns) and 519700 observations (rows) in this data set. There is 2 user type: subsciber and customer.

### What is/are the main feature(s) of interest in your dataset?

> Infomation about start and end station such as station id, station name, station longtitude and latitude. There are also bike information (bike ID) as well as bikers's trip information such as trip duration in seconds and user type.

### What features in the dataset do you think will help support your investigation into your feature(s) of interest?

> In my opinion, trip durations, start time and user type are factors that impact trip duration the most. 


```python
## Load data set in and inspect data
df = pd.read_csv('tripdata.csv')

df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>duration_sec</th>
      <th>start_time</th>
      <th>end_time</th>
      <th>start_station_id</th>
      <th>start_station_name</th>
      <th>start_station_latitude</th>
      <th>start_station_longitude</th>
      <th>end_station_id</th>
      <th>end_station_name</th>
      <th>end_station_latitude</th>
      <th>end_station_longitude</th>
      <th>bike_id</th>
      <th>user_type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80110</td>
      <td>2017-12-31 16:57:39.6540</td>
      <td>2018-01-01 15:12:50.2450</td>
      <td>74</td>
      <td>Laguna St at Hayes St</td>
      <td>37.776435</td>
      <td>-122.426244</td>
      <td>43</td>
      <td>San Francisco Public Library (Grove St at Hyde...</td>
      <td>37.778768</td>
      <td>-122.415929</td>
      <td>96</td>
      <td>Customer</td>
    </tr>
    <tr>
      <th>1</th>
      <td>78800</td>
      <td>2017-12-31 15:56:34.8420</td>
      <td>2018-01-01 13:49:55.6170</td>
      <td>284</td>
      <td>Yerba Buena Center for the Arts (Howard St at ...</td>
      <td>37.784872</td>
      <td>-122.400876</td>
      <td>96</td>
      <td>Dolores St at 15th St</td>
      <td>37.766210</td>
      <td>-122.426614</td>
      <td>88</td>
      <td>Customer</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45768</td>
      <td>2017-12-31 22:45:48.4110</td>
      <td>2018-01-01 11:28:36.8830</td>
      <td>245</td>
      <td>Downtown Berkeley BART</td>
      <td>37.870348</td>
      <td>-122.267764</td>
      <td>245</td>
      <td>Downtown Berkeley BART</td>
      <td>37.870348</td>
      <td>-122.267764</td>
      <td>1094</td>
      <td>Customer</td>
    </tr>
    <tr>
      <th>3</th>
      <td>62172</td>
      <td>2017-12-31 17:31:10.6360</td>
      <td>2018-01-01 10:47:23.5310</td>
      <td>60</td>
      <td>8th St at Ringold St</td>
      <td>37.774520</td>
      <td>-122.409449</td>
      <td>5</td>
      <td>Powell St BART Station (Market St at 5th St)</td>
      <td>37.783899</td>
      <td>-122.408445</td>
      <td>2831</td>
      <td>Customer</td>
    </tr>
    <tr>
      <th>4</th>
      <td>43603</td>
      <td>2017-12-31 14:23:14.0010</td>
      <td>2018-01-01 02:29:57.5710</td>
      <td>239</td>
      <td>Bancroft Way at Telegraph Ave</td>
      <td>37.868813</td>
      <td>-122.258764</td>
      <td>247</td>
      <td>Fulton St at Bancroft Way</td>
      <td>37.867789</td>
      <td>-122.265896</td>
      <td>3167</td>
      <td>Subscriber</td>
    </tr>
  </tbody>
</table>
</div>



### Data Wrangling

#### Assess:
1. Convert duration second to minute and rename the column to duration_min
2. Convert start time and end time into panda date and time format for easier acess to day or month specifically.
3. There is no duplicated
4. No weird value (duration less than 0 wouldn't make any sense)


```python
df.shape
```




    (519700, 13)




```python
df.isnull().sum()
## There is no Nans
```




    duration_sec               0
    start_time                 0
    end_time                   0
    start_station_id           0
    start_station_name         0
    start_station_latitude     0
    start_station_longitude    0
    end_station_id             0
    end_station_name           0
    end_station_latitude       0
    end_station_longitude      0
    bike_id                    0
    user_type                  0
    dtype: int64




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 519700 entries, 0 to 519699
    Data columns (total 13 columns):
     #   Column                   Non-Null Count   Dtype  
    ---  ------                   --------------   -----  
     0   duration_sec             519700 non-null  int64  
     1   start_time               519700 non-null  object 
     2   end_time                 519700 non-null  object 
     3   start_station_id         519700 non-null  int64  
     4   start_station_name       519700 non-null  object 
     5   start_station_latitude   519700 non-null  float64
     6   start_station_longitude  519700 non-null  float64
     7   end_station_id           519700 non-null  int64  
     8   end_station_name         519700 non-null  object 
     9   end_station_latitude     519700 non-null  float64
     10  end_station_longitude    519700 non-null  float64
     11  bike_id                  519700 non-null  int64  
     12  user_type                519700 non-null  object 
    dtypes: float64(4), int64(4), object(5)
    memory usage: 51.5+ MB
    


```python
## Nothing less than or equal to 0 so it's good
df[df['duration_sec']<=0]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>duration_sec</th>
      <th>start_time</th>
      <th>end_time</th>
      <th>start_station_id</th>
      <th>start_station_name</th>
      <th>start_station_latitude</th>
      <th>start_station_longitude</th>
      <th>end_station_id</th>
      <th>end_station_name</th>
      <th>end_station_latitude</th>
      <th>end_station_longitude</th>
      <th>bike_id</th>
      <th>user_type</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
## Making sure there are only 2 values in user type
df['user_type'].value_counts()
```




    Subscriber    409230
    Customer      110470
    Name: user_type, dtype: int64




```python
df.duplicated().sum()
```




    0




```python
# Convert start time and end time into panda datetime format
df['start_time'] = pd.to_datetime(df['start_time'], infer_datetime_format=True)
df['end_time'] = pd.to_datetime(df['end_time'], infer_datetime_format=True)
```


```python
## Adding more start columns
df['start_hour'] = df['start_time'].dt.hour
df['start_month'] = df['start_time'].dt.month
df['start_day'] = df['start_time'].dt.weekday

def to_stringday(day):
    if day==0:
        return 'Mon'
    elif day==1:
        return 'Tues'
    elif day==2:
        return 'Wed'
    elif day==3:
        return 'Thur'
    elif day==4:
        return 'Fri'
    elif day==5:
        return 'Sat'
    else:
        return 'Sun'
    
df['start_day'] = df['start_day'].apply(to_stringday)
```


```python
## No longer need start and end time
df.drop(axis=1, columns=['start_time', 'end_time'], inplace=True)
```


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>duration_sec</th>
      <th>start_station_id</th>
      <th>start_station_name</th>
      <th>start_station_latitude</th>
      <th>start_station_longitude</th>
      <th>end_station_id</th>
      <th>end_station_name</th>
      <th>end_station_latitude</th>
      <th>end_station_longitude</th>
      <th>bike_id</th>
      <th>user_type</th>
      <th>start_hour</th>
      <th>start_month</th>
      <th>start_day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>80110</td>
      <td>74</td>
      <td>Laguna St at Hayes St</td>
      <td>37.776435</td>
      <td>-122.426244</td>
      <td>43</td>
      <td>San Francisco Public Library (Grove St at Hyde...</td>
      <td>37.778768</td>
      <td>-122.415929</td>
      <td>96</td>
      <td>Customer</td>
      <td>16</td>
      <td>12</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>1</th>
      <td>78800</td>
      <td>284</td>
      <td>Yerba Buena Center for the Arts (Howard St at ...</td>
      <td>37.784872</td>
      <td>-122.400876</td>
      <td>96</td>
      <td>Dolores St at 15th St</td>
      <td>37.766210</td>
      <td>-122.426614</td>
      <td>88</td>
      <td>Customer</td>
      <td>15</td>
      <td>12</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>2</th>
      <td>45768</td>
      <td>245</td>
      <td>Downtown Berkeley BART</td>
      <td>37.870348</td>
      <td>-122.267764</td>
      <td>245</td>
      <td>Downtown Berkeley BART</td>
      <td>37.870348</td>
      <td>-122.267764</td>
      <td>1094</td>
      <td>Customer</td>
      <td>22</td>
      <td>12</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>3</th>
      <td>62172</td>
      <td>60</td>
      <td>8th St at Ringold St</td>
      <td>37.774520</td>
      <td>-122.409449</td>
      <td>5</td>
      <td>Powell St BART Station (Market St at 5th St)</td>
      <td>37.783899</td>
      <td>-122.408445</td>
      <td>2831</td>
      <td>Customer</td>
      <td>17</td>
      <td>12</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>4</th>
      <td>43603</td>
      <td>239</td>
      <td>Bancroft Way at Telegraph Ave</td>
      <td>37.868813</td>
      <td>-122.258764</td>
      <td>247</td>
      <td>Fulton St at Bancroft Way</td>
      <td>37.867789</td>
      <td>-122.265896</td>
      <td>3167</td>
      <td>Subscriber</td>
      <td>14</td>
      <td>12</td>
      <td>Sun</td>
    </tr>
  </tbody>
</table>
</div>



### Unvariate

#### 1. Duration
> Bikers tend to make trip duration around 700 seconcs (~12 minutes)


```python
# 1. duration.
bins = 5 ** np.arange(2, 5.0 + 0.1, 0.1) 
plt.hist(df['duration_sec'], bins=bins, color='pink')
plt.xlim(0,3200) 
plt.xlabel('Duration (Second)')
plt.title('Trip duration histogram',  fontweight='bold', fontsize=16)
plt.ylabel('Duration Range Frequency')
plt.show();
```


![png](output_17_0.png)


#### Month

> June has the least bike rentals and October has the most. However, as it get cooleror hotter, people doesn't want to ride a bike, especially in June (start of summer)


```python
# 2. month
# https://seaborn.pydata.org/generated/seaborn.countplot.html
sns.countplot(df['start_month'])
plt.title("Number of trip for each month of year 2017",  fontweight='bold', fontsize=16)
plt.ylabel('Number of bike trips')
plt.xlabel('Month')
plt.show()
```


![png](output_19_0.png)


#### Day of the week

> It's not expected that there are more trip during weekdays other than weekend. Maybe in the observation area, people ride their bike to work more?


```python
# 3. weekday
sns.countplot(df['start_day'])
plt.title("Number of trip for each day of week of year 2017", fontweight='bold', fontsize=16)
plt.ylabel('Number of bike trips')
plt.xlabel('Day')
plt.show()
```


![png](output_21_0.png)


#### Hour distribution

> There is no outlier in the graph therefore nothing extreme is in the graph. If there is then we have to trim it off. Most hour is around 2 pm and who has bike trip at the midnight?


```python
## 4. Hour distribution
sns.boxplot(df['start_hour'], color='blue')
plt.title('Start hour distribution', fontweight='bold', fontsize=16)
plt.xlabel('Hour')
plt.show()

# No outliers which is really good
```


![png](output_23_0.png)


### Discuss the distribution(s) of your variable(s) of interest. Were there any unusual points? Did you need to perform any transformations?

> The trip duration is right skewed as most trip is around 10 to 13 minutes. There are also some trips with 3000 seconds, nearly one hour. 

> Ask for the month, June is the one with less bike trip. In my opinion, June is the start of summer and people tend to go out less due to hotness. However, peek is in October and it's pretty symmetric that as the whether get colder or hotter, the number of trip slightly decrease, except for June. 

> Overall, there are less bike trip in the weekend. Weekday has more bike trip. Tuesday and Wednesday has approximately the same number of trips. However, the number decrease as it get closer and closer to the weekend and rise back in the first day of the week (Monday).

> About start hour distribution, there is no outlier displayed on the boxplot therefore I'm not worried about any extreme value. However, the min and max value is 0 and 24 ... Who rent a bike in the middle of the night (Maybe visitors who want to explore the city?)

### Of the features you investigated, were there any unusual distributions? Did you perform any operations on the data to tidy, adjust, or change the form of the data? If so, why did you do this?

> As of this point, there is no unsual distributions except for the right skewed in trip duration.

> Some data inspection: checking for nulls, duplicated, make sure format is right

> Some data cleaning: Change start and end from string to panda datetime format so that I could extract data from it easier. Drop some unused columns.

> Why? To make the data cleaner and to avoid misinterpreting when ploting and making decision.

### Bivariate


```python
## Overall corralation looking and choosing out variable that has the highest correlation

plt.figure(figsize=(20,10))
sns.heatmap(df[['duration_sec', 'start_hour', 'start_month']].corr(), annot=True)
plt.title("Correlation between variable", fontsize=24, fontweight='bold')
plt.show()
```


![png](output_26_0.png)



```python
## Start hour vs Trip duration
plt.scatter(df['start_month'],df['duration_sec'])
plt.title('Start hour vs Trip duration')
plt.xlabel('Hour')
plt.ylabel('Trip duration (second)')
plt.show()
```


![png](output_27_0.png)



```python
sns.catplot(x="user_type", y="duration_sec", data=df)
plt.title('Trip duration base on user type', fontweight='bold', fontsize=16)
plt.xlabel('User Type')
plt.ylabel('Trip duration (second)')
plt.show()
```


![png](output_28_0.png)



```python
## This is a multivariate
sns.countplot(df['start_month'], hue=df['user_type'])
plt.title('Number of bike trips base on user type', fontweight='bold', fontsize=16)
plt.xlabel('Month')
plt.ylabel('Number of trips')
plt.show()
```


![png](output_29_0.png)



```python
facetgrid = sns.FacetGrid(data=df, col='user_type', col_wrap = 4, height = 6, aspect=2, sharey=False)
facetgrid.map(sns.countplot, 'start_hour')
facetgrid.axes[0].set_title('Bike trip hour for customer', fontweight='bold', fontsize=24)
facetgrid.axes[1].set_title('Bike trip hour for subscriber', fontweight='bold', fontsize=24)
facetgrid.axes[0].set_xlabel('Hours of a day', fontsize=22)
facetgrid.axes[1].set_xlabel('Hours of a day', fontsize=22)
facetgrid.axes[0].set_ylabel('Number of trips', fontsize=22)
facetgrid.axes[1].set_ylabel('Number of trips', fontsize=22)
plt.show()
```

    C:\Users\phuon\anaconda3\lib\site-packages\seaborn\axisgrid.py:728: UserWarning: Using the countplot function without specifying `order` is likely to produce an incorrect plot.
      warnings.warn(warning)
    


![png](output_30_1.png)



```python
sub = dict(df[df['user_type']=='Subscriber']['start_station_name'].value_counts())
cus = dict(df[df['user_type']=='Customer']['start_station_name'].value_counts())

y_sub=[]
y_cus=[]

x = df['start_station_name'].value_counts().index[0:15]

for i in x:
    y_sub.append(sub[i])
    y_cus.append(cus[i])
    
dummy_df = pd.DataFrame({'customer': y_cus, 'subscriber':y_sub}, index=x)
dummy_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer</th>
      <th>subscriber</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>San Francisco Ferry Building (Harry Bridges Plaza)</th>
      <td>5210</td>
      <td>9977</td>
    </tr>
    <tr>
      <th>The Embarcadero at Sansome St</th>
      <td>5864</td>
      <td>7800</td>
    </tr>
    <tr>
      <th>San Francisco Caltrain (Townsend St at 4th St)</th>
      <td>1046</td>
      <td>11500</td>
    </tr>
    <tr>
      <th>San Francisco Caltrain Station 2  (Townsend St at 4th St)</th>
      <td>985</td>
      <td>11070</td>
    </tr>
    <tr>
      <th>Market St at 10th St</th>
      <td>1847</td>
      <td>10113</td>
    </tr>
    <tr>
      <th>Montgomery St BART Station (Market St at 2nd St)</th>
      <td>1750</td>
      <td>9584</td>
    </tr>
    <tr>
      <th>Berry St at 4th St</th>
      <td>1439</td>
      <td>9517</td>
    </tr>
    <tr>
      <th>Powell St BART Station (Market St at 4th St)</th>
      <td>3174</td>
      <td>6968</td>
    </tr>
    <tr>
      <th>Howard St at Beale St</th>
      <td>660</td>
      <td>9266</td>
    </tr>
    <tr>
      <th>Steuart St at Market St</th>
      <td>1628</td>
      <td>7719</td>
    </tr>
    <tr>
      <th>Powell St BART Station (Market St at 5th St)</th>
      <td>2087</td>
      <td>5900</td>
    </tr>
    <tr>
      <th>Embarcadero BART Station (Beale St at Market St)</th>
      <td>1014</td>
      <td>6635</td>
    </tr>
    <tr>
      <th>2nd St at Townsend St - Coming Soon</th>
      <td>1038</td>
      <td>5567</td>
    </tr>
    <tr>
      <th>3rd St at Townsend St</th>
      <td>1089</td>
      <td>5325</td>
    </tr>
    <tr>
      <th>Townsend St at 7th St</th>
      <td>489</td>
      <td>5734</td>
    </tr>
  </tbody>
</table>
</div>




```python
ax = dummy_df.plot.barh()
plt.title("User Type and Top 10 Stations", fontsize=18, fontweight='bold')
plt.xlabel('Number of trips taken from this station')
plt.show()
```


![png](output_32_0.png)


### Talk about some of the relationships you observed in this part of the investigation. How did the feature(s) of interest vary with other features in the dataset?

> User Type and Trip Duration: When comparing user type and trip duration, both of the user type has linear relationship with the trip duration as when the trip duration increase, it is getting less and less dense. However, customer tends to have their bike trip longer than subscriber as from around 20000 seconds, it starts to be less compact for subscibers whereas customer points remain densly for almost every of the trip durations. 

> Number of bike trip within every month and User Type: Unlike trip duration, subscriber tends to have shorter trip duration but do more trips as within every month, subscribers always have double (triple for some months) amount of number of bike trip than customers. What is more, the trip distribution for both user type is not the same. Subscriber numer of trip peek in October while for customer is in September. Subscribers number of trips decrease more when it gets colder/hotter. However, customers' number of trip is only slightly change except for June and July.

> Trip start hour and user type: Subsciber has a unimodal shape in 8 and 16 o'clock. Both of them is left skewed. However, Customer is sharply skewed when compare to subsciber.

### Did you observe any interesting relationships between the other features (not the main feature(s) of interest)?

> There was no actual relationship between the top 10 stations and the number of trips have taken from that station. 

> It's hard to find out specific correlation because user type is categorical.

### Multivariate


```python
## Trip duration within different month base on user type

plt.figure(figsize = [6,4])
sns.pointplot(ci=None, x = df['start_month'], y = df['duration_sec'], hue = df['user_type'])
plt.title('Trip duration in each month of the year', fontweight='bold', fontsize=16)
plt.ylabel('Average Trip Duration (secconds)')
plt.xlabel('Month')
plt.show();
```


![png](output_35_0.png)



```python
## Trip duration within different month base on user type

plt.figure(figsize = [6,4])
sns.pointplot(ci=None, x = df['start_hour'], y = df['duration_sec'], hue = df['user_type'])
plt.title('Trip duration in each hour of the day', fontweight='bold', fontsize=16)
plt.ylabel('Average Trip Duration (secconds)')
plt.xlabel('Hour')
plt.show();
```


![png](output_36_0.png)



```python
## This is a multivariate
sns.countplot(df['start_hour'], hue=df['user_type'])
plt.title('Number of bike trips base on user type', fontweight='bold', fontsize=16)
plt.xlabel('Hour')
plt.ylabel('Number of trips')
plt.show()
```


![png](output_37_0.png)


### Talk about some of the relationships you observed in this part of the investigation. Were there features that strengthened each other in terms of looking at your feature(s) of interest?

> When I fisrt look at the member type and trip duration, I thought that customers do bike trips more than subscribers. However, it turn out that customers has higher trip durations in average than subscribers but make lower bike trips.

> Trip Duration base on different months for each user type also support the above conclusion. Except for 3 am, trip duration for subscriber base on month remains stable while fluctuating for customers' trip duration. 

> Trip Duration base on different hour of the day for each user show a bimodal with merely normal distributed with peak at 8 am and 5 pm. Meanwhile, for customers, the number of trips spread out evenly for "working hours' and start to decrease when night time comes. For both of the user type, there is almost no trip for 2am to 4am. 

> There is no bike trip being made from January to May for the investigated year. However, subscibers' amount of bike trips is double (almost tripple for October, November, December) when compare with customers'. 


### Were there any interesting or surprising interactions between features?

> Before I started this project, I make a lot of assumptions about relationship between but after some processed, everything start to be cleared and I can see connection between factors verse user types is that:

>> The subsriber has lower average trip duration but more number of trip.

>> People in the investigated area like to make bike trip when the whether remain cool as there are less bike trip when the whether gets hotter or colder. 

>> For subscribers, they do biking scheduly since there is a bimodel shape and for customer, it's oscassionally since it's widely distributed.


```python
df.to_csv('df_final.csv', index=False)
```

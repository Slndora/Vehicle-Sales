# Vehicle-Sales
## Vehicle Sales Insights:A Comprehensive Analysis of Sales, Pricing, and Trends
![alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/7317651.jpg)
## Objective
The objective of this project is to analyze a vehicle sales dataset to uncover key trends and factors influencing car prices and demand. By examining variables like make, model, condition, odometer, and sales data, the project aims to provide insights that help optimize pricing, inventory, and market strategies in automotive sales.
## Table of Contents
- [Table of Contents](#table-of-contents)
- [Data Overview](#data-overview)
- [Analysis Goals](#analysis-goals)
- [Methodology](#methodology)
- [Technologies Used](#technologies-used)
- [Importing the data](#importing-the-data)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Univariate Analysis](#univariate-analysis)
- [Bivariate analysis](#bivariate-analysis)
- [Multi variate analysis](#multi-variate-analysis)
- [Measures in Power BI](#measures-in-power-bI)
- [Dashboard](#dashboard)
- [Acknowledgments](#acknowledgments)
 
## Data Overview
This dataset provides information on used car sales, including key variables that capture various attributes of the cars,

such as their make, model, year of manufacture, transmission type, odometer reading, and selling price. The dataset also

contains additional details about the condition of the cars, state of sale, and more.

Key columns in the dataset:

1) Year: The year the car was manufactured.
2) Make: The brand of the car.
3) Model: The specific model of the car.
4) Trim: A variant or version of the model with different features.
5) Body: The type or category of the car (e.g., SUV, Sedan).
6) Transmission: Type of transmission (automatic or manual).
7) VIN: Vehicle Identification Number (unique identifier for each car).
8) State: The state where the car is sold.
9) Condition: The condition of the car when sold (e.g., new, used).
10) Odometer: Number of miles the car has been driven.
11) Color: The exterior color of the car.
12) Interior: The interior color/material of the car.
13) Seller: The seller of the car.
14) MMR: Manheim Market Report value (provides a price benchmark for the vehicle).
15) Selling Price: The actual selling price of the car.
16) Sale Date: The date the car was sold.

## Analysis Goals
Here are key analysis goals for your vehicle sales dataset:

1) Price Determinants: Identify the factors (e.g., make, model, year, condition, odometer) that most significantly influence the selling price of vehicles.
2) Sales Trends: Analyze sales trends over time (e.g., by year, month, or season) to determine peak sales periods and seasonal patterns.
3) Market Segmentation: Segment the market based on attributes like vehicle type (body style), condition (new vs. used), or seller to understand specific market behaviors and preferences.
4) Geographic Analysis: Explore sales performance across different states, identifying regional variations in demand, pricing, and vehicle preferences.
5) Condition and Pricing Relationship: Investigate how vehicle condition (new vs. used) affects pricing, including price depreciation for used vehicles based on mileage and age.
6) Odometer and Price Correlation: Examine how the number of miles a vehicle has been driven (odometer) correlates with its selling price, to understand depreciation patterns.
7) Model and Trim-Level Analysis: Evaluate how specific vehicle models and their trim variations affect sales and pricing, identifying premium vs. base model trends.
8) Seller Performance: Assess how different sellers influence vehicle pricing and sales volume, identifying top-performing sellers and potential pricing strategies.
9) VIN and Unique Vehicle Characteristics: Identify unique characteristics or anomalies related to specific VINs and their impact on sales price or sales volume.
10) Comparison with MMR: Compare actual selling prices with the Manheim Market Report (MMR) values to assess pricing accuracy and market competitiveness.
These goals aim to provide actionable insights for pricing strategies, inventory management, and understanding market dynamics within the automotive sales industry.

## Methodology
- Data Cleaning & Preparation: Ensure data integrity and consistency.
- Descriptive Analysis: Generate summary statistics and visualizations to identify trends.
- Inferential Analysis: Apply statistical methods to test hypotheses and draw conclusions.
- Data Visualization: Utilize tools like Power BI to create interactive dashboards.

## Technologies Used
1) Python (for Exploratory Data Analysis - EDA): Python was used for conducting thorough exploratory data analysis (EDA) on the vehicle sales dataset. Key libraries such as Pandas were used for data manipulation and cleaning, Matplotlib and Seaborn for data visualization, and NumPy for numerical operations. Python enabled the analysis of relationships between different variables (e.g., price, odometer, condition) and allowed for statistical analysis, trend detection, and data transformation to prepare insights for further visualization.
2) Power BI (for Data Visualization): Power BI was employed to create interactive and insightful visualizations from the processed dataset. The platform's drag-and-drop interface facilitated the creation of dashboards that allow for easy exploration of trends, distributions, and comparisons in the vehicle sales data. Visualizations such as bar charts, scatter plots, line graphs, and geographical maps provided a clear, accessible way to communicate key insights and patterns to stakeholders.

## Importing the data
To begin the analysis, I imported the vehicle sales dataset from a CSV file into Python using the Pandas library. The pd.read_csv() function was used to load the dataset into a DataFrame, which allowed for efficient data manipulation, cleaning, and analysis. This step enabled me to explore and preprocess the dataset before performing any exploratory data analysis (EDA).

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import warnings
warnings.filterwarnings("ignore")
df=pd.read_csv('C:/Users/akash/Downloads/.kaggle/car_prices.csv')
```
```
df.head()
year	make	model	trim	body	transmission	vin	state	condition	odometer	color	interior	seller	mmr	sellingprice	saledate
0	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg566472	ca	5.0	16639.0	white	black	kia motors america inc	20500.0	21500.0	Tue Dec 16 2014 12:30:00 GMT-0800 (PST)
1	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg561319	ca	5.0	9393.0	white	beige	kia motors america inc	20800.0	21500.0	Tue Dec 16 2014 12:30:00 GMT-0800 (PST)
2	2014	BMW	3 Series	328i SULEV	Sedan	automatic	wba3c1c51ek116351	ca	45.0	1331.0	gray	black	financial services remarketing (lease)	31900.0	30000.0	Thu Jan 15 2015 04:30:00 GMT-0800 (PST)
3	2015	Volvo	S60	T5	Sedan	automatic	yv1612tb4f1310987	ca	41.0	14282.0	white	black	volvo na rep/world omni	27500.0	27750.0	Thu Jan 29 2015 04:30:00 GMT-0800 (PST)
4	2014	BMW	6 Series Gran Coupe	650i	Sedan	automatic	wba6b2c57ed129731	ca	43.0	2641.0	gray	black	financial services remarketing (lease)	66000.0	67000.0	Thu Dec 18 2014 12:30:00 GMT-0800 (PST)
```


### Data overview
```
df.shape
(558837, 16)
```
```

df.columns
Index(['year', 'make', 'model', 'trim', 'body', 'transmission', 'vin', 'state',
       'condition', 'odometer', 'color', 'interior', 'seller', 'mmr',
       'sellingprice', 'saledate'],
      dtype='object')
```
```

df.count()
year            558837
make            548536
model           548438
trim            548186
body            545642
transmission    493485
vin             558833
state           558837
condition       547017
odometer        558743
color           558088
interior        558088
seller          558837
mmr             558799
sellingprice    558825
saledate        558825
dtype: int64
```
```

df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 558837 entries, 0 to 558836
Data columns (total 16 columns):
 #   Column        Non-Null Count   Dtype  
---  ------        --------------   -----  
 0   year          558837 non-null  int64  
 1   make          548536 non-null  object 
 2   model         548438 non-null  object 
 3   trim          548186 non-null  object 
 4   body          545642 non-null  object 
 5   transmission  493485 non-null  object 
 6   vin           558833 non-null  object 
 7   state         558837 non-null  object 
 8   condition     547017 non-null  float64
 9   odometer      558743 non-null  float64
 10  color         558088 non-null  object 
 11  interior      558088 non-null  object 
 12  seller        558837 non-null  object 
 13  mmr           558799 non-null  float64
 14  sellingprice  558825 non-null  float64
 15  saledate      558825 non-null  object 
dtypes: float64(4), int64(1), object(11)
memory usage: 68.2+ MB
```
```

df.describe()
year	condition	odometer	mmr	sellingprice
count	558837.000000	547017.000000	558743.000000	558799.000000	558825.000000
mean	2010.038927	30.672365	68320.017767	13769.377495	13611.358810
std	3.966864	13.402832	53398.542821	9679.967174	9749.501628
min	1982.000000	1.000000	1.000000	25.000000	1.000000
25%	2007.000000	23.000000	28371.000000	7100.000000	6900.000000
50%	2012.000000	35.000000	52254.000000	12250.000000	12100.000000
75%	2013.000000	42.000000	99109.000000	18300.000000	18200.000000
max	2015.000000	49.000000	999999.000000	182000.000000	230000.000000
```
```

df.columns = df.columns.str.strip().str.lower()

```

## Data cleaning

```
plt.figure(figsize=(14, 6))

sns.heatmap(df.isnull(), cbar=False,cmap='inferno')
plt.xticks(rotation=30)

plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120636.png)

```
null_percentage= (df.isnull().sum()/df.shape[0])*100

plt.figure(figsize=(12,6))
null_percentage.plot(kind='bar',color='skyblue')
plt.title('Null percentage in columns')
plt.xlabel('columns')
plt.ylabel('null percentage(%')
plt.xticks(rotation=30)
plt.grid(axis='y')
plt.gcf().patch.set_facecolor('lightgreen')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120726.png)

```
fill_methods = {

    'make': 'mode',

    'model': 'mode',

    'trim': 'mode',

    'body': 'mode',

    'transmission': 'mode',

}

for column, method in fill_methods.items():

    if method == 'median':

        df[column].fillna(df[column].median(), inplace=True)

    elif method == 'mode':

        df[column].fillna(df[column].mode()[0], inplace=True)
```
```


df.isnull().mean() * 100
year            0.000000
make            0.000000
model           0.000000
trim            0.000000
body            0.000000
transmission    0.000000
vin             0.000716
state           0.000000
condition       2.115107
odometer        0.016821
color           0.134028
interior        0.134028
seller          0.000000
mmr             0.006800
sellingprice    0.002147
saledate        0.002147
dtype: float64

```
```
df = df.dropna(subset=['sellingprice', 'saledate', 'mmr', 'make', 'color', 'odometer', 'condition', 'interior'])
df.isnull().mean() * 100
year            0.0
make            0.0
model           0.0
trim            0.0
body            0.0
transmission    0.0
vin             0.0
state           0.0
condition       0.0
odometer        0.0
color           0.0
interior        0.0
seller          0.0
mmr             0.0
sellingprice    0.0
saledate        0.0
dtype: float64
```
```

df.describe()
year	condition	odometer	mmr	sellingprice
count	546325.000000	546325.000000	546325.000000	546325.000000	546325.000000
mean	2010.132280	30.669557	67289.743418	13903.192697	13751.715761
std	3.906608	13.400986	52781.847842	9652.965754	9724.318611
min	1982.000000	1.000000	1.000000	25.000000	1.000000
25%	2008.000000	23.000000	28072.000000	7375.000000	7100.000000
50%	2012.000000	35.000000	51260.000000	12400.000000	12300.000000
75%	2013.000000	42.000000	97438.000000	18400.000000	18300.000000
max	2015.000000	49.000000	999999.000000	182000.000000	230000.000000
```
```

df.duplicated().sum()
0

```
### Handling date data

```
df['saledate'] = pd.to_datetime(df['saledate'], utc=True)

df['sale_year'] = df['saledate'].dt.year

df['sale_month'] = df['saledate'].dt.month

df['sale_day'] = df['saledate'].dt.day

df['sale_dayofweek'] = df['saledate'].dt.dayofweek

df.dtypes
year                            int64
make                           object
model                          object
trim                           object
body                           object
transmission                   object
vin                            object
state                          object
condition                     float64
odometer                      float64
color                          object
interior                       object
seller                         object
mmr                           float64
sellingprice                  float64
saledate          datetime64[ns, UTC]
sale_year                       int32
sale_month                      int32
sale_day                        int32
sale_dayofweek                  int32
```

### Renaming states
```
state_names = {

'ca': 'California', 'tx': 'Texas', 'pa': 'Pennsylvania', 'mn': 'Minnesota',

'az': 'Arizona', 'wi': 'Wisconsin', 'tn': 'Tennessee', 'md': 'Maryland',

'fl': 'Florida', 'ne': 'Nebraska', 'nj': 'New Jersey', 'nv': 'Nevada',

'oh': 'Ohio', 'mi': 'Michigan', 'ga': 'Georgia', 'va': 'Virginia',

'sc': 'South Carolina', 'nc': 'North Carolina', 'in': 'Indiana',

'il': 'Illinois', 'co': 'Colorado', 'ut': 'Utah', 'mo': 'Missouri',

'ny': 'New York', 'ma': 'Massachusetts', 'pr': 'Puerto Rico', 'or': 'Oregon',

'la': 'Louisiana', 'wa': 'Washington', 'hi': 'Hawaii', 'qc': 'Quebec',

'ab': 'Alberta', 'on': 'Ontario', 'ok': 'Oklahoma', 'ms': 'Mississippi',

'nm': 'New Mexico', 'al': 'Alabama', 'ns': 'Nova Scotia'
}
```
```
df['state'] = df['state'].map(state_names) 
df.head()
year	make	model	trim	body	transmission	vin	state	condition	odometer	color	interior	seller	mmr	sellingprice	saledate	sale_year	sale_month	sale_day	sale_dayofweek
0	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg566472	California	5.0	16639.0	white	black	kia motors america inc	20500.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1
1	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg561319	California	5.0	9393.0	white	beige	kia motors america inc	20800.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1
2	2014	BMW	3 Series	328i SULEV	Sedan	automatic	wba3c1c51ek116351	California	45.0	1331.0	gray	black	financial services remarketing (lease)	31900.0	30000.0	2015-01-14 20:30:00+00:00	2015	1	14	2
3	2015	Volvo	S60	T5	Sedan	automatic	yv1612tb4f1310987	California	41.0	14282.0	white	black	volvo na rep/world omni	27500.0	27750.0	2015-01-28 20:30:00+00:00	2015	1	28	2
4	2014	BMW	6 Series Gran Coupe	650i	Sedan	automatic	wba6b2c57ed129731	California	43.0	2641.0	gray	black	financial services remarketing (lease)	66000.0	67000.0	2014-12-18 04:30:00+00:00	2014	12	18	

```
### Outliers

```
o_plot=['condition','odometer','mmr','sellingprice']
```
```
df.shape
(546325, 20)
```
```
def identify_outliers(df, col):
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR

    outliers = df[(df[col] < lower_bound) | (df[col] > upper_bound)]
    
    return outliers, lower_bound, upper_bound

plt.figure(figsize=(10, 6))
for i, col in enumerate(col_to_plot):
    if col == 'condition': 
        continue

    outliers, lower, upper = identify_outliers(df, col)
    
    plt.subplot(2, 2, i+1)
    sns.boxplot(x=df[col])
    plt.title(f'Boxplot for {col}')

    plt.scatter(outliers[col], np.zeros_like(outliers[col]), color='red', label='Outliers', zorder=3)
    
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120739.png)

```
def remove_outliers(df, col):
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    
    return df[(df[col] >= lower_bound) & (df[col] <= upper_bound)]
    
for col in col_to_plot:
    if col != 'condition':  
        df = remove_outliers(df, col)

```
### Handling Missing Values
```
df.dropna(inplace=True)
```
```
df['Price_diff'] = df['sellingprice'] - df['mmr']
```
```
df.head()
year	make	model	trim	body	transmission	vin	state	condition	odometer	...	interior	seller	mmr	sellingprice	saledate	sale_year	sale_month	sale_day	sale_dayofweek	Price_diff
0	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg566472	California	5.0	16639.0	...	black	kia motors america inc	20500.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1	1000.0
1	2015	Kia	Sorento	LX	SUV	automatic	5xyktca69fg561319	California	5.0	9393.0	...	beige	kia motors america inc	20800.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1	700.0
2	2014	BMW	3 Series	328i SULEV	Sedan	automatic	wba3c1c51ek116351	California	45.0	1331.0	...	black	financial services remarketing (lease)	31900.0	30000.0	2015-01-14 20:30:00+00:00	2015	1	14	2	-1900.0
3	2015	Volvo	S60	T5	Sedan	automatic	yv1612tb4f1310987	California	41.0	14282.0	...	black	volvo na rep/world omni	27500.0	27750.0	2015-01-28 20:30:00+00:00	2015	1	28	2	250.0
5	2015	Nissan	Altima	2.5 S	Sedan	automatic	1n4al3ap1fn326013	California	1.0	5554.0	...	black	enterprise vehicle exchange / tra / rental / t...	15350.0	10900.0	2014-12-30 04:00:00+00:00	2014	12	30	1	-4450.0
5 rows × 21 columns

```
### Handling Missing and Inconsistent Values in Categorical Columns

```
Categorical_col = df.select_dtypes(include= 'object').columns
df[Categorical_col] = df[Categorical_col].apply(lambda col: col.str.upper())
```
```
df.head()
year	make	model	trim	body	transmission	vin	state	condition	odometer	...	interior	seller	mmr	sellingprice	saledate	sale_year	sale_month	sale_day	sale_dayofweek	Price_diff
0	2015	KIA	SORENTO	LX	SUV	AUTOMATIC	5XYKTCA69FG566472	CALIFORNIA	5.0	16639.0	...	BLACK	KIA MOTORS AMERICA INC	20500.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1	1000.0
1	2015	KIA	SORENTO	LX	SUV	AUTOMATIC	5XYKTCA69FG561319	CALIFORNIA	5.0	9393.0	...	BEIGE	KIA MOTORS AMERICA INC	20800.0	21500.0	2014-12-16 04:30:00+00:00	2014	12	16	1	700.0
2	2014	BMW	3 SERIES	328I SULEV	SEDAN	AUTOMATIC	WBA3C1C51EK116351	CALIFORNIA	45.0	1331.0	...	BLACK	FINANCIAL SERVICES REMARKETING (LEASE)	31900.0	30000.0	2015-01-14 20:30:00+00:00	2015	1	14	2	-1900.0
3	2015	VOLVO	S60	T5	SEDAN	AUTOMATIC	YV1612TB4F1310987	CALIFORNIA	41.0	14282.0	...	BLACK	VOLVO NA REP/WORLD OMNI	27500.0	27750.0	2015-01-28 20:30:00+00:00	2015	1	28	2	250.0
5	2015	NISSAN	ALTIMA	2.5 S	SEDAN	AUTOMATIC	1N4AL3AP1FN326013	CALIFORNIA	1.0	5554.0	...	BLACK	ENTERPRISE VEHICLE EXCHANGE / TRA / RENTAL / T...	15350.0	10900.0	2014-12-30 04:00:00+00:00	2014	12	30	1	-4450.0
5 rows × 21 columns

```
```
df['seller'].unique()
array(['KIA MOTORS AMERICA  INC',
       'FINANCIAL SERVICES REMARKETING (LEASE)',
       'VOLVO NA REP/WORLD OMNI', ..., 'CHESTERFIELD MOTORSPORTS LLC',
       'ALTERNATIVE FINANCIAL GROUP INC', 'I -5 UHLMANN RV'], dtype=object)
df['seller'] = df['seller'].str.lower().str.strip()
```
```
df['seller'] = df['seller'].str.replace('-', ' ', regex=False)
df['seller'].value_counts()
seller
nissan infiniti lt               29472
ford motor credit company llc    18704
the hertz corporation            17932
santander consumer               15103
avis corporation                 12045
                                 ...  
conroe auto credit                   1
home financial service               1
courtesy car co. llc                 1
us acceptance                        1
i  5 uhlmann rv                      1
Name: count, Length: 12468, dtype: int64
columns_with_weird_values = ['color', 'interior']

```
```
for column in columns_with_weird_values:
    weird_rows_count = df[df[column] == '—'].shape[0]
    total_rows = df.shape[0]
    percentage_weird_rows = (weird_rows_count / total_rows) * 100

    print(f'Column: {column}')
    print(f'Weird rows count: {weird_rows_count}')
    print(f'Percentage of weird rows: {percentage_weird_rows:.2f}%\n')
Column: color
Weird rows count: 23049
Percentage of weird rows: 4.48%

Column: interior
Weird rows count: 10662
Percentage of weird rows: 2.07%
```
```
for col in ['color', 'interior']:

    most_common_value = df[col].mode()[0]

    df[col] = df[col].replace('—', most_common_value)

    weird_rows_count = df[df[col] == '—'].shape[0]

    percentage_weird_rows = (weird_rows_count / df.shape[0]) * 100

    print(f"Percentage of rows with weird '{col}' values after replacement: {percentage_weird_rows:.2f}%")
Percentage of rows with weird 'color' values after replacement: 0.00%
Percentage of rows with weird 'interior' values after replacement: 0.00%
```
```
df.isnull().mean() * 100
year              0.0
make              0.0
model             0.0
trim              0.0
body              0.0
transmission      0.0
vin               0.0
state             0.0
condition         0.0
odometer          0.0
color             0.0
interior          0.0
seller            0.0
mmr               0.0
sellingprice      0.0
saledate          0.0
sale_year         0.0
sale_month        0.0
sale_day          0.0
sale_dayofweek    0.0
Price_diff        0.0
dtype: float64
```
```
df.types
year                            int64
make                           object
model                          object
trim                           object
body                           object
transmission                   object
vin                            object
state                          object
condition                     float64
odometer                      float64
color                          object
interior                       object
seller                         object
mmr                           float64
sellingprice                  float64
saledate          datetime64[ns, UTC]
sale_year                       int32
sale_month                      int32
sale_day                        int32
sale_dayofweek                  int32
Price_diff                    float64
dtype: object
```
```
df.columns
Index(['year', 'make', 'model', 'trim', 'body', 'transmission', 'vin', 'state',
       'condition', 'odometer', 'color', 'interior', 'seller', 'mmr',
       'sellingprice', 'saledate', 'sale_year', 'sale_month', 'sale_day',
       'sale_dayofweek', 'Price_diff'],
      dtype='object')
```
```
df.describe().T
count	mean	std	min	25%	50%	75%	max
year	515002.0	2010.169813	3.783585	1982.0	2008.00	2012.0	2013.00	2015.0
condition	515002.0	30.717947	13.217493	1.0	24.00	35.0	41.00	49.0
odometer	515002.0	65364.194213	46131.399387	1.0	28908.25	52108.0	96316.75	201485.0
mmr	515002.0	12977.228486	7371.044690	25.0	7475.00	12200.0	17650.00	34700.0
sellingprice	515002.0	12812.337170	7455.765930	1.0	7200.00	12100.0	17600.00	33400.0
sale_year	515002.0	2014.923459	0.265863	2014.0	2015.00	2015.0	2015.00	2015.0
sale_month	515002.0	3.616141	3.028018	1.0	1.00	2.0	6.00	12.0
sale_day	515002.0	14.548986	8.661816	1.0	7.00	15.0	22.00	31.0
sale_dayofweek	515002.0	1.444025	1.236829	0.0	1.00	1.0	2.00	6.0
Price_diff	515002.0	-164.891317	1592.862485	-31200.0	-800.00	-50.0	625.00	23050.0
```
```
df.to_csv('cleaned_car_prices.csv', index=False)

```
## Exploratory Data Analysis
## Univariate Analysis
1) Make
```
plt.figure(figsize=(24,8))
sns.countplot(data=df, x='make')
plt.title('Frequency Distribution of Car Makes')
plt.xticks(rotation=70)
plt.gcf().patch.set_facecolor('lightgreen')
plt.show()

```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120753.png)

2) State
```
plt.figure(figsize=(20,8))
sns.countplot(data=df, x='state')
plt.title('Frequency Distribution of Car over states')
plt.xticks(rotation=70)
plt.gcf().patch.set_facecolor('lightgreen')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120816.png)

3) condition
```
plt.figure(figsize=(14,4))
sns.countplot(data=df, x='condition')
plt.title('Frequency Distribution of Car over condition')
plt.xticks(rotation=70)
plt.gcf().patch.set_facecolor('lightgreen')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120824.png)

4) Distribution of Selling Price
```
plt.figure(figsize=(12, 6))
sns.histplot(df['sellingprice'], bins=30, kde=True, color='blue', edgecolor='black')
plt.title('Distribution of Selling Price', fontsize=16)
plt.xlabel('Selling Price', fontsize=14)
plt.ylabel('Frequency', fontsize=14)
plt.grid(axis='y', linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120831.png)

5) Distribution of Odometer
```
plt.figure(figsize=(12, 6))
sns.histplot(df['odometer'], bins=30, kde=True, color='red', edgecolor='black')
plt.title('Distribution of odometer', fontsize=16)
plt.xlabel('Selling Price', fontsize=14)
plt.ylabel('Frequency', fontsize=14)
plt.grid(axis='y', linestyle='--', alpha=0.5)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120841.png)

6) model 
```
plt.figure(figsize=(10, 4))
sns.set_theme(style="ticks")
sns.countplot(y='model', data=df, order=df['model'].value_counts().index[:10], palette='colorblind')
plt.title('Top 10 Car Models', fontsize=16, fontweight='bold')
plt.xlabel('Count', fontsize=14)
plt.ylabel('Model', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120848.png)

7) trim 
```
plt.figure(figsize=(10, 4))
sns.set_theme(style="darkgrid")
sns.countplot(y='trim', data=df, order=df['trim'].value_counts().index[:10], palette='viridis')
plt.title('Top 10 Car Trims', fontsize=16, fontweight='bold')
plt.xlabel('Count', fontsize=14)
plt.ylabel('Trim', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120855.png)

8) body types
```
plt.figure(figsize=(10, 4))
sns.set_theme(style="darkgrid")
sns.countplot(y='body', data=df, order=df['body'].value_counts().index[:10], palette='dark')
plt.title('Top 10 Car Body Types', fontsize=16, fontweight='bold')
plt.xlabel('Count', fontsize=14)
plt.ylabel('Body', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120901.png)

9) color
```
plt.figure(figsize=(10, 6))
sns.set(style="whitegrid")
custom_palette = {'BLACK': 'black','WHITE': 'white','SILVER': 'silver','GRAY': 'gray','BLUE': 'blue','RED': 'red','GOLD': 'gold','GREEN': 'green',
                  'BEIGE': 'beige','BURGUNDY': 'maroon','BROWN': 'brown','ORANGE': 'orange','PURPLE': 'purple','OFF-WHITE': 'lightgray',
                  'YELLOW': 'yellow','CHARCOAL': 'dimgray','TURQUOISE': 'turquoise','PINK': 'pink','LIME': 'lime'}
color_counts = df['color'].value_counts().reset_index()
color_counts.columns = ['color', 'count']

bar_plot = sns.barplot(x='color', y='count', data=color_counts, palette=custom_palette)
for bar in bar_plot.patches:
    bar.set_edgecolor('black')
    bar.set_linewidth(1.5)
    
plt.title('Count of Cars by Color', fontsize=16)
plt.xlabel('Color', fontsize=14)
plt.ylabel('Count', fontsize=14)
plt.xticks(rotation=45, ha='right')
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120910.png)

10) sales trend 
```
palette_month = sns.color_palette("Set2", len(df['sale_month'].unique())) 
palette_day = sns.color_palette("dark:#5A9_r", len(df['sale_dayofweek'].unique())) 
palette_year = sns.color_palette("Blues", len(df['sale_year'].unique()))  

fig, axes = plt.subplots(1, 3, figsize=(15, 5))

sns.countplot(data=df, x='sale_year', palette=palette_year, ax=axes[0])
axes[0].set_title('Yearly Sales Distribution')
axes[0].set_xlabel('Year')

sns.countplot(data=df, x='sale_month', palette=palette_month, ax=axes[1])
axes[1].set_title('Monthly Sales Distribution')
axes[1].set_xlabel('Month')

sns.countplot(data=df, x='sale_dayofweek', palette=palette_day, ax=axes[2])
axes[2].set_title('Sales by Day of Week')
axes[2].set_xlabel('Day of Week')

plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120918.png)

11) Transmissiom 
```
sns.set_style('darkgrid')
fig = plt.figure(figsize=(8, 4))
axes = fig.subplots(1, 2)
transmission = df['transmission'].value_counts()

axes[0].pie(transmission,
             labels=transmission.index,
             autopct="%1.1f%%",
             explode=[0, 0.1],
             colors=['skyblue', 'green'],
             startangle=140)
axes[0].set_title('Transmission Percentage', fontsize=16)

sns.countplot(data=df, x='transmission', ax=axes[1], palette='deep')
axes[1].set_title('Transmission Count', fontsize=16)
axes[1].set_xlabel('Transmission', fontsize=14)
axes[1].set_ylabel('Count', fontsize=14)

plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120925.png)

12) State abbreviations
```
state_abbreviations = {'CALIFORNIA': 'CA','NEW JERSEY': 'NJ','GEORGIA': 'GA','VIRGINIA': 'VA','INDIANA': 'IN','ILLINOIS': 'IL','MINNESOTA': 'MN',
                       'MICHIGAN': 'MI','OHIO': 'OH','TEXAS': 'TX','ARIZONA': 'AZ','COLORADO': 'CO','MISSOURI': 'MO','PENNSYLVANIA': 'PA',
                       'NEBRASKA': 'NE','NEVADA': 'NV','MASSACHUSETTS': 'MA', 'MAUTAH': 'UT','PUERTO RICO': 'PR','NORTH CAROLINA': 'NC','FLORIDA': 'FL',
                       'SOUTH CAROLINA': 'SC','NEW YORK': 'NY','WISCONSIN': 'WI','MARYLAND': 'MD','TENNESSEE': 'TN','WASHINGTON': 'WA',
                       'LOUISIANA': 'LA','OREGON': 'OR','HAWAII': 'HI','OKLAHOMA': 'OK','MISSISSIPPI': 'MS','NEW MEXICO': 'NM','ALABAMA': 'AL'}

```
```
df_abb = df['state'].replace(state_abbreviations)
state_counts = df_abb.value_counts().reset_index()
state_counts.columns = ['state', 'count']

fig = px.choropleth(state_counts,locations='state',locationmode='USA-states',color='count',scope="usa",color_continuous_scale="reds",
                    title="Distribution of Selling Price Across States")

fig.show()
```

![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120933.png)

## Bivariate analysis

1) Avg Price by Odometer
```
df['odometer_group'] = (df['odometer'] // 5000) * 5000

avg_price_by_group = df.groupby('odometer_group')['sellingprice'].mean().reset_index()
avg_price_by_mileage = df.groupby('odometer')['sellingprice'].mean().reset_index()

sns.set_style("whitegrid")
sns.set_palette("pastel")

fig, axs = plt.subplots(1, 2, figsize=(18, 8))

sns.lineplot(data=avg_price_by_group, x='odometer_group', y='sellingprice', marker='o', ax=axs[0], color='black')
axs[0].set_title('Avg Price vs Odometer (Grouped)', fontsize=14)
axs[0].set_xlabel('Odometer (Miles)', fontsize=12)
axs[0].set_ylabel('Avg Price ($)', fontsize=12)
axs[0].tick_params(axis='x', rotation=45)

sns.scatterplot(data=avg_price_by_mileage, x='odometer', y='sellingprice', ax=axs[1], color='darkgreen')
axs[1].set_title('Avg Price by Odometer', fontsize=14)
axs[1].set_xlabel('Odometer (Miles)', fontsize=12)
axs[1].set_ylabel('Avg Price ($)', fontsize=12)

plt.tight_layout()
plt.show()

```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120939.png)

2) Selling Price vs MMR
```
   plt.figure(figsize=(10, 6))
sns.lineplot(x='mmr', y='sellingprice', data=df,color='blue')
plt.title('Selling Price vs MMR')
plt.xlabel('MMR')
plt.ylabel('Selling Price')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120946.png)

3) Average Selling Price by Condition
```
avg_price_by_condition = df.groupby('condition')['sellingprice'].mean().reset_index()

plt.figure(figsize=(14, 12))

plt.subplot(2, 1, 1)
sns.lineplot(data=avg_price_by_condition, x='condition', y='sellingprice', marker='o', color='orange')
plt.title('Average Selling Price by Condition', fontsize=18, fontweight='bold')
plt.xlabel('Condition', fontsize=14)
plt.ylabel('Average Selling Price ($)', fontsize=14)
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.grid(True, linestyle='--', alpha=0.7)

df['condition_group'] = pd.cut(df['condition'], bins=[0, 1, 2, 3, 4, 5],
                               labels=['Very Poor', 'Poor', 'Average', 'Good', 'Excellent'])

plt.subplot(2, 1, 2)
sns.boxplot(data=df, x='condition_group', y='sellingprice', palette='deep', 
            order=['Very Poor', 'Poor', 'Average', 'Good', 'Excellent'])
plt.title('Box Plot of Selling Price by Condition Group', fontsize=18, fontweight='bold')
plt.xlabel('Condition Group', fontsize=14)
plt.ylabel('Selling Price ($)', fontsize=14)
plt.xticks(rotation=45, fontsize=12)
plt.yticks(fontsize=12)
plt.grid(True, linestyle='--', alpha=0.7)

plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20120958.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121014.png)

4) Year vs Odometer
```
plt.figure(figsize=(12, 6))
sns.lineplot(data=df, x='year', y='odometer', color='blue', marker='x')
plt.title('Year vs Odometer', fontsize=16)
plt.xlabel('Year', fontsize=12)
plt.ylabel('Odometer (Miles)', fontsize=12)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121023.png)

5) Average Condition of Sold Cars Over the Years
```
 plt.figure(figsize=(10, 6))
sns.lineplot(x='year', y='condition', data=df, marker='o', linestyle='-', color='green')
plt.title('Average Condition of Sold Cars Over the Years', fontsize=18)
plt.xlabel('Year', fontsize=12)
plt.ylabel('Condition of Sold Car', fontsize=12)
plt.ylim(1, 50)
plt.xticks(fontsize=10)
plt.yticks(fontsize=10)
plt.grid(True, linestyle='-', alpha=0.4)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121031.png)

6) Distribution of Car Year and Total Revenue
```
import plotly.graph_objects as go
p = df.groupby('year').agg({'sellingprice': ['count', 'sum']})
p.columns = ['sales_count', 'total_revenue']

fig = go.Figure()
fig.add_trace(go.Bar(x=p.index, y=p['sales_count'], name='Sales Count', marker_color='blue'))
fig.add_trace(go.Scatter(x=p.index, y=p['total_revenue'], name='Total Revenue', 
                         mode='lines+markers', line=dict(color='orange'), yaxis='y2'))

fig.update_layout(
    title='Distribution of Car Year and Total Revenue',
    template='plotly_white',
    yaxis=dict(title='Cars Sold'),
    yaxis2=dict(title='Total Revenue', overlaying='y', side='right'))

fig.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121038.png)

7) Average Selling Price categories wise
```
 def categorize(price):
    if price < 10000:
        return 'Economical'
    elif 10000 <= price < 20000:
        return 'Medium'
    else:
        return 'High'

df['category'] = df['sellingprice'].apply(categorize)
df_avg = df.groupby(['make', 'category'], as_index=False)['sellingprice'].mean()

sns.set_theme(style="darkgrid", palette="muted") 
ordered_categories = ['High', 'Medium', 'Economical']
plt.figure(figsize=(22, 15))

for i, category in enumerate(ordered_categories):
    plt.subplot(3, 1, i + 1) 
    category_data = df_avg[df_avg['category'] == category].sort_values(by='sellingprice', ascending=False)
    sns.barplot(data=category_data, x='make', y='sellingprice', palette="Blues_d")
    plt.title(f'Average Selling Price - {category}', fontsize=18, weight='bold')
    plt.xlabel('Make', fontsize=14)
    plt.ylabel('Average Price ($)', fontsize=14)
    plt.xticks(rotation=45, ha='right', fontsize=12)
    plt.yticks(fontsize=12)
    
    for p in plt.gca().patches:
        plt.annotate(f'{p.get_height():,.0f}', 
                     (p.get_x() + p.get_width() / 2., p.get_height()), 
                     ha='center', va='bottom', fontsize=10, color='black')
        
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121111.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121139.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121148.png)

8) Selling Prices by Category
```
sns.set_theme(style="whitegrid", palette="pastel")
plt.figure(figsize=(10, 6))
sns.boxplot(data=df, x='category', y='sellingprice', palette='Set2')
plt.title('Box Plot of Selling Prices by Category', fontsize=20, weight='bold', color='darkblue')
plt.xlabel('Category', fontsize=14, weight='bold', color='darkblue')
plt.ylabel('Selling Price ($)', fontsize=14, weight='bold', color='darkblue')
plt.xticks(fontsize=12)
plt.yticks(fontsize=12)
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121200.png)

9) Percentage of Sales by State
```
state_sales = df.groupby('state')['sellingprice'].sum().sort_values(ascending=False)
top_6_states = state_sales.nlargest(5)
other_sales = state_sales.iloc[5:].sum()
other_series = pd.Series({'Other': other_sales})
top_6_states = pd.concat([top_6_states, other_series])

plt.figure(figsize=(7, 6))
colors = sns.color_palette("Set3", len(top_6_states))
explode = [0.1] + [0.02] * (len(top_6_states) - 1)

plt.pie(top_6_states.values,
        labels=top_6_states.index,
        autopct='%1.1f%%',
        explode=explode,
        colors=colors,
        startangle=290,
        wedgeprops={'edgecolor': 'black'},
        textprops={'fontsize': 14, 'weight': 'bold', 'color': 'black'},
       shadow=True)

plt.title('Percentage of Sales by State (Top 5 + Other)', fontsize=20, weight='bold', color='darkblue')
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121207.png)

10) Brand by Models Count
```
 brand_car = df.groupby('make', as_index=False)['model'].count().sort_values('model', ascending=False)
top_10 = brand_car.head(4)
other_total = brand_car.iloc[4:]['model'].sum()
other_data = pd.DataFrame({'make': ['Other'], 'model': [other_total]})
combin_data = pd.concat([top_10, other_data])
plt.figure(figsize=(7,6), facecolor='lavender')

colors = sns.color_palette('viridis', len(combin_data)) 
plt.pie(combin_data['model'], 
        labels=combin_data['make'], 
        autopct='%1.2f%%', 
        startangle=270, 
        colors=colors,
        wedgeprops={'edgecolor': 'black'},  
        textprops={'fontsize': 14, 'weight': 'bold', 'color': 'black'})

plt.title('Brand by Models Count', fontsize=20, weight='bold', color='darkblue')
plt.axis('equal')  
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121217.png)

11) Top sellers 
```
top_sellers = df.groupby('seller')['sellingprice'].sum().nlargest(5).reset_index()


top_sellers
seller	sellingprice
0	nissan infiniti lt	481774031.0
1	ford motor credit company llc	326062300.0
2	the hertz corporation	234745113.0
3	avis corporation	184363880.0
4	santander consumer	120513815.0

```

12) Top 5 Sellers by Total Selling Price'
```
plt.figure(figsize=(6, 4))
sns.barplot(data=top_sellers, x='sellingprice', y='seller', palette='viridis')
plt.title('Top 5 Sellers by Total Selling Price', fontsize=18, weight='bold', color='darkblue')
plt.xlabel('Total Sales ($)', fontsize=14, weight='bold', color='darkblue')
plt.ylabel('Seller', fontsize=14, weight='bold', color='darkblue')
plt.grid(axis='x', linestyle='--', alpha=0.7)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121225.png)

13) Average Selling Price by Body Type
```
avg_body_prices = df.groupby('body')['sellingprice'].mean().reset_index()
avg_body_prices = avg_body_prices.sort_values(by='sellingprice', ascending=False)
plt.figure(figsize=(15, 8), facecolor='lightgray')
sns.barplot(data=avg_body_prices, x='body', y='sellingprice', palette='RdYlBu')
plt.title('Average Selling Price by Body Type', fontsize=20, weight='bold', color='darkblue')
plt.xlabel('Body Type', fontsize=14, weight='bold', color='darkblue')
plt.ylabel('Average Selling Price ($)', fontsize=14, weight='bold', color='darkblue')
plt.xticks(rotation=90, ha='right', fontsize=12)
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121235.png)

## Multi variate analysis

1) Top Models by make
```
total_sales = df.groupby(['make', 'model']).agg({'sellingprice': 'sum'}).reset_index()
top_makes = total_sales.groupby('make')['sellingprice'].sum().nlargest(6).index
top_models = total_sales[total_sales['make'].isin(top_makes)]
top_models = top_models.loc[top_models.groupby('make')['sellingprice'].nlargest(3).reset_index(level=0, drop=True).index]
other_models = total_sales[total_sales['make'].isin(top_makes) & ~total_sales['model'].isin(top_models['model'])]

other_sales = other_models.groupby('make').agg({'sellingprice': 'sum'}).reset_index()
other_sales['model'] = 'Other'
combined_sales = pd.concat([top_models, other_sales], ignore_index=True)

plt.figure(figsize=(14, 12))
for i, make in enumerate(combined_sales['make'].unique(), start=1):
    plt.subplot(3, 2, i)
    make_data = combined_sales[combined_sales['make'] == make]
    sizes = make_data['sellingprice']
    labels = make_data['model']
    explode = [0.05 if label != 'Other' else 0 for label in labels]
    colors = plt.cm.get_cmap('Set1').colors[:len(sizes)]
    plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90, colors=colors, explode=explode, shadow=True)
    plt.title(f'Top Models for {make}', fontsize=14, fontweight='bold')
plt.tight_layout(pad=2)
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121246.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121253.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121301.png)

2) Make vs. Transmission vs. Selling Price by Condition
```
top_makes = df['make'].value_counts().index[:4]
df_filtered = df[df['make'].isin(top_makes)]

g = sns.catplot(
    x='transmission', y='sellingprice', col='make', data=df_filtered, kind='bar',
    col_wrap=2, height=4, aspect=1.2, hue='condition_group')

g.set_titles('{col_name}')
g.set_axis_labels('Transmission', 'Selling Price')
g.fig.suptitle('Make vs. Transmission vs. Selling Price by Condition', y=1.05)
g._legend.remove()
g.add_legend(title='Condition Group', loc='upper right')

plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121314.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121335.png)

3) Top 10 Makes vs. Transmission vs. Total Selling Price
```
top_makes = df.groupby('make')['sellingprice'].sum().nlargest(10).index
filtered_df = df[df['make'].isin(top_makes)]


plt.figure(figsize=(16, 10))
sns.barplot(data=filtered_df, y='make', x='sellingprice', hue='transmission', dodge=True)
plt.xticks(rotation=45)
plt.title('Top 10 Makes vs. Transmission vs. Total Selling Price')
plt.xlabel('Selling Price')
plt.ylabel('Make')
plt.legend(title='Transmission')
plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20122524.png)

4) Top 5 Car Soldout count
```
df['full_model'] = df['make'] + ' ' + df['model'] + ' ' + df['sale_year'].astype(str)
model_n = df.groupby(['full_model', 'condition']).size().reset_index(name='count')
top_models = model_n.groupby(['full_model'])['count'].sum().reset_index()
top_models = top_models.sort_values('count', ascending=False).head(5)
plt.figure(figsize=(20, 8))
sns.barplot(data=model_n[model_n['full_model'].isin(top_models['full_model'])], x='full_model', y='count', hue='condition')
plt.xlabel('Model Name', fontsize=15)
plt.ylabel('Number Of Cars', fontsize=15)
plt.title('Top 5 Car Soldout count', fontsize=26)
plt.xticks(rotation=90, fontsize=14)
plt.yticks(fontsize=14)
plt.legend(title='Condition', fontsize=12)
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121404.png)

5) Year vs Condition vs Selling Price
```
fig = plt.figure(figsize=(12, 8))
ax = fig.add_subplot(111, projection='3d')
sc = ax.scatter(df['year'], df['condition'], df['sellingprice'],

                c=df['sellingprice'], cmap='viridis', s=50, alpha=0.7)

ax.set_xlabel('Year', fontsize=14)
ax.set_ylabel('Condition (1-5)', fontsize=14)
ax.set_zlabel('Selling Price', fontsize=14)
ax.set_title('3D Plot: Year vs Condition vs Selling Price', fontsize=16)
cbar = plt.colorbar(sc, ax=ax, shrink=0.6)
cbar.set_label('Selling Price')

plt.tight_layout()
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121909.png)

6) Condition Group vs. Odometer vs. Selling Price
```
fig = plt.figure(figsize=(10, 7))
ax = fig.add_subplot(111, projection='3d')
scatter = ax.scatter(df['condition'], df['odometer'], df['sellingprice'],

                     c=df['sellingprice'], cmap='coolwarm', s=50)

ax.set_xlabel('Condition Group')
ax.set_ylabel('Odometer')
ax.set_zlabel('Selling Price')
ax.set_title('Condition Group vs. Odometer vs. Selling Price')
cbar = fig.colorbar(scatter, ax=ax, pad=0.1)
cbar.set_label('Selling Price')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121920.png)

7) Year vs. Odometer vs. Selling Price
```
 fig = plt.figure(figsize=(10, 7))
ax = fig.add_subplot(111, projection='3d')
sc = ax.scatter(df['year'], df['odometer'], df['sellingprice'],

                c=df['sellingprice'], cmap='viridis', s=50)

ax.set_xlabel('Year')
ax.set_ylabel('Odometer')
ax.set_zlabel('Selling Price')
ax.set_title('Year vs. Odometer vs. Selling Price')
cbar = plt.colorbar(sc)
cbar.set_label('Selling Price')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20121957.png)

8) Correlation Heatmap of Key Variables
```
plt.figure(figsize=(10, 6))
correlation_matrix = df[['condition', 'odometer', 'mmr', 'sellingprice']].corr()
plt.show()
<Figure size 1000x600 with 0 Axes>
```
```
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5)
plt.title('Correlation Heatmap of Key Variables')
plt.show()
```
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/4e97d75bf6bb9405a255f1309f0aa9e02c3550a7/Screenshot%202024-11-12%20122006.png)

## Measures in Power BI
I successfully imported data from my device to Power BI. Following the import, I developed several measures to enhance data analysis and visualization capabilities. These measures were designed to provide key insights and facilitate informed decision-making based on the underlying data.
The integration process involved establishing relationships between various data tables to ensure accurate data modeling. I utilized DAX (Data Analysis Expressions) to create custom calculations, enabling dynamic reporting and in-depth analysis.The resulting Power BI dashboards offer a comprehensive view of the data, empowering with actionable insights and fostering a data-driven culture within the organization.

```
Average Odometer Reading = AVERAGE(cleaned_car_prices[odometer])
Average Selling price = AVERAGE(cleaned_car_prices[sellingprice])
Total Revenue = SUM(cleaned_car_prices[sellingprice])
Total Sales = COUNTROWS('cleaned_car_prices')
```

## Dashboard
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/b466535495165eff8a8186b4556eef0fb4f0220d/Screenshot%202024-11-12%20130433.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/b466535495165eff8a8186b4556eef0fb4f0220d/Screenshot%202024-11-12%20130442.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/bc683abfff6f2f4b1f5612ce3d42aebe965299f1/Screenshot%202024-11-13%20134352.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/b466535495165eff8a8186b4556eef0fb4f0220d/Screenshot%202024-11-12%20130501.png)
![Alt text](https://github.com/Slndora/Vehicle-Sales/blob/b466535495165eff8a8186b4556eef0fb4f0220d/Screenshot%202024-11-12%20130509.png)

## Acknowledgments
This project uses the vehicle sales dataset provided by MIT from kaggle. We thank them for their valuable contribution.





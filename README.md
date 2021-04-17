### Importing Data](https://academy.dqlab.id/main/livecode/166/322/1513)

```plantuml
import pandas as pd
import numpy as np
import io 
import pandas_profiling 
retail_raw = pd.read_csv('https://dqlab-dataset.s3-ap-southeast-1.amazonaws.com/retail_raw_reduced_data_quality.csv')
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Inspeksi tipe data](https://academy.dqlab.id/main/livecode/166/322/1514)

```plantuml
#Cetak tipe data di setiap kolom retail_raw
print(retail_raw.dtypes)

```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----
### Descriptive Statistics - Part 1](https://academy.dqlab.id/main/livecode/166/322/1515)
 ```plantuml
# Kolom city
length_city = len(retail_raw['city'])
print('Length kolom city:', length_city)

# Tugas Praktek: Kolom product_id
length_product_id = len(retail_raw['product_id'])
print('Length kolom product_id:', length_product_id)

```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----
### Descriptive Statistics - Part 2](https://academy.dqlab.id/main/livecode/166/322/1517)
 ```plantuml
# Count kolom city
count_city = retail_raw['city'].count()
print('Count kolom count_city:', count_city)

# Tugas praktek: count kolom product_id
count_product_id = retail_raw['product_id'].count()
print('Count kolom product_id:', count_product_id)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Descriptive Statistics - Part 3](https://academy.dqlab.id/main/livecode/166/322/1519)
 ```plantuml
# Missing value pada kolom city
number_of_missing_values_city = length_city - count_city
float_of_missing_values_city = float(number_of_missing_values_city/length_city)
pct_of_missing_values_city = '{0:.1f}%'.format(float_of_missing_values_city * 100)
print('Persentase missing value kolom city:', pct_of_missing_values_city)

# Tugas praktek: Missing value pada kolom product_id
number_of_missing_values_product_id = length_product_id - count_product_id
float_of_missing_values_product_id = float(number_of_missing_values_product_id/length_product_id)
pct_of_missing_values_product_id = '{0:.1f}%'.format(float_of_missing_values_product_id * 100)
print('Persentase missing value kolom product_id:', pct_of_missing_values_product_id)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Descriptive Statistics - Part 4](https://academy.dqlab.id/main/livecode/166/322/1521)
 ```plantuml
#Deskriptif statistics kolom quantity
print('Kolom quantity')
print('Minimum value: ', retail_raw['quantity'].min())
print('Maximum value: ', retail_raw['quantity'].max())
print('Mean value: ', retail_raw['quantity'].mean())
print('Mode value: ', retail_raw['quantity'].mode())
print('Median value: ', retail_raw['quantity'].median())
print('Standard Deviation value: ', retail_raw['quantity'].std())

#Tugas praktek: Deskriptif statistics kolom item_price
print('')
print('Kolom item_price')
print('Minimum value: ', retail_raw['item_price'].min())
print('Maximum value: ', retail_raw['item_price'].max())
print('Mean value: ', retail_raw['item_price'].mean())
print('Median value: ', retail_raw['item_price'].median())
print('Standard Deviation value: ', retail_raw['item_price'].std())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Descriptive Statistics - Part 5](https://academy.dqlab.id/main/livecode/166/322/1523)
```plantuml 
# Quantile statistics kolom quantity
print('Kolom quantity:')
print(retail_raw['quantity'].quantile([0.25, 0.5, 0.75]))

# Tugas praktek: Quantile statistics kolom item_price
print('')
print('Kolom item_price:')
print(retail_raw['item_price'].quantile([0.25, 0.5, 0.75]))
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Descriptive Statistics - Part 6](https://academy.dqlab.id/main/livecode/166/322/1526)
 ```plantuml
print('Korelasi quantity dengan item_price')
print(retail_raw[['quantity', 'item_price']].corr())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Missing Data](https://academy.dqlab.id/main/livecode/166/323/1529)
 ```plantuml
# Check kolom yang memiliki missing data
print('Check kolom yang memiliki missing data:')
print(retail_raw.isnull().any())

# Filling the missing value (imputasi)
print('\nFilling the missing value (imputasi):')
print(retail_raw['quantity'].fillna(retail_raw['quantity'].mean()))

# Drop missing value
print('\nDrop missing value:')
print(retail_raw['quantity'].dropna())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Tugas Praktek](https://academy.dqlab.id/main/livecode/166/323/1530)
```plantuml 
print(retail_raw['item_price'].fillna(retail_raw['item_price'].mean()))
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Outliers](https://academy.dqlab.id/main/livecode/166/323/1534)
 ```plantuml
# Q1, Q3, dan IQR
Q1 = retail_raw['quantity'].quantile(0.25)
Q3 = retail_raw['quantity'].quantile(0.75)
IQR = Q3 - Q1

# Check ukuran (baris dan kolom) sebelum data yang outliers dibuang
print('Shape awal: ', retail_raw.shape)

# Removing outliers
retail_raw = retail_raw[~((retail_raw['quantity'] < (Q1 - 1.5 * IQR)) | (retail_raw['quantity'] > (Q3 + 1.5 * IQR)))]

# Check ukuran (baris dan kolom) setelah data yang outliers dibuang
print('Shape akhir: ', retail_raw.shape)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Tugas Praktek](https://academy.dqlab.id/main/livecode/166/323/1535)
```plantuml 
#Q1, Q3, dan IQR
Q1 = retail_raw['item_price'].quantile(0.25)
Q3 = retail_raw['item_price'].quantile(0.75)
IQR = Q3 - Q1

#Check ukuran (baris dan kolom) sebelum data yang outliers dibuang
print('Shape awal: ', retail_raw.shape)

#Removing outliers
retail_raw = retail_raw[~((retail_raw['item_price'] < (Q1 - 1.5 * IQR)) | (retail_raw['item_price'] > (Q3 + 1.5 * IQR)))]

#Check ukuran (baris dan kolom) setelah data yang outliers dibuang
print('Shape akhir: ', retail_raw.shape)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Tugas Praktek](https://academy.dqlab.id/main/livecode/166/323/1537)
```plantuml 
# Check ukuran (baris dan kolom) sebelum data duplikasi dibuang
print('Shape awal: ', retail_raw.shape)

# Buang data yang terduplikasi
retail_raw.drop_duplicates(inplace=True)

# Check ukuran (baris dan kolom) setelah data duplikasi dibuang
print('Shape akhir: ', retail_raw.shape)
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Case Studi: Data Profiling](https://academy.dqlab.id/main/livecode/166/324/1532)
```plantuml 
#Baca dataset uncleaned_raw.csv
uncleaned_raw = pd.read_csv('https://dqlab-dataset.s3-ap-southeast-1.amazonaws.com/uncleaned_raw.csv')

#inspeksi dataframe uncleaned_raw
print('Lima data teratas:')
print(uncleaned_raw.head())

#Check kolom yang mengandung missing value
print('\nKolom dengan missing value:')
print(uncleaned_raw.isnull().any())

#Persentase missing value
length_qty = len(uncleaned_raw['Quantity'])
count_qty = uncleaned_raw['Quantity'].count()

#mengurangi length dengan count
number_of_missing_values_qty = length_qty - count_qty

#mengubah ke bentuk float
float_of_missing_values_qty = float(number_of_missing_values_qty / length_qty)

#mengubah ke dalam bentuk persen
pct_of_missing_values_qty = '{0:.1f}%'.format(float_of_missing_values_qty*100)

#print hasil percent dari missing value
print('Persentase missing value kolom Quantity:', pct_of_missing_values_qty)

#Mengisi missing value tersebut dengan mean dari kolom tersebut
uncleaned_raw['Quantity'] = uncleaned_raw['Quantity'].fillna(uncleaned_raw['Quantity'].mean())
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Case Study: Data Cleansing - Part 1](https://academy.dqlab.id/main/livecode/166/324/2602)
```plantuml 
import matplotlib.pyplot as plt

#Mengetahui kolom yang memiliki outliers!
uncleaned_raw.boxplot()
plt.show()
```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

### Case Study: Data Cleansing - Part 2](https://academy.dqlab.id/main/livecode/166/324/2603)
```plantuml 
#Check IQR
Q1 = uncleaned_raw['UnitPrice'].quantile(0.25)
Q3 = uncleaned_raw['UnitPrice'].quantile(0.75)
IQR = Q3 - Q1

#removing outliers
uncleaned_raw = uncleaned_raw[~((uncleaned_raw[['UnitPrice']] < (Q1 - 1.5 * IQR)) | (uncleaned_raw[['UnitPrice']] > (Q3 + 1.5 * IQR)))]

#check for duplication
print(uncleaned_raw.duplicated(subset=None))

#remove duplication
uncleaned_raw = uncleaned_raw.drop_duplicates()

```
<details>
<summary markdown="span">Output :</summary>
Aksara, Usia: 25, Pendapatan 8500000</br>
Senja, Usia: 28, Pendapatan 12500000	
</details>
</br>
<a href="https://academy.dqlab.id/main/livecode/161/301/1355">Link materi : academy.dqlab.id/main/livecode/161/301/1355</a>

----

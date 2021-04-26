### Importing Data 

```plantuml
import pandas as pd
import numpy as np
import io 
import pandas_profiling 
retail_raw = pd.read_csv('https://dqlab-dataset.s3-ap-southeast-1.amazonaws.com/retail_raw_reduced_data_quality.csv')
```

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1513">Link materi : academy.dqlab.id/main/livecode/166/322/1513</a>

----

### Inspeksi tipe data 

```plantuml
#Cetak tipe data di setiap kolom retail_raw
print(retail_raw.dtypes)

```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_1.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1514">Link materi : academy.dqlab.id/main/livecode/166/322/1514</a>

----

### Descriptive Statistics - Part 1 

 ```plantuml
#Kolom city
length_city = len(retail_raw['city'])
print('Length kolom city:', length_city)
#Tugas Praktek: Kolom product_id
length_product_id = len(retail_raw['product_id'])
print('Length kolom product_id:', length_product_id)
```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_2.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1515">Link materi : academy.dqlab.id/main/livecode/166/322/1515</a>

----

### Descriptive Statistics - Part 2 
<p align="justify">Fungsi count menghitung jumlah pengamatan non-NA / non-null dalam suatu series / column. Fungsi len akan hanya menghitung elemen dari kolom yang mempunyai nilai (exclude missing value).</p>
 
 ```plantuml
# Count kolom city
count_city = retail_raw['city'].count()
print('Count kolom count_city:', count_city)

# Tugas praktek: count kolom product_id
count_product_id = retail_raw['product_id'].count()
print('Count kolom product_id:', count_product_id)
```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_3.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1517">Link materi : academy.dqlab.id/main/livecode/166/322/1517</a>

----

### Descriptive Statistics - Part 3 
<p align="justify">Dengan Length dan Count, sekarang dapat menghitung jumlah missing-value. Jumlah nilai yang hilang adalah perbedaan antara Length dan Count.</p>
 
 ```plantuml
#Missing value pada kolom city
number_of_missing_values_city = length_city - count_city
float_of_missing_values_city = float(number_of_missing_values_city/length_city)
pct_of_missing_values_city = '{0:.1f}%'.format(float_of_missing_values_city * 100)
print('Persentase missing value kolom city:', pct_of_missing_values_city)
#Tugas praktek: Missing value pada kolom product_id
number_of_missing_values_product_id = length_product_id - count_product_id
float_of_missing_values_product_id = float(number_of_missing_values_product_id/length_product_id)
pct_of_missing_values_product_id = '{0:.1f}%'.format(float_of_missing_values_product_id * 100)
print('Persentase missing value kolom product_id:', pct_of_missing_values_product_id)
```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_4.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1519">Link materi : academy.dqlab.id/main/livecode/166/322/1519</a>

----

### Descriptive Statistics - Part 4 
 
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

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_5.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1521">Link materi : academy.dqlab.id/main/livecode/166/322/1521</a>

----

### Descriptive Statistics - Part 5 

```plantuml 
# Quantile statistics kolom quantity
print('Kolom quantity:')
print(retail_raw['quantity'].quantile([0.25, 0.5, 0.75]))
# Tugas praktek: Quantile statistics kolom item_price
print('')
print('Kolom item_price:')
print(retail_raw['item_price'].quantile([0.25, 0.5, 0.75]))
```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_6.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1523">Link materi : academy.dqlab.id/main/livecode/166/322/1523</a>

----

### Descriptive Statistics - Part 6 
<p align="justify">Korelasi adalah cara yang tepat untuk menemukan hubungan antara variabel numerik. Koefisien korelasi berkisar antara -1 hingga 1. Korelasi 1 adalah korelasi positif total, korelasi -1 adalah korelasi negatif total dan korelasi 0 adalah korelasi non-linear.</p>

```plantuml
print('Korelasi quantity dengan item_price')
print(retail_raw[['quantity', 'item_price']].corr())
```

|Output : |
| :--     | 
|<img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_7.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/322/1526">Link materi : academy.dqlab.id/main/livecode/166/322/1526</a>

----

### Missing Data 

```plantuml
#Check kolom yang memiliki missing data
print('Check kolom yang memiliki missing data:')
print(retail_raw.isnull().any())

#Filling the missing value (imputasi)
print('\nFilling the missing value (imputasi):')
print(retail_raw['quantity'].fillna(retail_raw['quantity'].mean()))

#Drop missing value
print('\nDrop missing value:')
print(retail_raw['quantity'].dropna())
```

|Output : |
| :--     | 
| <img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/download.png">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/323/1529">Link materi : academy.dqlab.id/main/livecode/166/323/1529</a>

----

### Tugas Praktek 

```plantuml 
print(retail_raw['item_price'].fillna(retail_raw['item_price'].mean()))
```

|Output : |
| :--     | 
|<img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/download (1).png">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/323/1530">Link materi : academy.dqlab.id/main/livecode/166/323/1530</a>

----

### Outliers 

```plantuml
#Q1, Q3, dan IQR
Q1 = retail_raw['quantity'].quantile(0.25)
Q3 = retail_raw['quantity'].quantile(0.75)
IQR = Q3 - Q1

#Check ukuran (baris dan kolom) sebelum data yang outliers dibuang
print('Shape awal: ', retail_raw.shape)

#Removing outliers
retail_raw = retail_raw[~((retail_raw['quantity'] < (Q1 - 1.5 * IQR)) | (retail_raw['quantity'] > (Q3 + 1.5 * IQR)))]

#Check ukuran (baris dan kolom) setelah data yang outliers dibuang
print('Shape akhir: ', retail_raw.shape)
```

|Output : |
| :--     | 
|<img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/Screenshot_8.jpg">|

</br>
<a href="https://academy.dqlab.id/main/livecode/166/323/1534">Link materi : academy.dqlab.id/main/livecode/166/323/1534</a>

----

### Tugas Praktek 

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

</br>
<a href="https://academy.dqlab.id/main/livecode/166/323/1535">Link materi : academy.dqlab.id/main/livecode/166/323/1535</a>

----

### Tugas Praktek 

```plantuml 
#Check ukuran (baris dan kolom) sebelum data duplikasi dibuang
print('Shape awal: ', retail_raw.shape)

#Buang data yang terduplikasi
retail_raw.drop_duplicates(inplace=True)

#Check ukuran (baris dan kolom) setelah data duplikasi dibuang
print('Shape akhir: ', retail_raw.shape)
```

</br>
<a href="https://academy.dqlab.id/main/livecode/166/323/1537">Link materi : academy.dqlab.id/main/livecode/166/323/1537</a>

----

### Case Studi: Data Profiling 

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

</br>
<a href="https://academy.dqlab.id/main/livecode/166/324/1532">Link materi : academy.dqlab.id/main/livecode/166/324/1532</a>

----

### Case Study: Data Cleansing - Part 1 

```plantuml 
import matplotlib.pyplot as plt

#Mengetahui kolom yang memiliki outliers!
uncleaned_raw.boxplot()
plt.show()
```

</br>
<a href="https://academy.dqlab.id/main/livecode/166/324/2602">Link materi : academy.dqlab.id/main/livecode/166/324/2602</a>

----

### Case Study: Data Cleansing - Part 2 

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

</br>
<a href="https://academy.dqlab.id/main/livecode/166/324/2603">Link materi : academy.dqlab.id/main/livecode/166/324/2603</a>

----


<p align="justify">Yuk belajar data science bersama DQLab dengan daftarkan diri kamu dengan signup di dqlab.id. Dapatkan potongan 10% dengan menggunakan link referral ini  ! <a href="https://dqlab.id/signup?referralCode=YENN3520"> Klik Gabung </a> </p></br>

<p align="center"><b>E-Sertifikat </b></br><img src="https://github.com/yenysyafitry/DQLab-Data-Quality-with-Python-for-Beginner/blob/main/e-sertifikat.jpg"></p>

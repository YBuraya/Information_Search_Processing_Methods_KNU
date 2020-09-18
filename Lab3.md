# Лабораторна робота №3

**1. За допомогою download.file() завантажте любий excel файл з порталу http://data.gov.ua та зчитайте його (xls, xlsx – бінарні формати, тому встановить mode = “wb”. Виведіть перші 6 строк отриманого фрейму даних.**
```r
download.file("https://data.gov.ua/dataset/f9f0c32e-1cb0-44a6-a13f-534d385b95c0/resource/b526b4af-fe7f-427b-b94a-b58ba3ba4390/download/134-zaborgovanist-iz-viplati-zarobitnoyi-plati-do-vidpovidnogo-misiatsia-mln-grn.xlsx", "lab1_data1.xlsx", "auto", TRUE, mode = "wb")
library("readxl")
lab1_data1 <- read_xlsx("lab1_data1.xlsx", sheet = 2)
head(data, n = 6)
```
```
# A tibble: 6 x 3
  code  period  data              
  <chr> <chr>   <chr>             
1 	Коди  Дата    дані              
2 	01    2019-01 2614.3
3 	01    2019-02 2446.8
4 	01    2019-03 2463.3
5 	01    2019-04 2615.4            
6	 01    2019-05 2718.3    
```

**2. За допомогою download.file() завантажте файл getdata_data_ss06hid.csv за посиланням https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv та завантажте дані в R. Code book, що пояснює значення змінних знаходиться за посиланням https://www.dropbox.com/s/dijv0rlwo4mryv5/PUMSDataDict06.pdf?dl=0 Необхідно знайти, скільки property мають value $1000000+**

```r
download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv", "lab1_data2.csv", "auto", TRUE, mode = "wb")
lab1_data2 <- read.csv("lab1_data2.csv")
sum(lab1_data2$VAL == 24, na.rm = TRUE)
```
```
[1] 53
```

**3. Зчитайте xml файл за посиланням http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml Скільки ресторанів мають zipcode 21231?**
```r
library(XML)
download.file("http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml", "lab1_data3.xml", "auto", TRUE, mode = "wb")
lab1_data3 <- xmlRoot(xmlTreeParse("lab1_data3.xml", useInternalNodes = TRUE))
sum(xpathSApply(lab1_data3, "//zipcode", xmlValue) == 21231)
```
```
[1] 127
```

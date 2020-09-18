# Лабораторна робота №2

**1. Створить список list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2)). Для цього списку знайдіть sum за допомогою lapply.**
``` r
list1 <- list(observationA = c(1:5, 7:3), observationB = matrix(1:6, nrow=2))
lapply(list1, sum)
```
```
$observationA
[1] 40

$observationB
[1] 21
```

**2. Для кожного елементу списку list1 знайдіть максимальне та мінімальне значення (range) за допомогою lapply та sapply.**
``` r
lapply(list1, range)
sapply(list1, range)
```
```
> lapply(list1, range)
$observationA
[1] 1 7

$observationB
[1] 1 6

> sapply(list1, range)
     observationA observationB
[1,]            1            1
[2,]            7            6
```

**3.Для вбудованого набору даних InsectSprays знайти середнє count для кожного spray.**
``` r
count = InsectSprays$count
spray = InsectSprays$spray

tapply(count, spray, mean, na.rm = TRUE)
```
```
        A         B         C         D         E         F 
14.500000 15.333333  2.083333  4.916667  3.500000 16.666667 
```

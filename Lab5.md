# Лабораторна робота № 5
## 1. Написати функцію pmean, яка обчислює середнє значення (mean) забруднення сульфатами або нітратами серед заданого переліка моніторів.
# Функція приймає три аргументи: *«directory», «pollutant», «id»*. *Directory* – папка, в якій розміщені дані, *pollutant* – вид забруднення, *id* – перелік моніторів. 
#Аргумент *id* має значення за замовчуванням 1:332. Функція повинна ігнорувати **NA** значення. 


```r
pmean <- function(pollutant, id = 1:332, directory="D:/Дз/R STUDIO/specdata") {
  #Створюємо список для обраного pollutant 
  pmean1 = lapply(id, function(y) read.csv(paste(directory, "/", formatC(y,width = 3, flag = "0"), ".csv", sep=""))[[pollutant]])
  return (mean(unlist(pmean1), na.rm = TRUE))
}

pmean("sulfate", 1)
[1] 3.880701
pmean("nitrate", 100:200)
[1] 1.507905
```

### 2.Написати функцію complete, яка виводить кількість повних спостережень для кожного файлу. 
# Функція приймає два аргументи: *«directory»* та *«id»* та повертає **data frame**, в якому перший стовпчик – ім’я файлу, а другий – кількість повних спостережень. 

```r
complete <- function(id= 1:332, directory="D:/Дз/R STUDIO/specdata"){
  nobs<-numeric()
  for (i in id) { 
    comp <- read.csv(paste(directory, "/", formatC(i, width = 3, flag = "0"),  ".csv", sep = ""))
    nobs <- c(nobs,sum(complete.cases(comp)))
  }
  return(data.frame(id, nobs))
}
complete (c(10,20,30,40,50))
  id nobs
1 10  148
2 20  124
3 30  932
4 40   21
5 50  459
complete (95:100)
   id nobs
1  95   81
2  96  873
3  97  243
4  98  736
5  99  479
6 100  104
```

### 3.Написати функцію corr, яка приймає два аргументи: directory (папка, де знаходяться файли спостережень) та threshold (порогове значення, за замовчуванням дорівнює 0) та обчислює кореляцію між сульфатами та нітратами для моніторів, кількість повних спостережень для яких більше порогового значення. 
# Функція повинна повернути вектор значень кореляцій. Якщо ні один монітор не перевищує порогового значення, функція повинна повернути numeric вектор довжиною 0. Для обчислення кореляції між сульфатами та нітратами використовуйте вбудовану функцію **«cor»** з параметрами за замовчуванням.

```r
corr <- function(threshold = 0, directory="D:/Дз/R STUDIO/specdata") {
  cor3 <- NULL
  for (i in 1:332) {
    cor1<- read.csv(paste(directory, "/", formatC(i, width = 3, flag = "0"),".csv", sep = ""))
    cor2 <- cor1[complete.cases(cor1), ]
    if (nrow(cor2) > threshold)
      cor3 <- c(cor3, cor(cor2[,"sulfate"], cor2[, "nitrate"]))
  }
  if(length(cor3) > 0)
    return (cor3)
  return (as.numeric(c()))
}
cr <- corr(250)
head(cr); summary(cr)

[1] -0.01895754 -0.04389737 -0.06815956 -0.07588814 -0.08684194  0.76312884
    Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
-0.21057 -0.04188  0.10455  0.13587  0.26844  0.76313 
```


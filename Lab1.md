#Лабораторна робота № 1 
# 1. Створити змінні базових (atomic) типів. Базові типи: character, numeric, integer, complex, logical.

x1 <- TRUE #logical
class(x1)
x2 <- -25.3 #numeric
class(x2)
x3 <- 5L # integer (L вказує що це ціле число)
class(x3)
x4 <- 7+8i #complex
class(x4)
x5 <- "Have a good day!" #character
class(x5)

#2. Створити вектори, які: містить послідовність з 5 до 75; містить числа 3.14,2.71, 0, 13; 100 значень TRUE.

x6 <- 5:75 #містить послідовність з 5 до 75
x6

x7 <- c(3.14,2.71, 0, 13) #містить числа 3.14,2.71, 0, 13
x7

x8<- rep(TRUE, 100) #100 значень TRUE
x8

#3. Створити наступну матрицю за допомогою matrix, та за допомогою cbind або rbind
#0.5 1.3 3.5
# 3.9 131 2.8
# 0 2.2 4.6
# 2 7 5.1

x9<-matrix(data = c(0.5, 1.3, 3.5,
                    3.9, 131, 2.8,
                    0, 2.2, 4.6,
                    2, 7, 5.1), nrow = 4, ncol = 3, byrow = TRUE)
x9


x10<-cbind(c(0.5,3.9, 0, 2),  c(1.3, 131, 2.2, 7),   c(3.5,2.8,4.6, 5.1))
x10


x11<-rbind(c(0.5, 1.3, 3.5),
             c(3.9, 131, 2.8),
             c(0, 2.2, 4.6),
             c(2, 7, 5.1))
x11

#4. Створити довільний список (list), в який включити всі базові типи.

x12 <- list(TRUE, -25.3, 5L, 7+8i, "Have a good day!")
print(x12)

#5. Створити фактор з трьома рівнями «baby», «child», «adult»

x13 <- factor(levels=c("baby", "child", "adult"),ordered=TRUE)
x13

#6. Знайти індекс першого значення NA в векторі 1, 2, 3, 4, NA, 6, 7, NA, 9, NA,11. Знайти кількість значень NA

a1 <- c(1, 2, 3, 4, NA, 6, 7, NA, 9, NA, 11)
x14<-match(NA,a1) #індекс першого значення NA
x14

x14.1<-length(which(is.na(a1))) #кількість значень NA
x14.1

#7. Створити довільний data frame та вивести в консоль.

meal <- c('borsch', 'pizza', 'pasta', 'soup', 'pie')
price <- c(110, 150, 120, 80, 130)
currency<-rep("UAH",5)
menu <- data.frame(meal, price, currency)
menu

#8. Змінити імена стовпців цього data frame.

colnames(menu) <- c('discount_meal','price with discount','currency')
print(menu)




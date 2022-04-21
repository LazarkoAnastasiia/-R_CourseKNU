#Лабораторна робота № 3
#В лабораторній роботі необхідно написати наступні функції на мові R та вивести
#результат роботи цих функцій на довільних даних:
#1. Функція add2(x, y), яка повертає суму двох чисел.

add2<-function(x, y){
   result <-x+y
   return(result)}

add2(123,456)

#2. Функція above(x, n=10), яка приймає вектор та число n, та повертає всі
#елементі вектору, які більше n. По замовчуванню n = 10.

above<-function(x,n=10){
  result1<-x[x>n]
  return(result1)}
t<-c(6,7,25,37,72,3)

above(t,15)

#3. Функція my_ifelse(x, exp, n), яка приймає вектор x, порівнює всі його
#елементи за допомогою exp з n, та повертає елементи вектору, які
#відповідають умові expression. Наприклад, my_ifelse(x, “>”, 0) повертає всі
#елементи x, які більші 0. Exp може дорівнювати “<”, “>”, “<=”, “>=”, “==”.
#Якщо exp не співпадає ні з одним з цих виразів, повертається вектор x

my_ifelse <- function(x, exp, n){
  if (exp == "<") { x[x<n] } 
  else if(exp == "<="){x[x<=n]} 
  else if (exp == ">"){x[x>n]} 
  else if (exp == ">="){ x[x>=n]} 
  else if (exp == "=="){x[x==n]}
  else {x}}
x <- c(125, 150, 170, 180, 300, 700, 850)
my_ifelse(x, "<", 200)

my_ifelse(x, "<=", 170)

my_ifelse(x, ">", 180)

my_ifelse(x, ">=", 300)

my_ifelse(x, "==", 850)

#4. Функція columnmean(x, removeNA), яка розраховує середнє значення
#(mean) по кожному стовпцю матриці, або data frame. Логічний параметр
#removeNA вказує, чи видаляти NA значення. По замовчуванню він
#дорівнює TRUE.

columnmean <- function(y, removeNA=TRUE){
  res<-vector()
  for (col in 1:ncol(y)){
    res[col]<-(mean(y[,col], na.rm=removeNA))
  }
  return(res)
}  
y <- matrix(c(8,9,12, NA, 5, 6, NA, NA, 8), nrow=3, ncol=3, byrow=TRUE)
columnmean(y)

columnmean (y, FALSE)






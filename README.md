# Assignment-7
S3 Vs S4
 # Create an S3 dataset
> s3_dataset <- list(
+   name = c("Alice", "Bob", "Charlie"),
+   age = c(28, 35, 30),
+   grade = c("A", "B", "C")
+ )
> 
> # Assign the S3 class
> class(s3_dataset) <- "myS3Class"
> 
> # Define a generic function for S3
> summary.myS3Class <- function(object) {
+   cat("Summary for myS3Class object:\n")
+   print(object)
+ }
> 
> # Use the generic function
> summary(s3_dataset)
Summary for myS3Class object:
$name
[1] "Alice"   "Bob"     "Charlie"

$age
[1] 28 35 30

$grade
[1] "A" "B" "C"

attr(,"class")
[1] "myS3Class"
> # Install and load the methods package if not already installed
> # install.packages("methods")
> # library(methods)
> 
> # Define an S4 class for a Student dataset
> setClass(
+   "StudentDataset",
+   slots = list(
+     names = "character",
+     ages = "numeric",
+     grades = "character"
+   )
+ )
> 
> # Create an S4 object
> s4_dataset <- new(
+   "StudentDataset",
+   names = c("Alice", "Bob", "Charlie"),
+   ages = c(28, 35, 30),
+   grades = c("A", "B", "C")
+ )
> 
> # Define a method for the S4 class
> setMethod("summary", "StudentDataset", function(object) {
+   cat("Summary for StudentDataset object:\n")
+   print(paste("Names:", paste(object@names, collapse = ", ")))
+   print(paste("Ages:", paste(object@ages, collapse = ", ")))
+   print(paste("Grades:", paste(object@grades, collapse = ", ")))
+ })
> 
> # Use the method
> summary(s4_dataset)
Summary for StudentDataset object:
[1] "Names: Alice, Bob, Charlie"
[1] "Ages: 28, 35, 30"
[1] "Grades: A, B, C"
> 
Example 1: S3 class for a person
# Define an S3 class for a Person
> Person <- function(name, age, gender) {
+   person <- list(name = name, age = age, gender = gender)
+   class(person) <- "Person"
+   return(person)
+ }
> 
> # Create an S3 object of class Person
> person1 <- Person(name = "Alice", age = 30, gender = "Female")
> 
> # Print the S3 object
> print(person1)
$name
[1] "Alice"

$age
[1] 30

$gender
[1] "Female"

attr(,"class")
[1] "Person"
Example 2: S3 class for a vehicle
# Define an S3 class for a Vehicle
> Vehicle <- function(make, model, year) {
+   vehicle <- list(make = make, model = model, year = year)
+   class(vehicle) <- "Vehicle"
+   return(vehicle)
+ }
> 
> # Create an S3 object of class Vehicle
> car1 <- Vehicle(make = "Toyota", model = "Camry", year = 2022)
> 
> # Print the S3 object
> print(car1)
$make
[1] "Toyota"

$model
[1] "Camry"

$year
[1] 2022

attr(,"class")
[1] "Vehicle"
> 
Example 1: S4 class for a Rectangle
>  # Install and load the methods package if not already installed
> # install.packages("methods")
> # library(methods)
> 
> # Define an S4 class for a Rectangle
> setClass(
+   "Rectangle",
+   slots = c(width = "numeric", height = "numeric"),
+   prototype = list(width = 0, height = 0)
+ )
> 
> # Create an S4 object of class Rectangle
> rectangle1 <- new("Rectangle", width = 5, height = 8)
> 
> # Print the S4 object
> print(rectangle1)
An object of class "Rectangle"
Slot "width":
[1] 5

Slot "height":
[1] 8
Example 2: S4 class for a Book
 # Install and load the methods package if not already installed
> # install.packages("methods")
> # library(methods)
> 
> # Define an S4 class for a Book
> setClass(
+   "Book",
+   slots = c(title = "character", author = "character", pages = "numeric"),
+   prototype = list(title = "", author = "", pages = 0)
+ )
> 
> # Create an S4 object of class Book
> book1 <- new("Book", title = "The Great Gatsby", author = "F. Scott Fitzgerald", pages = 180)
> 
> # Print the S4 object
> print(book1)
An object of class "Book"
Slot "title":
[1] "The Great Gatsby"

Slot "author":
[1] "F. Scott Fitzgerald"

Slot "pages":
[1] 180

> 

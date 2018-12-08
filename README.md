---
title: "INFO 201 Cheat Sheet"
author: "Anhad Dhillon"
date: "December 7, 2018"
output: html_document
---
## 1. Command Line
* Display path of current working directory
```
$ pwd
```
* Change directory to <directory>
```
$ cd <directory>
```
* Navigate to parent directory
```
$ cd ...
```
* List directory contents
```
$ ls
```
* Create new directory named "directory"
```
$ mkdir <directory>
```
* Delete file
```
$ rm <file>
```
## 2. GitHub
* Create a local repository from scratch
```
$ git init [project name]
```
* Download an existing repository
```
$ git clone my_url
```
* List new or modified files not yet committed
```
$ git status
```
* Stage the file ready for commit
```
$ git add [file]
```
* Commit all staged files to versioned history
```
$ git commit -m "commit message"
```
* Fetch the latest changes from origin and merge
```
$ git pull
```
* Push local changes to the origin
```
$ git push
```
## 3. R basics
* Download and install a package from CRAN
```
install.packages('dplyr')
```
* Load the package into the session, making all its functions available to use
```
library(dplyr)
```
* Find the current working directory
```
getwd()
```
* Change the current working directory
```
setwd(":C//file/path")
```
### 4. Built-in R functions

-------------------

| Function Name  | Description                                                   | Example                                            | 
|--------------- |---------------------------------------------------------------|----------------------------------------------------|
| sum(a,b,...)   | Calculates the sum of all input values                        | sum(1,5) returns 6                                 |
| round(x,digits)| Rounds the first argument to the given number of digits       | round(3.1415, 3) returns 3.142                     | 
| toupper(str)   | Returns the characters in uppercase                           | toupper("hi there") returns "HI THERE"             | 
| paste(a,b,...) | Concatenate (combine) characters into one value               | paste("hi", "there") returns "hi there"            | 
| nchar(str)     | Counts the number of characters in a string                   | nchar("hi there") returns 8 (space is a character!)| 
| c(a,b,...)     | Concatenate (combine) multiple items into a vector            | c(1, 2) returns 1, 2                               |
| seq(a,b)       | Return a sequence of numbers from a to b                      | seq(1, 5) returns 1, 2, 3, 4, 5                    |

-------------------

### 5. Data Frames

* Creating data frames
```
example_dataframe <- data.frame(vector1, vector2)
```
* Finding dimensions of a data frame
```
dim(dataframe_name)
[1] 3 2 #dataframe_name has 3 rows and 2 columns
```
* Describing Structure of Data Frames

-------------------

| Function            	 | Description                                                         |
|------------------------|---------------------------------------------------------------------|
| nrow(my_data_frame)	   | Number of rows in the data frame                                    |
| ncol(my_data_frame)	   | Number of columns in the data frame                                 |
| dim(my_data_frame)	   | Dimensions (rows, columns) in the data frame                        |
| colnames(my_data_frame)| Names of the columns of the data frame                              |
| rownames(my_data_frame)| Names of the row of the data frame                                  |
| head(my_data_frame)	   | Extracts the first few rows of the data frame (as a new data frame) |
| tail(my_data_frame)	   | Extracts the last few rows of the data frame (as a new data frame)  |
| View(my_data_frame)	   | Opens the data frame in as spreadsheet-like viewer (only in RStudio)|

-------------------

*  Accessing Data in Data Frames

-------------------

| Syntax                    |	Description	                                      | Example                                                        |
|---------------------------|---------------------------------------------------|----------------------------------------------------------------|
| my_df[row_num, col_num]	  | Element by row and column indices	                | my_frame[2,3] (element in the second row, third column)        |
| my_df[row_name, col_name]	| Element by row and column names	                  | my_frame['Ada','height'] (element in row Ada and column height |
| my_df[row, col]	          | Element by row and col; can mix indices and names	| my_frame[2,'height'] (second element in the height column)     |
| my_df[row, ]	            | All elements (columns) in row index or name	      | my_frame[2,] (all columns in the second row)                   |
| my_df[, col]	            | All elements (rows) in a col index or name	      | my_frame[,'height'] (all rows in the height column)            |

### 6. The dplyr library

* Combine vectors into a data frame
```
dplyr::data_frame(a = 1:3, b = 4:6)
```
* Order rows by values of a column(low to high)
```
dplyr::arrange(dataframe_name, column_name)
```
* Order rows by values of a column(high to low)
```
dplyr::arrange(dataframe_name, desc(column_name))
```
* Rename the columns of a data frame
```
dplyr::rename(dataframe_name, old_name = new_name)
```
* Extract rows that meet logical criteria
```
dplyr::filter(df_name, df_name.col_name > 7)
```
* Remove duplicate rows
```
dplyr::distinct(df_name)
```
* Select columns by name
```
dplyr::select(df_name, df_name.col_name)
```
* Select columns whose name contains a character string
```
select(df_name, contains("."))
```
* Select columns whose name starts with a character string
```
select(df_name, starts_with("abc"))
```
* Select columns whose name ends with a character string
```
select(df_name, ends_with("abc"))
```
* Select every column
```
select(df_name, everything())
```
* Summarise data into single row of values
```
dplyr::summarise(df_name, avg = mean(col_name))
```
* Apply summary function to each column
```
dplyr::summarise_each(df_name, funs(mean))
```
* Compute and append one or more new columns
```
dplyr::mutate(df_name, new_col_name = existing_col1 + existing_col2)
```
* Group data into rows with the same value of Species
```
dplyr::group_by(df_name, col_name)
```
* Remove grouping information from data frame
```
dplyr::ungroup(df_name)
```
* Compute separate summary row for each group
```
df_name %>% group_by(col_name) %>% summarise(...)
```
* Compute new variables by group
```
df_name %>% group_by(col_name) %>% mutate(...)
```
* Join matching rows from dataframe b to a
```
dplyr::left_join(a, b, by = "x1")
```
* Join matching rows from dataframe a to b
```
dplyr::right_join(a, b, by = "x1")
```
* Join data. Retain only rows in both sets
```
dplyr::inner_join(a, b, by = "x1")
```
* Join data. Retain all values, all rows
```
dplyr::full_join(a, b, by = "x1")
```
### 7. ggplot2 library
* Build a basic graph with ggplot()
```
ggplot(data = df_name, aes(x = col_name1, y = col_name2))
```
* Saves last plot as 5’ x 5’ file named "plot.png" in working directory. Matches file type to file extension
```
ggsave("plot.png", width = 5, height = 5)
```
#Installing Required packages

install.packages("pryr")
require(pryr)
require(ISLR)
require(boot)
install.packages("plyr")
library(data.table)
library(plyr)


#Load students data from the table in given dataset

students_data<- read.table("C:/Users/DELL/OneDrive/Desktop/Assignment6_Dataset.txt", header = TRUE,sep=",")
print(students_data)


#Using ddply to calculate mean of the grades for different genders

StudentAverage = ddply(students_data,"Sex",transform,Grade.Average=mean(Grade))
print(StudentAverage)

# Writing the output to a file

write.table(StudentAverage, file = "StudentAverageOutput.txt", row.names = FALSE) 


#using grepl as a filter created a new subset, which contains students with letter i in their name

i_students <- subset(students_data, grepl("i", students_data$Name, ignore.case=T))
print(i_students)

#Writing the names to a file separated by commas (CSV)

write.csv(i_students$Name, file = "i_students_names.csv")


# Writing the filtered dataset to a CSV file

write.csv(i_students, file = "i_students_data.csv")


###########################################################################################################################################################################################

# The above code is about importing a dataset, calculate means, create subsets, and write dataframes to files in various formats. Detailed explaination for the code is below:


1.	install.packages("pryr"): Installs the "pryr" package from CRAN, which provides tools for inspecting memory usage in R.

2.	require(pryr): Loads the "pryr" package into the current R session. This package will be used for memory management tasks.

3.	require(ISLR): Loads the "ISLR" package into the current R session. This package contains datasets and functions for the book "An Introduction to Statistical Learning with Applications in R".

4.	require(boot): Loads the "boot" package into the current R session. This package provides functions and datasets for bootstrapping techniques.

5.	install.packages("plyr"): Installs the "plyr" package from CRAN, which provides tools for splitting, applying, and combining data.

6.	library(data.table): Loads the "data.table" package into the current R session. This package provides an extension of data frames in R with enhanced features.

7.	library(plyr): Loads the "plyr" package into the current R session. This package was already installed in step 5, and now it's loaded for use.

8.	students_data<- read.table("C:/Users/DELL/OneDrive/Desktop/Assignment6_Dataset.txt", header = TRUE,sep=","): Reads the dataset located at the specified file path into R. The dataset is assumed to have a header row and use comma (,) as the separator.

9.	print(students_data): Prints the contents of the students_data dataframe to the console.

10.	StudentAverage = ddply(students_data,"Sex",transform,Grade.Average=mean(Grade)): Uses the ddply() function from the "plyr" package to calculate the mean of the grades for different genders. The result is stored in a new dataframe called StudentAverage.

11.	print(StudentAverage): Prints the contents of the StudentAverage dataframe to the console.

12.	write.table(StudentAverage, file = "StudentAverageOutput.txt", row.names = FALSE): Writes the StudentAverage dataframe to a text file named "StudentAverageOutput.txt" without including row names.

13.	i_students <- subset(students_data, grepl("i", students_data$Name, ignore.case=T)): Creates a subset of the students_data dataframe containing only those rows where the student's name contains the letter "i". This subset is stored in a new dataframe called i_students.

14.	print(i_students): Prints the contents of the i_students dataframe to the console.

15.	write.csv(i_students$Name, file = "i_students_names.csv"): Writes the names of students in the i_students dataframe to a CSV file named "i_students_names.csv".

16.	write.csv(i_students, file = "i_students_data.csv"): Writes the entire i_students dataframe to a CSV file named "i_students_data.csv".

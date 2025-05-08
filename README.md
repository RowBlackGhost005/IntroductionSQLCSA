# Introduction to SQL 
**ALL THIS INFORMATION IS CONTAINED IN THE .SQL FILE**

/*Create your first database*/
---
CREATE DATABASE StudentRecords;

/*Create Table with Appropiate Data Types*/
---
CREATE TABLE Students(
studentId INT PRIMARY KEY,
firstName VARCHAR(50),
lastName VARCHAR(50),
age INT,
email VARCHAR(100)
);

/*Insert Simple Data*/
---
INSERT INTO Students (studentId, firstName, lastName , age , email) VALUES
(1, 'Jhon' , 'Doe' , 20 , 'jhon.doe@mail.com'),
(2, 'Mark' , 'Smith' , 22 , 'marks@mail.com'),
(3, 'Alyson' , 'Roberts' , 19 , 'aly.r@mail.com'),
(4, 'Robert' , 'Swartsman' , 21 , 'robertsman@mail.com'),
(5, 'Carlos' , 'Sainz' , 23 , 'carlos.sainz@mail.com');

/*BONUS: Create Second table Course*/
---
CREATE TABLE Courses(
courseId INT PRIMARY KEY,
courseName VARCHAR(50),
courseDescription VARCHAR(150));

/*BONUS: Inserting data for Courses*/
---
INSERT INTO Courses (courseId , courseName , courseDescription) VALUES 
(1 , "Data Bases" , "Introduction to Data Bases"),
(2 , "Web Development" , "Basic web development with React"),
(3 , "App Deployment" , "Deployment CI/CD apps with AWS"),
(4 , "Java" , "Basic to Advanced Java topics for app development");

/*BONUS: Altering table to create a relationship between Students and Courses*/
---
ALTER TABLE Students 
ADD COLUMN courseId INT ,
ADD FOREIGN KEY (courseId) REFERENCES Students (studentId);

/*BONUS: Creating (Updating students) relationships between Students and Courses (Students have A Course)*/
---
UPDATE Students SET courseId = 1 WHERE studentId = 1;
UPDATE Students SET courseId = 2 WHERE studentId = 2;
UPDATE Students SET courseId = 4 WHERE studentId = 3;
UPDATE Students SET courseId = 3 WHERE studentId = 4;
UPDATE Students SET courseId = 4 WHERE studentId = 5;

/*UNDERSTANDING DATABASE BASICS:
A database is a collection of data that has a defined structure and an API to
interact with it to create, delete and modifiy its structure and the data it
holds, there are different kinds of databases, the most used ones being
the relational databases where data is stored in tables where a row is a new
entry and a column is an attribute for that entry that has a specific datatype.
Databases allow us to manage large amounts of data and perform operations on them,
this is why they are essentials for development, they allow us to operate over
the data in a structured way providing us a lot of features to ensure consistency
and accessibility.
*/

/*BASIC COMMANDS*/
---

/*Insert Data*/
---
INSERT INTO Students (studentId, firstName, lastName , age , email , courseId) VALUES
(6, 'Jose' , 'Jhonson' , 21 , 'jhonson.@mail.com', 3),
(7, 'Danny' , 'Lopez' , 20 , 'danny.lop@mail.com', 4);

/*Select Data*/
---
SELECT * FROM students;

/*Modify the age of one student*/
---
UPDATE Students SET age = 22 WHERE studentId = 6;

/*
Question 1: Why did you choose specific data types for the columns in the Student Table?
- This data types makes sense for the information being stored like a String for a
name and Int for ages and Ids, and this allow for better queries later on like
asking for students between X range of age.
*/

/*
Question 2: What are some benefits of using databases over simple fire storage systems?
- Databases are optimized for storage and query the data that its in it and on top if it
it has complex characteristics like access control and they can also be in a remote
server location and can still be accessed.
Meanwhile simple files are unrealiable, cannot be accessed by multiple people and every
time it will need a complete module on top of it to be able to manage it based on the
app needs.
*/

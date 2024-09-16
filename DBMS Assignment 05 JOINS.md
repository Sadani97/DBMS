CREATE DATABASE School;

USE School;

CREATE TABLE Student(
	student_id VARCHAR(20) PRIMARY KEY,
	first_name VARCHAR(20),
	last_name VARCHAR(20)
);

DESC Student;


INSERT INTO Student vALUES(1,'Kamal','Perera'),(2,'Nimal','Samson'),(3,'Amal','Perera'),(4,'Roy','Silva');

SELECT * FROM Student;


CREATE TABLE student_contact(
	student_id VARCHAR(20) PRIMARY KEY,
	email_address VARCHAR(20),
	contact INT(20) UNIQUE NOT NULL,
	CONSTRAINT FOREIGN KEY(student_id) REFERENCES Student(student_id)
);
DESC student_contact;




INSERT INTO student_contact VALUES(1,'kamal@school.edu',077234512),(2,'nimal@school.edu',077456396),(3,'amal@school.edu',077743566);


SELECT * FROM student_contact;


SELECT Student.student_id,Student.first_name,student_contact.contact
FROM Student
LEFT JOIN student_contact
ON Student.student_id=student_contact.student_id;


SELECT Student.student_id,Student.first_name,student_contact.email_address AS Email
FROM Student
LEFT JOIN student_contact
ON Student.student_id=student_contact.student_id;

SELECT Student.student_id, CONCAT (first_name,' ',last_name),student_contact.email_address
FROM Student
LEFT JOIN student_contact
ON Student.student_id=student_contact.student_id;



SELECT Student.student_id, Student.first_name,student_contact.email_address 
FROM Student 
LEFT JOIN student_contact 
ON Student.student_id=student_contact.student_id
WHERE Student.first_name LIKE  '%mal';


/////////////////////////////////////////////////////

CREATE TABLE DepartmentInfo(
	DepartmentID VARCHAR(20) PRIMARY KEY,
	DepartmentName VARCHAR(20)
	);

DESC DepartmentInfo;

INSERT INTO DepartmentInfo VALUES(101,'Computer Science'),(102,'Mathematics'),(103,'History');


SELECT * FROM DepartmentInfo;



CREATE TABLE StudentInfo(
	StudentID VARCHAR(20) PRIMARY KEY,
	StudentName VARCHAR(20),
	DepartmentID VARCHAR(20),
	CONSTRAINT FOREIGN KEY(DepartmentID) REFERENCES DepartmentInfo(DepartmentID)
);

DESC StudentInfo;


INSERT INTO StudentInfo VALUES(1,'Alice',101),(2,'Bob',102),(3,'Carol',101),(4,'Dave',103);

SELECT * FROM StudentInfo;



CREATE TABLE CourseInfo(
	CourseID VARCHAR(20) PRIMARY KEY,
	CourseName VARCHAR(20),
	DepartmentID VARCHAR(20), 
	CONSTRAINT FOREIGN KEY(DepartmentID) REFERENCES DepartmentInfo(DepartmentID)

);
DESC CourseInfo;


INSERT INTO CourseInfo VALUES(1,'Database Systems',101),(2,'Calculus',102),(3,'World History',103);



SELECT * FROM CourseInfo;


SELECT StudentInfo.StudentName,DepartmentInfo.DepartmentName
FROM DepartmentInfo
INNER JOIN StudentInfo
ON DepartmentInfo.DepartmentID=StudentInfo.DepartmentID;


SELECT StudentInfo.StudentName,DepartmentInfo.DepartmentName
FROM DepartmentInfo
RIGHT JOIN StudentInfo
ON DepartmentInfo.DepartmentID=StudentInfo.DepartmentID;

SELECT DepartmentInfo.DepartmentName,StudentInfo.StudentName
FROM DepartmentInfo
LEFT JOIN StudentInfo
ON DepartmentInfo.DepartmentID=StudentInfo.DepartmentID;




SELECT DepartmentInfo.DepartmentName, StudentInfo.StudentName
FROM DepartmentInfo
INNER JOIN StudentInfo
ON DepartmentInfo.DepartmentID=StudentInfo.DepartmentID
COUNT(StudentName) FROM StudentInfo;


SELECT DepartmentInfo.DepartmentName, COUNT(StudentInfo.StudentName) FROM DepartmentInfo
INNER JOIN StudentInfo
ON DepartmentInfo.DepartmentID = StudentInfo.DepartmentID
GROUP BY DepartmentInfo.DepartmentID;





SELECT StudentInfo.StudentName,CourseInfo.CourseName,DepartmentInfo.DepartmentName
FROM DepartmentInfo
INNER JOIN StudentInfo
ON DepartmentInfo.DepartmentID = StudentInfo.DepartmentID
INNER JOIN CourseInfo
ON DepartmentInfo.DepartmentID = CourseInfo.DepartmentID
WHERE DepartmentInfo.DepartmentName='Computer Science ;








SELECT DepartmentInfo.DepartmentName, COUNT(StudentInfo.StudentName) 
FROM DepartmentInfo
INNER JOIN StudentInfo
ON DepartmentInfo.DepartmentID = StudentInfo.DepartmentID
GROUP BY DepartmentInfo.DepartmentID
HAVING COUNT(StudentInfo.StudentName) >1;




SELECT StudentInfo.StudentName,DepartmentInfo.DepartmentName,CourseInfo.CourseName
FROM StudentInfo
INNER JOIN DepartmentInfo
ON DepartmentInfo.DepartmentID = StudentInfo.DepartmentID
INNER JOIN CourseInfo
ON DepartmentInfo.DepartmentID = CourseInfo.DepartmentID
WHERE DepartmentInfo.DepartmentName='Computer Science' AND CourseInfo.CourseName='Database Systems';




///////////////////////////////////////////////////////////////////////////////////////////////////////



CREATE TABLE Author(
	AuthorID VARCHAR(20) PRIMARY KEY,
	AuthorName VARCHAR(20),
	Country VARCHAR(20)
);

DESC Author;

INSERT INTO Author VALUES(1,'John Smith','USA'),(2,'Emily Brown','UK'),(3,'Maria Lopez','Spain');


SELECT * FROM Author;



CREATE TABLE Book(
	BookID VARCHAR(20) PRIMARY KEY,
	Title VARCHAR(20),
	AuthorID VARCHAR(20),
	PublicationYear INT(10),
	CONSTRAINT FOREIGN KEY(AuthorID) REFERENCES Author(AuthorID)
);

DESC Book;


INSERT INTO Book VALUES(1,'The Book of Life',1,2020),(2,'Secrets Revealed',2,2019),(3,'Mystery Tales',1,2022),(4,'Spanish Cuisine',3,2021);

SELECT * FROM Book;



CREATE TABLE Reader(
	ReaderID VARCHAR(20) PRIMARY KEY,
	ReaderName VARCHAR(20),
	BookID VARCHAR(20),
	CONSTRAINT FOREIGN KEY(BookID) REFERENCES Book(BookID)
);
DESC Reader;


INSERT INTO Reader VALUES(101,'Alice',1),(102,'Bob',2),(103,'Carol',3),(104,'David',1);


SELECT * FROM Reader;


SELECT Author.AuthorName, COUNT(Author.AuthorID) AS TotalNoOfBooks
FROM Author
LEFT JOIN Book
ON Author.AuthorID=Book.AuthorID
GROUP BY Author.AuthorID;


SELECT Author.AuthorName, Book.PublicationYear
FROM Author
RIGHT JOIN Book
ON Author.AuthorID=Book.AuthorID;



SELECT Book.Title,Book.PublicationYear,Author.AuthorName
FROM Author
INNER JOIN Book
ON Author.AuthorID=Book.AuthorID
WHERE Book.PublicationYear<2020;




SELECT Book.Title,Reader.ReaderName
FROM Book
INNER JOIN Reader
ON Book.BookID=Reader.BookID
WHERE Reader.ReaderID IN (101, 102);




SELECT Book.Title,Reader.ReaderName
FROM Book
INNER JOIN Reader
ON Book.BookID=Reader.BookID
WHERE Reader.ReaderID IN (101, 102) AND Book.BookID=2;








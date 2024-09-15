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




INSERT INTO student_contact vALUES(1,'kamal@school.edu',077234512),(2,'nimal@school.edu',077456396),(3,'amal@school.edu',077743566);


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










CREATE DATABASE AirportManagement;
USE AirportManagement;

CREATE TABLE Airline(
        airline_id INT AUTO_INCREMENT,
	airline_name VARCHAR(100) NOT NULL,
	country VARCHAR(50) NOT NULL,
	CONSTRAINT PRIMARY KEY(airline_id)
);
DESC Airline;

INSERT INTO Airline VALUES(1,'Delta Airlines','USA');
INSERT INTO Airline (airline_name,country) VALUES('Emirates','UAE');
INSERT INTO Airline (airline_name,country) VALUES('Lufthansa','Germany');

SELECT * FROM Airline;







CREATE TABLE Flight(
	flight_id INT AUTO_INCREMENT,
	airline_id INT,
	flight_number VARCHAR(20) NOT NULL,
	origin VARCHAR(50) NOT NULL,
	destination VARCHAR(50) NOT NULL,
	departure_time DATETIME,
	arrival_time DATETIME,
	CONSTRAINT PRIMARY KEY(flight_id,airline_id),
	CONSTRAINT FOREIGN KEY (airline_id) REFERENCES Airline (airline_id)
);
DESC Flight;


INSERT INTO Flight VALUES(1,1,'DL123','New York','Los Angeles','2023-01-01 08:00:00','2023-01-01 10:30:00');
INSERT INTO Flight (airline_id,flight_number,origin,destination,departure_time,arrival_time) VALUES(2,'EK456','Dubai','London','2023-01-02 14:00:00','2023-01-02 18:00:00');
INSERT INTO Flight (airline_id,flight_number,origin,destination,departure_time,arrival_time) VALUES(3,'LH789','Berlin','Paris','2023-01-03 09:30:00','2023-01-03 11:30:00');

SELECT * FROM Flight;











CREATE TABLE Ticket(
	ticket_id INT AUTO_INCREMENT ,
	flight_id INT,
	ticket_price DECIMAL(10,2) NOT NULL,
	ticket_class VARCHAR(20),
	CONSTRAINT PRIMARY KEY(ticket_id,flight_id),
	CONSTRAINT FOREIGN KEY (flight_id) REFERENCES Flight(flight_id)	
);
DESC Ticket;

INSERT INTO Ticket VALUES(1,1,250,'Economy');
INSERT INTO Ticket (flight_id,ticket_price,ticket_class) VALUES(2,500,'Business');
INSERT INTO Ticket (flight_id,ticket_price,ticket_class) VALUES(3,300,'Economy');

SELECT * FROM Ticket;






CREATE TABLE Passenger(
	passenger_id INT  AUTO_INCREMENT,
	first_name VARCHAR(50) NOT NULL,
	last_name VARCHAR(50) NOT NULL,
	email VARCHAR(100),
	age INT,
	seat_number VARCHAR(10),
	ticket_id INT,
	CONSTRAINT PRIMARY KEY(passenger_id,ticket_id),
	CONSTRAINT FOREIGN KEY (ticket_id) REFERENCES Ticket(ticket_id)
);
DESC Passenger;


INSERT INTO Passenger VALUES(4,'John','Doe','john@example.com',30,'A23',1);
INSERT INTO Passenger (first_name,last_name,email,age,seat_number,ticket_id) VALUES('Emma','Smith','emma@example.com',25,'B15',2);
INSERT INTO Passenger (first_name,last_name,email,age,seat_number,ticket_id)  VALUES('Micheal','Johnson','micheal@example.com',40,'C10',3);

SELECT * FROM Passenger;




UPDATE Flight
SET destination='Paris'
WHERE flight_id=2;

SELECT * FROM Flight;


UPDATE Ticket SET ticket_price=350 WHERE ticket_class='Economy' AND Flight_id=2;

SELECT * FROM Ticket;

UPDATE Flight SET departure_time= '2023-02-01 
10:00:00' WHERE origin='New York' OR destination='Los Angeles';

SELECT * FROM Flight;



SELECT  flight_id FROM Flight  WHERE origin='Berlin' AND destination='Paris';


SELECT  * FROM Ticket  WHERE ticket_class='Business' OR ticket_class='Economy';


SELECT  * FROM Passenger  WHERE age=25 OR email='last_name+@example.com';

SELECT * FROM Passenger Limit 5;


SELECT  * FROM Ticket  ORDER BY ticket_price DESC Limit 3;

SELECT COUNT(flight_id) FROM Flight;


SELECT COUNT(passenger_id) FROM Passenger WHERE age>30;



SELECT * FROM Ticket WHERE ticket_price>300;


SELECT * FROM Flight ORDER BY departure_time  DESC;

SELECT * FROM Passenger ORDER BY age  DESC;

SELECT * FROM Ticket ORDER BY ticket_price  DESC;

SELECT * FROM Passenger ORDER BY first_name;

SELECT * FROM Ticket ORDER BY ticket_class;

SELECT * FROM Flight ORDER BY origin ASC, destination DESC;

SELECT * FROM Passenger ORDER BY age DESC, last_name DESC;



SELECT * FROM flight
WHERE arrival_time BETWEEN '2023-01-01 12:00:00' AND '2023-01-03 12:00:00';

SELECT Passenger.passenger_id,Passenger.first_name, Flight.flight_id, Ticket.flight_id, Ticket.ticket_id
FROM Passenger
INNER JOIN Ticket
ON Passenger.ticket_id = Ticket.flight_id
INNER JOIN  Flight 
ON Ticket.ticket_id = Flight.flight_id

WHERE Flight.origin = 'New York';














# LittleLemon
Meta Database Engineer Certificate
Scenario

Little Lemon, a family-owned Mediterranean restaurant in Chicago, Illinois, combines traditional recipes with a modern twist, drawing inspiration from Italian, Greek, and Turkish cultures. Owned by brothers Mario and Adrian, the restaurant has a rotating menu and a rustic atmosphere. Mario, the chef, incorporates family recipes, while Adrian handles marketing.

Prerequisites

Database Creation:
sql
Copy code
CREATE DATABASE IF NOT EXISTS Little_Lemon;
Use the Database:
sql
Copy code
USE Little_Lemon;
Customers Table Creation:
sql
Copy code
CREATE TABLE Customers(
    CustomerID INT NOT NULL PRIMARY KEY, 
    FullName VARCHAR(100) NOT NULL, 
    PhoneNumber INT NOT NULL UNIQUE
);
Customers Table Data Insertion:
sql
Copy code
INSERT INTO Customers(CustomerID, FullName, PhoneNumber) VALUES 
(1, "Vanessa McCarthy", 0757536378),
...
(9, "Mike Edwards", 0757236375);
Bookings Table Creation:
sql
Copy code
CREATE TABLE Bookings(
    BookingID INT, 
    BookingDate DATE, 
    TableNumber INT, 
    NumberOfGuests INT,
    CustomerID INT
);
Bookings Table Data Insertion:
sql
Copy code
INSERT INTO Bookings (BookingID, BookingDate, TableNumber, NumberOfGuests, CustomerID) VALUES
(10, '2021-11-10', 7, 5, 1),
...
(21, '2021-11-14', 3, 2, 4);
Courses Table Creation:
sql
Copy code
CREATE TABLE Courses (
    CourseName VARCHAR(255) PRIMARY KEY, 
    Cost Decimal(4,2)
);
Courses Table Data Insertion:
sql
Copy code
INSERT INTO Courses (CourseName, Cost) VALUES 
("Greek salad", 15.50),
...
("Shwarma", 11.30);
Task Instructions

Task 1: Filter data using the WHERE Clause and Logical Operators.

SELECT * FROM Bookings
WHERE BookingDate BETWEEN '2021-11-11' AND '2021-11-13';

Task 2: Create a JOIN Query.

SELECT Customers.FullName, Bookings.BookingID
FROM Customers
JOIN Bookings ON Customers.CustomerID = Bookings.CustomerID
WHERE BookingDate = '2021-11-11';

Task 3: Create a GROUP BY Query.

SELECT BookingDate, COUNT(*) as TotalBookings
FROM Bookings
GROUP BY BookingDate;

Task 4: Create a REPLACE Statement.

UPDATE Courses
SET Cost = 20.00
WHERE CourseName = 'Kabasa';

Task 5: Create Constraints.

CREATE TABLE DeliveryAddress (
    ID INT PRIMARY KEY, 
    Address VARCHAR(255) NOT NULL, 
    Type VARCHAR(50) NOT NULL DEFAULT 'Private', 
    CustomerID INT NOT NULL,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

Task 6: Alter Table Structure.

ALTER TABLE Courses
ADD COLUMN Ingredients VARCHAR(255);

Task 7: Create a Subquery.

SELECT FullName
FROM Customers
WHERE CustomerID IN (SELECT CustomerID FROM Bookings WHERE BookingDate = '2021-11-11');

Task 8: Create a Virtual Table.

CREATE VIEW BookingsView AS
SELECT BookingID, BookingDate, NumberOfGuests
FROM Bookings
WHERE BookingDate < '2021-11-13' AND NumberOfGuests > 3;

SELECT * FROM BookingsView;
Task 9: Create a Stored Procedure.

DELIMITER //
CREATE PROCEDURE GetBookingsData(IN InputDate DATE)
BEGIN
    SELECT * FROM Bookings WHERE BookingDate = InputDate;
END //
DELIMITER ;

CALL GetBookingsData('2021-11-13');

Task 10: Use the String Function.

SELECT 
    CONCAT('ID: ', BookingID, ', ', 'Date: ', BookingDate, ', ', 'Number of guests: ', NumberOfGuests) AS 'Booking Details'
FROM Bookings;


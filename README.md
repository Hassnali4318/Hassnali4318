CREATE DATABASE RailwayManagementSystem;
USE RailwayManagementSystem;
CREATE TABLE Passengers (
 passenger_id INT PRIMARY KEY AUTO_INCREMENT,
 name VARCHAR(100),
 age INT,
 gender VARCHAR(10),
 contact_info VARCHAR(100)
);
CREATE TABLE Trains (
 train_id INT PRIMARY KEY AUTO_INCREMENT,
 train_name VARCHAR(100),
 source VARCHAR(100),
 destination VARCHAR(100),
 total_seats INT
);
CREATE TABLE Tickets (
 ticket_id INT PRIMARY KEY AUTO_INCREMENT,
 passenger_id INT,
 train_id INT,
 booking_date DATE,
 status VARCHAR(20),
 FOREIGN KEY (passenger_id) REFERENCES Passengers(passenger_id),
 FOREIGN KEY (train_id) REFERENCES Trains(train_id)
);
CREATE TABLE Schedules (
 schedule_id INT PRIMARY KEY AUTO_INCREMENT,
 train_id INT,
 departure_time DATETIME,
 arrival_time DATETIME,
 platform INT,
 FOREIGN KEY (train_id) REFERENCES Trains(train_id)
);
CREATE TABLE Employees (
 employee_id INT PRIMARY KEY AUTO_INCREMENT,
 name VARCHAR(100),
 role VARCHAR(50),
 contact_info VARCHAR(100),
 station_id INT
);
CREATE TABLE Maintenance (
 maintenance_id INT PRIMARY KEY AUTO_INCREMENT,
 train_id INT,
 issue_description TEXT,
 date_reported DATE,
 resolved BOOLEAN,
 FOREIGN KEY (train_id) REFERENCES Trains(train_id)
);
CREATE TABLE StationFacilities (
 facility_id INT PRIMARY KEY AUTO_INCREMENT,
 facility_name VARCHAR(100),
 status VARCHAR(20),
 station_id INT
);







INSERT INTO Passengers (name, age, gender, contact_info)
VALUES 
('John Doe', 30, 'Male', 'john.doe@example.com'),
('Jane Smith', 25, 'Female', 'jane.smith@example.com')
INSERT INTO Trains (train_name, source, destination, total_seats)
VALUES 
('Express 101', 'City A', 'City B', 300),
('Express 202', 'City B', 'City C', 200)
INSERT INTO Tickets (passenger_id, train_id, booking_date, status)
VALUES 
(1, 1, '2024-06-01', 'Booked'),
(2, 2, '2024-06-02', 'Cancelled');

INSERT INTO Schedules (train_id, departure_time, arrival_time, platform)
VALUES 
(1, '2024-06-10 08:00:00', '2024-06-10 12:00:00', 1),
(2, '2024-06-11 09:00:00', '2024-06-11 13:00:00', 2)
INSERT INTO Employees (name, role, contact_info, station_id)
VALUES 
('Alice Johnson', 'Conductor', 'alice.johnson@example.com', 1),
('Bob Lee', 'Engineer', 'bob.lee@example.com', 1);
INSERT INTO Maintenance (train_id, issue_description, date_reported, resolved)
VALUES 
(1, 'Engine overheating', '2024-06-01', FALSE),
(2, 'Brake malfunction', '2024-06-02', TRUE);
INSERT INTO StationFacilities (facility_name, status, station_id)
VALUES 
('Waiting Room', 'Available', 1),
('Restroom', 'Maintenance', 1);
CREATE PROCEDURE BookTicket (
 IN p_passenger_id INT,
 IN p_train_id INT,
 IN p_booking_date DATE,
 IN p_status VARCHAR(20)
)
BEGIN
 INSERT INTO Tickets (passenger_id, train_id, booking_date, status)
 VALUES (p_passenger_id, p_train_id, p_booking_date, p_status);
CREATE PROCEDURE UpdateTrainSchedule (
 IN p_schedule_id INT,
 IN p_departure_time DATETIME,
 IN p_arrival_time DATETIME,
 IN p_platform INT
)
BEGIN
SET departure_time = p_departure_time, arrival_time = p_arrival_time, platform = 
p_platform
 WHERE schedule_id = p_schedule_id;
 Results in Detail
Booking a Ticket
To book a ticket for passenger with ID 1 on train with ID 1:
CALL BookTicket(1, 1, '2024-06-15', 'Booked');



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


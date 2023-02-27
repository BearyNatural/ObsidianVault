![[M20 1.png]]

- Create a simple database with the name cities.
- In this database, add a table that contains a "city" and a "country" field
- Insert some data
- To test it is working, make a query to request all cities in a specific country that you've inserted into the database.
- Answers:
	- mysql -u root -p [used to login; password is entered and you are in mariaDB]
	- show databases; [brings up a list of databases]
	- create database cities;
		- use cities; [moves you into the database]
	- create table cities(city VARCHAR(20), country VARCHAR(2));
		- insert into cities(city, country) values('Rome', 'IT');
		- insert into cities(city, country) values('Milan', 'IT');
	- select * from cities; [shows the tables with the inserted data]
		- insert into cities(city, country) values('Rotterdam', 'NL');
	- select * from cities where country = 'NL'; [filtering of dat]
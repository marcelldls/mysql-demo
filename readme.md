# mysql-demo
```
docker run -d -p 3306:3306 -v $(pwd)/conf.d:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=password mysql/mysql-server
```

Interact:
```
podman exec -ti <container> bash
```

Inside bash prompt:
```
mysql -u root -p  # MYSQL_ROOT_PASSWORD=password
```

Inside mysql shell:
```
CREATE DATABASE database_name;
SHOW DATABASES;
USE database_name;

CREATE TABLE Persons (
    PersonID int NOT NULL,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    PRIMARY KEY (PersonID) -- UNIQUE & no NULL, only one (multi column OK)
);
INSERT into Persons values (1,'Dave','Smith','2121');
INSERT into Persons values (2,'Tom','Smith','2331');
INSERT into Persons values (3,'John','Smith','2332');
SELECT * from Persons;  -- Displays table

CREATE TABLE Orders (
    PersonID int NOT NULL,
    OrderNumber int,
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID) -- Must be value from parent
);
INSERT into Orders values (1,2234);
INSERT into Orders values (1,2234);
INSERT into Orders values (2,2789);
SHOW TABLES;  -- Displays table names



```

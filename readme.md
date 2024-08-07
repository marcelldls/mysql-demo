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
    FirstName varchar(255) DEFAULT 'John',
    Age int,
    PRIMARY KEY (PersonID) -- UNIQUE & no NULL, only one (multi column OK)
    CHECK (Age>=18)
);
INSERT into Persons values (1,'Dave','Smith',19);
INSERT into Persons values (2,'Tom','Smith',21);
INSERT into Persons values (3,'John','Smith',21);
SELECT * from Persons;  -- Displays table

CREATE TABLE Orders (
    PersonID int NOT NULL,
    OrderNumber int,
    OrderDate date DEFAULT CURRENT_DATE()
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID) -- Must be value from parent
    UNIQUE (OrderNumber)
);
INSERT into Orders values (1,2234);
INSERT into Orders values (1,2234);
INSERT into Orders values (2,2789);
SHOW TABLES;  -- Displays table names

SELECT * FROM Persons
WHERE FirstName = 'Tom';
```

To run a script:
```
mysql --user="username" --database="databasename" -p <filepath>
```
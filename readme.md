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
mysql -u root -p
```

Inside mysql shell:
```
CREATE DATABASE database_name;

USE database_name;

CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255)
);

INSERT into Persons values (1,'Dave','Smith','2121');
INSERT into Persons values (2,'Dave','Smith','2331');
INSERT into Persons values (3,'John','Smith','2332');

SELECT * from Persons;
```
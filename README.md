# SQLhomework2

*** Using count, get the number of cities in the USA ***


mysql> use world;
Database changed
mysql> show tables;
+-----------------+
| Tables_in_world |
+-----------------+
| city            |
| country         |
| countrylanguage |
+-----------------+
3 rows in set (0.00 sec)

mysql> desc city;
+-------------+----------+------+-----+---------+----------------+
| Field       | Type     | Null | Key | Default | Extra          |
+-------------+----------+------+-----+---------+----------------+
| ID          | int      | NO   | PRI | NULL    | auto_increment |
| Name        | char(35) | NO   |     |         |                |
| CountryCode | char(3)  | NO   | MUL |         |                |
| District    | char(20) | NO   |     |         |                |
| Population  | int      | NO   |     | 0       |                |
+-------------+----------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> SELECT COUNT(*)
    -> FROM city
    -> WHERE countrycode = (SELECT code FROM country WHERE name = 'United States');

+----------+
| COUNT(*) |
+----------+
|      274 |
+----------+
1 row in set (0.02 sec)









*** Find out what the population and average life expectancy for people in Argentina (ARG) is! ***


mysql> SELECT Population, LifeExpectancy
    -> FROM Country
    -> WHERE code = 'ARG';
+------------+----------------+
| Population | LifeExpectancy |
+------------+----------------+
|   37032000 |           75.1 |
+------------+----------------+
1 row in set (0.00 sec)









*** Display all the cities for any country of your choice besides the USA ***


mysql> SELECT City.Name
    -> FROM City
    -> JOIN Country ON City.CountryCode = country.code
    -> WHERE country.name = 'El Salvador';
+--------------------+
| Name               |
+--------------------+
| San Salvador       |
| Santa Ana          |
| Mejicanos          |
| Soyapango          |
| San Miguel         |
| Nueva San Salvador |
| Apopa              |
+--------------------+
7 rows in set (0.01 sec)






*** Come up with two more queries of your own. ***



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

mysql> SELECT Name AS countryName, population
    -> FROM country
    -> ORDER BY population DESC
    -> LIMIT 5;
+---------------+------------+
| countryName   | population |
+---------------+------------+
| China         | 1277558000 |
| India         | 1013662000 |
| United States |  278357000 |
| Indonesia     |  212107000 |
| Brazil        |  170115000 |
+---------------+------------+
5 rows in set (0.02 sec)




mysql> SELECT name, population
    -> FROM country
    -> WHERE population < 6000000
    -> ORDER BY population DESC
    -> LIMIT 10;
+------------------------+------------+
| name                   | population |
+------------------------+------------+
| Libyan Arab Jamahiriya |    5605000 |
| Paraguay               |    5496000 |
| Laos                   |    5433000 |
| Slovakia               |    5398700 |
| Denmark                |    5330000 |
| Finland                |    5171300 |
| Jordan                 |    5083000 |
| Nicaragua              |    5074000 |
| Georgia                |    4968000 |
| Sierra Leone           |    4854000 |
+------------------------+------------+
10 rows in set (0.00 sec)

# zad01
list od teściowej

komendy skopowiane i wklejone 




mysql> Create TABLE postac( id_postaci int AUTO_INCREMENT, nazwa CHAR(40), rodzaj ENUM (wiking, ptak, kobieta), data_ur DATE, wiek TINYINT(3) UNSIGNED, PRIMARY KEY (id_postaci) );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'wiking, ptak, kobieta), data_ur DATE, wiek TINYINT(3) UNSIGNED, PRIMARY KEY (id_' at line 1
mysql> Create TABLE postac( id_postaci int AUTO_INCREMENT, nazwa CHAR(40), rodzaj ENUM ('wiking', 'ptak', 'kobieta'), data_ur DATE, wiek TINYINT(3) UNSIGNED, PRIMARY KEY (id_postaci) );
Query OK, 0 rows affected, 1 warning (0.02 sec)


mysql> SHOW TABLES
    -> ;
+--------------------+
| Tables_in_bralskim |
+--------------------+
| postac             |
+--------------------+
1 row in set (0.00 sec)



login as: bralskim
bralskim@213.184.8.36's password:
Linux bad2 4.10.17-1-pve #1 SMP PVE 4.10.17-16 (Tue, 11 Jul 2017 09:55:44 +0200)                                                                                                                                                  x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Tue Nov 15 20:30:03 2022 from 81.190.139.165
bralskim@bad2:~$ mysql -u bralskim -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 5189
Server version: 8.0.22 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW DATABASES
    -> ;
+--------------------+
| Database           |
+--------------------+
| bralskim           |
| information_schema |
+--------------------+
2 rows in set (0.00 sec)

mysql> USE bralskim
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> SHOW TABLES;
+--------------------+
| Tables_in_bralskim |
+--------------------+
| postac             |
+--------------------+
1 row in set (0.01 sec)

mysql> SELECT * FROM postac
    -> ;
Empty set (0.02 sec)

mysql> INSERT INTO postac
    -> (nazwa,rodzaj,data_ur,wiek)
    -> VALUES
    -> (Bjorn,wiking,1102-01-04,25);
ERROR 1054 (42S22): Unknown column 'Bjorn' in 'field list'
mysql> SHOW field list
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that                                                                                                                                                  corresponds to your MySQL server version for the right syntax to use near 'field                                                                                                                                                  list' at line 1
mysql> SELECT * FROM postac
    -> ;
Empty set (0.00 sec)

mysql> ^C
mysql> ALTER TABLE postac
    -> MODIFY COLUMN nazwa varchar(40);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> mysql> ALTER TABLE postac
    -> ALTER COLUMN nazwa varchar(40)
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that                                                                                                                                                  corresponds to your MySQL server version for the right syntax to use near 'TABLE                                                                                                                                                  postac
ALTER COLUMN nazwa varchar(40)' at line 1
mysql> SHOW TABLE postac
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'postac' at line 1
mysql> SHOW TABLES postac
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'postac' at line 1
mysql> DESC postac
    -> ;
+------------+---------------------------------+------+-----+---------+----------------+
| Field      | Type                            | Null | Key | Default | Extra          |
+------------+---------------------------------+------+-----+---------+----------------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_increment |
| nazwa      | varchar(40)                     | YES  |     | NULL    |                |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                |
| data_ur    | date                            | YES  |     | NULL    |                |
| wiek       | tinyint unsigned                | YES  |     | NULL    |                |
+------------+---------------------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> INSERT INTO postac
    -> (nazwa,rodzaj,data_ur,wiek)
    -> VALUES
    -> ('Bjorn','wiking',"1660-04-01",25);
Query OK, 1 row affected (0.01 sec)

mysql> SHOW TABLES postac
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'postac' at line 1
mysql> DESC postac;
+------------+---------------------------------+------+-----+---------+----------------+
| Field      | Type                            | Null | Key | Default | Extra          |
+------------+---------------------------------+------+-----+---------+----------------+
| id_postaci | int                             | NO   | PRI | NULL    | auto_increment |
| nazwa      | varchar(40)                     | YES  |     | NULL    |                |
| rodzaj     | enum('wiking','ptak','kobieta') | YES  |     | NULL    |                |
| data_ur    | date                            | YES  |     | NULL    |                |
| wiek       | tinyint unsigned                | YES  |     | NULL    |                |
+------------+---------------------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> SELECT * FROM postac;
+------------+-------+--------+------------+------+
| id_postaci | nazwa | rodzaj | data_ur    | wiek |
+------------+-------+--------+------------+------+
|          1 | Bjorn | wiking | 1660-04-01 |   25 |
+------------+-------+--------+------------+------+
1 row in set (0.00 sec)

mysql> INSERT INTO postac (nazwa,rodzaj,data_ur,wiek) VALUES ('Tesciowa','kobieta',"1500-03-01",89);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO postac (nazwa,rodzaj,data_ur,wiek) VALUES ('Drozd','ptak',"1663-03-09",11);
Query OK, 1 row affected (0.00 sec)

mysql> UPDATE postac
    -> SET wiek = 88,
    -> WHERE id_postac = 2 AND nazwa 'Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postac = 2 AND nazwa 'Tesciowa'' at line 3
mysql> UPDATE postac SET wiek = 88, WHERE id_postac = '2' AND nazwa 'Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postac = '2' AND nazwa 'Tesciowa'' at line 1
mysql> UPDATE postac SET wiek = 88, WHERE id_postac = '2' AND nazwa "Tesciowa";
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postac = '2' AND nazwa "Tesciowa"' at line 1
mysql> UPDATE postac SET wiek = 88, WHERE id_postaci = '2' AND nazwa "Tesciowa";
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postaci = '2' AND nazwa "Tesciowa"' at line 1
mysql> UPDATE postac SET wiek = 88, WHERE id_postaci = 2 AND nazwa 'Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postaci = 2 AND nazwa 'Tesciowa'' at line 1
mysql> UPDATE postac SET wiek=88, WHERE id_postaci=2 AND nazwa 'Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postaci=2 AND nazwa 'Tesciowa'' at line 1
mysql> UPDATE postac SET wiek=88, WHERE id_postaci=2 AND nazwa='Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postaci=2 AND nazwa='Tesciowa'' at line 1
mysql> UPDATE postac SET wiek=88, WHERE id_postaci=2;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE id_postaci=2' at line 1
mysql> SELECT * FROM postac;
+------------+----------+---------+------------+------+
| id_postaci | nazwa    | rodzaj  | data_ur    | wiek |
+------------+----------+---------+------------+------+
|          1 | Bjorn    | wiking  | 1660-04-01 |   25 |
|          2 | Tesciowa | kobieta | 1500-03-01 |   89 |
|          3 | Drozd    | ptak    | 1663-03-09 |   11 |
+------------+----------+---------+------------+------+
3 rows in set (0.00 sec)

mysql> UPDATE postac SET wiek=88, WHERE nazwa='Tesciowa';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'WHERE nazwa='Tesciowa'' at line 1
mysql> UPDATE postac SET wiek=88 WHERE nazwa='Tesciowa' AND id_postaci=2;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> jestem bardzo *niezadowolny* z tego przecinka;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'jestem bardzo *niezadowolny* z tego przecinka' at line 1
mysql> CREATE TABLE walizka(
    -> id_walizki INT AUTO_INCREMENT,
    -> pojemnosc INT NOT NULL,
    -> kolor ENUM ('rozowy','czerwony','teczowy','zolty'),
    -> id_wlasciciela INT,
    -> PRIMARY KEY (id_walizki)
    -> FOREGIN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FOREGIN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE)' at line 7
mysql> CREATE TABLE walizka( id_walizki INT AUTO_INCREMENT, pojemnosc INT NOT NULL, kolor ENUM ('rozowy','czerwony','teczowy','zolty'), id_wlasciciela INT, PRIMARY KEY (id_walizki), FOREGIN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE)' at line 1
mysql> CREATE TABLE walizka( id_walizki INT AUTO_INCREMENT, pojemnosc INT NOT NULL, kolor ENUM ('rozowy','czerwony','teczowy','zolty'), id_wlasciciela INT, PRIMARY KEY (id_walizki) FOREGIN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE)
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FOREGIN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE)' at line 1
mysql> CREATE TABLE walizka( id_walizki INT AUTO_INCREMENT, pojemnosc INT NOT NULL, kolor ENUM ('rozowy','czerwony','teczowy','zolty'), id_wlasciciela INT, PRIMARY KEY (id_walizki),
    -> FOREIGN KEY (id_wlasciciela)
    -> REFERENCES postac(id_postaci)
    -> ON DELETE CASCADE
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> ALTER TABLE walizka
    -> ALTER kolor SET DEFAULT 'rozowy'
    -> ;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> DESC walizka
    -> ;
+----------------+---------------------------------------------+------+-----+---------+----------------+
| Field          | Type                                        | Null | Key | Default | Extra          |
+----------------+---------------------------------------------+------+-----+---------+----------------+
| id_walizki     | int                                         | NO   | PRI | NULL    | auto_increment |
| pojemnosc      | int                                         | NO   |     | NULL    |                |
| kolor          | enum('rozowy','czerwony','teczowy','zolty') | YES  |     | rozowy  |                |
| id_wlasciciela | int                                         | YES  | MUL | NULL    |                |
+----------------+---------------------------------------------+------+-----+---------+----------------+
4 rows in set (0.00 sec)

mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela)
    -> VALUES
    -> (9,Bjorn)
    -> ;
ERROR 1054 (42S22): Unknown column 'Bjorn' in 'field list'
mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela) VALUES (9,'Bjorn');
ERROR 1366 (HY000): Incorrect integer value: 'Bjorn' for column 'id_wlasciciela' at row 1
mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela) VALUES (9,1);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela) VALUES (10,1);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela,kolor) VALUES (15,1,'czerwony');
Query OK, 1 row affected (0.00 sec)

mysql> SELECT * FROM walizka
    -> ;
+------------+-----------+----------+----------------+
| id_walizki | pojemnosc | kolor    | id_wlasciciela |
+------------+-----------+----------+----------------+
|          1 |         9 | rozowy   |              1 |
|          2 |        10 | rozowy   |              1 |
|          3 |        15 | czerwony |              1 |
+------------+-----------+----------+----------------+
3 rows in set (0.00 sec)

mysql> ^C
mysql> ^C
mysql> mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela,kolor) VALUES (15,1,'czerwony');
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela,kolor) VALUES (15,1,'czerwo' at line 1
mysql> ^C
mysql> ^Vv^C
mysql> ^C
mysql> ^C
mysql> mysql> INSERT INTO walizka (pojemnosc,id_wlasciciela,kolor) VALUES (15,1,'czerwony');^C
mysql> vvv^V^V^C^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^C
mysql> ^Mmysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    -> mysql> ^C
    ->

# zad12
list od teściowej






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


#Zadanie 1
CREATE TABLE postac(id_postaci INT NOT NULL AUTO_INCREMENT PRIMARY KEY, nazwa VARCHAR(40),rodzaj ENUM('wiking','ptak','kobieta'),data_ur DATE, wiek INT UNSIGNED);
 INSERT INTO postac values(0,'Bjorn','wiking','1983-03-17',39);
 INSERT INTO postac values(0,'Drozd','ptak','2017-12-24',4);
INSERT INTO postac values(0,'Tesciowa','kobieta','1934-4-11',87);
UPDATE postac SET wiek=88 WHERE nazwa='TESCIOWA';

#Zadanie 2
CREATE TABLE walizka (id_walizki INT AUTO_INCREMENT PRIMARY KEY,pojemnosc INT UNSIGNED,kolor ENUM('rozowy','czerwony','teczowy','zolty'),id_wlasciciela INT,FOREIGN KEY(id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE);
ALTER TABLE walizka MODIFY COLUMN kolor ENUM('rozowy','czerwony','teczowy','zolty') DEFAULT 'rozowy';
 INSERT INTO walizka VALUES(0,40,'czerwony',1);
INSERT INTO walizka VALUES(0,35,'teczowy',3);

#zadanie 3
CREATE TABLE izba(adres_budynku VARCHAR(40),nazwa_izby VARCHAR(20), metraz INT UNSIGNED, wlasciciel INT, FOREIGN KEY(wlasciciel) REFERENCES postac(id_postaci) ON DELETE SET NULL, PRIMARY KEY(adres_budynku,nazwa_izby));
ALTER TABLE izba ADD COLUMN color ENUM ('niebieski','czerwony','czarny')DEFAULT 'czarny';
 INSERT INTO izba VALUES('ul.sezamkowa 12','spizarnia',4,1,'niebieski');
 
#zadanie 4
CREATE TABLE przetwory(id_przetworu INT PRIMARY KEY,rok_produkcji YEAR DEFAULT 1985,id_wykonawcy INT, FOREIGN KEY(id_wykonawcy)REFERENCES postac(id_postaci),zawartosc VARCHAR(40),dodatek VARCHAR (20) DEFAULT 'papryczka chilli',id_konsumenta INT, FOREIGN KEY(id_konsumenta)REFERENCES postac(id_postaci));INS
INSERT INTO przetwory VALUES(1,'2010',1,'czosnek,kielbasa,kiszona kapusta',DEFAULT,3);

#zadanie 5
INSERT INTO postac VALUES(0,'Alf','wiking','1967-05-12',55);
INSERT INTO postac VALUES(0,'Alrik','wiking','1980-05-02',42);
INSERT INTO postac VALUES(0,'Erp','wiking','1979-11-07',44);
INSERT INTO postac VALUES(0,'Geitir','wiking','1990-06-23',32);
INSERT INTO postac VALUES(0,'Haki','wiking','1985-10-17',37);

CREATE TABLE statek(nazwa VARCHAR (20) PRIMARY KEY,rodzaj ENUM('Drakkar','Knara','Sneka'),data_wodowania DATE,max_ladownosc INT UNSIGNED);
INSERT INTO statek VALUES('statek1','Drakkar','2012-02-13',45);
INSERT INTO statek VALUES('statek2','Sneka','2016-06-27',45);

UPDATE postac SET funkcja='kapitan' WHERE nazwa LIKE 'Bjorn';
 ALTER TABLE postac ADD COLUMN nazwa_statku VARCHAR(20),ADD FOREIGN KEY(nazwa_statku)REFERENCES statek(nazwa);
UPDATE postac SET nazwa_statku='statek1' WHERE nazwa LIKE('Drozd');
 UPDATE postac SET nazwa_statku='statek2' WHERE rodzaj LIKE ('wiking');
 DELETE FROM izba WHERE nazwa_izby='spizarnia';
 DROP TABLE izba;
       PDF 2


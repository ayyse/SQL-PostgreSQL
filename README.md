# SQL-PostgreSQL
patika.dev sql assignments


## Ödev 1
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.


- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

  `SELECT title,description FROM film;`
  
- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

  `SELECT length FROM film WHERE length > 60 AND length < 75;`
  
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

  `SELECT * FROM film WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);`
  
- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

  `SELECT last_name FROM customer WHERE first_name = 'Mary';`
  
  last_name = Smith

- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

  `SELECT length FROM film WHERE NOT length > 50 AND (rental_rate = 2.99 OR rental_rate = 4.99);`
  
---


## Ödev 2
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.



- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

  `SELECT * FROM film WHERE replacement_cost BETWEEN 12.99 AND 16.99;`
  
- actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

  `SELECT first_name, last_name FROM actor WHERE first_name IN ('Penelope', 'Nick', 'Ed');`
  
- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

  `SELECT * FROM film WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);`
  
---

## Ödev 3
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

  `SELECT * FROM country WHERE country LIKE 'A%a';`
  
- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

  `SELECT * FROM country WHERE country LIKE '%n' AND length(country) >= 6;`
  
- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

  `SELECT title FROM film WHERE title ILIKE '%T%T%T%T%';`
  
- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

  `SELECT * FROM film WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;`
  
---

## Ödev 4
Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

  `SELECT DISTINCT replacement_cost FROM film;`
 
- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

  `SELECT COUNT(DISTINCT(replacement_cost))  FROM film;`
  
- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

  `SELECT title, rating FROM film WHERE title LIKE 'T%' AND rating = 'G';`
  
- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

  `SELECT COUNT(*) FROM country WHERE length(country) = 5;`
  
- city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

  `SELECT COUNT(*) FROM city WHERE city ILIKE '%R';`

---


## Ödev 5

- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

  `SELECT * FROM film WHERE title LIKE '%n' ORDER BY length DESC LIMIT 5;`

- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

  `SELECT * FROM film WHERE title LIKE '%n' ORDER BY length OFFSET 5 LIMIT 5;`

- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

  `SELECT * FROM customer WHERE store_id = 1 ORDER BY last_name DESC LIMIT 4;`
  
---

## Ödev 6
- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

  `SELECT AVG(rental_rate) FROM film;`

- film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

  `SELECT COUNT(*) FROM film WHERE title LIKE 'C%';`

- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

  `SELECT MAX(length) FROM film WHERE rental_rate = 0.99;`

- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

  `SELECT COUNT(DISTINCT(replacement_cost)) FROM film WHERE length > 150;`

---

## Ödev 7

- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

  `SELECT rating FROM film GROUP BY rating;`

- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

  `SELECT replacement_cost, COUNT(*) FROM film GROUP BY replacement_cost HAVING COUNT(*) > 50;`

- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

  `SELECT store_id, COUNT(*) FROM customer GROUP BY store_id;`

- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

  `SELECT country_id, COUNT(*) FROM city GROUP BY country_id ORDER BY COUNT(*) DESC LIMIT 1;`
  
---

## Ödev 8

- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```
CREATE TABLE employee (
  id SERIAL PRIMARY KEY,
  first_name VARCHAR(50) NOT NULL,
  last_name VARCHAR(50) NOT NULL,
  birthday DATE,
  email VARCHAR(100)
);
```

- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

```

insert into employee (id, first_name, last_name, birthday, email) values (1, 'Jerrylee', 'Searight', '2021-05-29 06:13:00', 'jsearight0@google.com.br');
insert into employee (id, first_name, last_name, birthday, email) values (2, 'Darcy', 'MacSwayde', '2020-11-05 09:58:56', 'dmacswayde1@smugmug.com');
insert into employee (id, first_name, last_name, birthday, email) values (3, 'Hall', 'Mecco', '2021-07-28 22:17:18', 'hmecco2@vkontakte.ru');
insert into employee (id, first_name, last_name, birthday, email) values (4, 'Mira', 'Keedy', '2021-02-09 14:49:57', 'mkeedy3@symantec.com');
insert into employee (id, first_name, last_name, birthday, email) values (5, 'Boris', 'Turneux', '2020-11-30 19:30:14', 'bturneux4@so-net.ne.jp');
insert into employee (id, first_name, last_name, birthday, email) values (6, 'Sherrie', 'Swaine', '2020-12-23 04:28:06', 'sswaine5@youtu.be');
insert into employee (id, first_name, last_name, birthday, email) values (7, 'Jennica', 'Maycock', '2021-05-17 12:54:08', 'jmaycock6@spotify.com');
insert into employee (id, first_name, last_name, birthday, email) values (8, 'Diannne', 'Chainey', '2020-12-07 02:19:21', 'dchainey7@topsy.com');
insert into employee (id, first_name, last_name, birthday, email) values (9, 'Roseann', 'Chessun', '2021-07-27 03:46:19', 'rchessun8@myspace.com');
insert into employee (id, first_name, last_name, birthday, email) values (10, 'Alyse', 'Ivankovic', '2020-11-05 20:30:54', 'aivankovic9@deliciousdays.com');
insert into employee (id, first_name, last_name, birthday, email) values (11, 'Adolphus', 'Ozanne', '2021-06-28 20:34:06', 'aozannea@techcrunch.com');
insert into employee (id, first_name, last_name, birthday, email) values (12, 'Marley', 'Caunter', '2020-12-23 02:30:18', 'mcaunterb@cpanel.net');
insert into employee (id, first_name, last_name, birthday, email) values (13, 'Essa', 'Phelips', '2020-11-28 00:43:45', 'ephelipsc@reuters.com');
insert into employee (id, first_name, last_name, birthday, email) values (14, 'Jonathan', 'Byrnes', '2020-12-25 20:11:02', 'jbyrnesd@stumbleupon.com');
insert into employee (id, first_name, last_name, birthday, email) values (15, 'Manuel', 'Keighley', '2021-03-20 19:09:49', 'mkeighleye@whitehouse.gov');
insert into employee (id, first_name, last_name, birthday, email) values (16, 'Giacopo', 'De Benedictis', '2021-05-28 04:18:55', 'gdebenedictisf@fda.gov');
insert into employee (id, first_name, last_name, birthday, email) values (17, 'Freemon', 'Tracy', '2021-04-26 13:06:19', 'ftracyg@soundcloud.com');
insert into employee (id, first_name, last_name, birthday, email) values (18, 'Don', 'Allport', '2020-09-13 10:16:03', 'dallporth@google.pl');
insert into employee (id, first_name, last_name, birthday, email) values (19, 'Orelle', 'Tumasian', '2020-09-03 04:05:50', 'otumasiani@artisteer.com');
insert into employee (id, first_name, last_name, birthday, email) values (20, 'Ollie', 'Bastie', '2020-10-19 23:45:54', 'obastiej@msn.com');
insert into employee (id, first_name, last_name, birthday, email) values (21, 'Rustin', 'Dumbar', '2020-11-26 16:44:44', 'rdumbark@arizona.edu');
insert into employee (id, first_name, last_name, birthday, email) values (22, 'Pepito', 'Backwell', '2020-12-29 01:35:12', 'pbackwelll@accuweather.com');
insert into employee (id, first_name, last_name, birthday, email) values (23, 'Florina', 'Maroney', '2021-06-08 16:42:33', 'fmaroneym@huffingtonpost.com');
insert into employee (id, first_name, last_name, birthday, email) values (24, 'Nilson', 'Mc Meekan', '2020-09-15 07:05:22', 'nmcmeekann@mapquest.com');
insert into employee (id, first_name, last_name, birthday, email) values (25, 'Gar', 'Skippon', '2020-11-17 23:52:43', 'gskippono@sourceforge.net');
insert into employee (id, first_name, last_name, birthday, email) values (26, 'Kenon', 'Luckey', '2020-08-29 01:18:40', 'kluckeyp@foxnews.com');
insert into employee (id, first_name, last_name, birthday, email) values (27, 'Hagan', 'Berkely', '2020-09-02 18:20:57', 'hberkelyq@blogs.com');
insert into employee (id, first_name, last_name, birthday, email) values (28, 'Ninon', 'Laurance', '2021-03-17 11:11:18', 'nlaurancer@chicagotribune.com');
insert into employee (id, first_name, last_name, birthday, email) values (29, 'Sascha', 'Spyer', '2021-04-22 05:06:12', 'sspyers@merriam-webster.com');
insert into employee (id, first_name, last_name, birthday, email) values (30, 'Bessy', 'Dassindale', '2021-08-03 17:26:02', 'bdassindalet@constantcontact.com');
insert into employee (id, first_name, last_name, birthday, email) values (31, 'Lewiss', 'Roussel', '2021-06-27 02:20:30', 'lrousselu@i2i.jp');
insert into employee (id, first_name, last_name, birthday, email) values (32, 'Odell', 'Baskerfield', '2021-07-19 02:07:25', 'obaskerfieldv@jigsy.com');
insert into employee (id, first_name, last_name, birthday, email) values (33, 'Rudolph', 'De la Yglesias', '2020-11-11 22:54:49', 'rdelayglesiasw@weibo.com');
insert into employee (id, first_name, last_name, birthday, email) values (34, 'Elana', 'Purchall', '2021-03-03 18:01:42', 'epurchallx@constantcontact.com');
insert into employee (id, first_name, last_name, birthday, email) values (35, 'Lula', 'McGeachey', '2021-08-15 20:05:42', 'lmcgeacheyy@scribd.com');
insert into employee (id, first_name, last_name, birthday, email) values (36, 'El', 'Gutcher', '2021-04-27 14:41:16', 'egutcherz@hc360.com');
insert into employee (id, first_name, last_name, birthday, email) values (37, 'Selig', 'Barfoot', '2021-05-11 15:04:21', 'sbarfoot10@salon.com');
insert into employee (id, first_name, last_name, birthday, email) values (38, 'Siouxie', 'Cameron', '2020-09-28 01:33:22', 'scameron11@intel.com');
insert into employee (id, first_name, last_name, birthday, email) values (39, 'Estrellita', 'Rawsen', '2021-04-12 02:12:17', 'erawsen12@miibeian.gov.cn');
insert into employee (id, first_name, last_name, birthday, email) values (40, 'Chantal', 'Kitteman', '2021-05-26 12:17:37', 'ckitteman13@istockphoto.com');
insert into employee (id, first_name, last_name, birthday, email) values (41, 'Aurore', 'Ivy', '2021-02-07 18:24:19', 'aivy14@time.com');
insert into employee (id, first_name, last_name, birthday, email) values (42, 'Ivor', 'Raden', '2021-03-19 05:14:20', 'iraden15@ehow.com');
insert into employee (id, first_name, last_name, birthday, email) values (43, 'Parnell', 'Purple', '2021-07-02 07:19:15', 'ppurple16@freewebs.com');
insert into employee (id, first_name, last_name, birthday, email) values (44, 'Chickie', 'Alesin', '2021-01-05 04:22:51', 'calesin17@blogspot.com');
insert into employee (id, first_name, last_name, birthday, email) values (45, 'Pavlov', 'Chestnut', '2021-04-04 08:23:22', 'pchestnut18@tripod.com');
insert into employee (id, first_name, last_name, birthday, email) values (46, 'Delphine', 'Gravenor', '2021-06-18 00:53:14', 'dgravenor19@microsoft.com');
insert into employee (id, first_name, last_name, birthday, email) values (47, 'Anabel', 'Pottie', '2021-05-10 17:31:56', 'apottie1a@paginegialle.it');
insert into employee (id, first_name, last_name, birthday, email) values (48, 'Hollis', 'Baythorp', '2021-03-27 00:04:54', 'hbaythorp1b@sourceforge.net');
insert into employee (id, first_name, last_name, birthday, email) values (49, 'Baldwin', 'Eccleshare', '2021-07-14 11:12:20', 'beccleshare1c@kickstarter.com');
insert into employee (id, first_name, last_name, birthday, email) values (50, 'Bill', 'Jedrzejewsky', '2021-03-28 08:55:22', 'bjedrzejewsky1d@fastcompany.com');

```

- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```
UPDATE employee
SET first_name = 'Mayak',
	last_name = 'Gravenor',
	birthday = '2020-11-28 00:43:45',
	email = 'sswaine5@youtu.be'
WHERE id = 2;
```


- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```
DELETE FROM employee WHERE first_name = 'Jennica';
DELETE FROM employee WHERE last_name = 'Raden';
DELETE FROM employee WHERE id = 5;
DELETE FROM employee WHERE birthday = '2021-06-18';
DELETE FROM employee WHERE email = 'apottie1a@paginegialle.it';
```

---

## Ödev 9

- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT city, country
FROM city
INNER JOIN country 
ON city.country_id = country.country_id;
```

- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT payment.payment_id, first_name, last_name
FROM customer
INNER JOIN payment 
ON payment.customer_id = customer.customer_id;
```

- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT rental.rental_id, first_name, last_name
FROM customer
INNER JOIN rental 
ON rental.customer_id = customer.customer_id;
```

---

## Ödev 10

- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

```
SELECT city, country
FROM city
LEFT JOIN country
ON city.country_id = country.country_id;
```

- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

```
SELECT payment_id, first_name, last_name
FROM customer
RIGHT JOIN payment
ON payment.customer_id = customer.customer_id;
```

- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

```
SELECT rental_id, first_name, last_name
FROM customer
FULL JOIN rental
ON customer.customer_id = rental.customer_id;
```

---


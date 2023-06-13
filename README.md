# SQL Ödevleri

## ÖDEV 1

### 1. film  tablosunda bulunan  title  ve  description  sütunlarındaki verileri sıralayınız.

```
 SELECT title, description FROM film;
 ```

### 2. film  tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük  VE  75 ten küçük olma koşullarıyla sıralayınız.

```
 SELECT * FROM film

WHERE length > 60 AND length < 75; 
 ```

### 3. film  tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99  **VE**  replacement_cost 12.99  **VEYA**  28.99 olma koşullarıyla sıralayınız.
```
SELECT * FROM film
WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```
### 4. customer  tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```
SELECT last_name FROM customer
WHERE first_name = 'Mary';
```

### 5. film  tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```
SELECT * FROM film
WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
```

[Ödev 1 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev1)

## ÖDEV 2

### 1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

```
SELECT * FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

### 2. actor  tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```
SELECT first_name, last_name FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```

### 3. film  tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```
SELECT * FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```
[Ödev 2 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev2)

## ÖDEV 3

### 1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```
SELECT country FROM country
WHERE country LIKE 'A%a';
```

### 2. country  tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```
SELECT country FROM country
WHERE country LIKE '_____%n';
```

### 3. film  tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```
SELECT title FROM film
WHERE title ILIKE '%t%t%t%t%';
```

### 4. film  tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```
SELECT * FROM film
WHERE title LIKE 'C%' AND length < 90 AND rental_rate IN (2.99);
```

[Ödev 3 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev3)

## ÖDEV 4

### 1. film  tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```
SELECT DISTINCT replacement_cost FROM film;
```

### 2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```
SELECT COUNT (DISTINCT replacement_cost) FROM film;
```

### 3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```
SELECT COUNT (*) FROM film
WHERE title LIKE 'T%' AND rating = 'G';
```

### 4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```
SELECT COUNT (*) FROM country
WHERE country LIKE '_____';
```

### 5. city  tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

```
SELECT COUNT(city) FROM city
WHERE city ILIKE '%r';
```

[Ödev 4 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev4)

## ÖDEV 5

### 1. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

### 2. film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

```
SELECT * FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
OFFSET 5
LIMIT 5;
```

### 3. customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```
SELECT * FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

[Ödev 5 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev5)

## ÖDEV 6

### 1. film  tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```
SELECT AVG(rental_rate) FROM film;
```

### 2. film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

```
SELECT COUNT(title) FROM film
WHERE title LIKE 'C%';
```

### 3. film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```
SELECT MAX(length) FROM film
WHERE rental_rate = 0.99;
```

### 4. film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```
SELECT COUNT(DISTINCT replacement_cost) FROM film
WHERE length > 150;
```
[Ödev 6 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev6)

## ÖDEV 7

### 1. film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
```

### 2. film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

```
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;
```

### 3. customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

```
SELECT store_id, COUNT(*) FROM customer
GROUP BY store_id;
```

### 4. city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

```
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```

[Ödev 7 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev7)

## ÖDEV 8

### 1. test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```
CREATE TABLE employee (
    id INTEGER,
	name VARCHAR(50),
	birthday DATE,
	email VARCHAR(100)
);
```

### 2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

```
insert into employee (id, name, birthday, email) values (1, 'Myer Veque', '11/23/2022', 'mveque0@marriott.com');
insert into employee (id, name, birthday, email) values (2, 'Billy Warriner', '10/7/2022', 'bwarriner1@discovery.com');
insert into employee (id, name, birthday, email) values (3, 'Berkley Yukhin', '12/18/2022', 'byukhin2@networksolutions.com');
insert into employee (id, name, birthday, email) values (4, 'Hube Borton', '5/12/2023', 'hborton3@chronoengine.com');
insert into employee (id, name, birthday, email) values (5, 'Gil Salterne', '10/29/2022', 'gsalterne4@cbc.ca');
insert into employee (id, name, birthday, email) values (6, 'Jewell Catton', '4/12/2023', 'jcatton5@statcounter.com');
insert into employee (id, name, birthday, email) values (7, 'Loren Hallock', '11/16/2022', 'lhallock6@smugmug.com');
insert into employee (id, name, birthday, email) values (8, 'Concordia Bulfoy', '8/13/2022', 'cbulfoy7@tmall.com');
insert into employee (id, name, birthday, email) values (9, 'Pearle Sikorsky', '7/9/2022', 'psikorsky8@forbes.com');
insert into employee (id, name, birthday, email) values (10, 'Wilburt Gerardin', '5/13/2023', 'wgerardin9@is.gd');
insert into employee (id, name, birthday, email) values (11, 'Adrian Lowery', '5/12/2023', 'alowerya@java.com');
insert into employee (id, name, birthday, email) values (12, 'Robin Deere', '1/1/2023', 'rdeereb@simplemachines.org');
insert into employee (id, name, birthday, email) values (13, 'Justinian Dysert', '6/23/2022', 'jdysertc@naver.com');
insert into employee (id, name, birthday, email) values (14, 'Papageno Chubb', '5/19/2023', 'pchubbd@nyu.edu');
insert into employee (id, name, birthday, email) values (15, 'Annmaria Lewing', '12/1/2022', 'alewinge@twitpic.com');
insert into employee (id, name, birthday, email) values (16, 'Shepperd Rhodus', '3/13/2023', 'srhodusf@weebly.com');
insert into employee (id, name, birthday, email) values (17, 'Loy Cressar', '10/14/2022', 'lcressarg@edublogs.org');
insert into employee (id, name, birthday, email) values (18, 'Felisha Lammenga', '8/20/2022', 'flammengah@dyndns.org');
insert into employee (id, name, birthday, email) values (19, 'Prisca Ferrini', '1/26/2023', 'pferrinii@ucsd.edu');
insert into employee (id, name, birthday, email) values (20, 'Ky Hinnerk', '8/27/2022', 'khinnerkj@devhub.com');
insert into employee (id, name, birthday, email) values (21, 'Mose Gowland', '2/7/2023', 'mgowlandk@163.com');
insert into employee (id, name, birthday, email) values (22, 'Guenna Boatwright', '4/20/2023', 'gboatwrightl@addthis.com');
insert into employee (id, name, birthday, email) values (23, 'Madlen Gatch', '2/6/2023', 'mgatchm@liveinternet.ru');
insert into employee (id, name, birthday, email) values (24, 'Catherina Benedick', '12/12/2022', 'cbenedickn@icio.us');
insert into employee (id, name, birthday, email) values (25, 'Craggy McShee', '11/29/2022', 'cmcsheeo@unblog.fr');
insert into employee (id, name, birthday, email) values (26, 'Grissel Brandacci', '5/4/2023', 'gbrandaccip@statcounter.com');
insert into employee (id, name, birthday, email) values (27, 'Aggi Vater', '11/16/2022', 'avaterq@yellowbook.com');
insert into employee (id, name, birthday, email) values (28, 'Jannel Sucre', '8/3/2022', 'jsucrer@baidu.com');
insert into employee (id, name, birthday, email) values (29, 'Jorey Scurlock', '4/20/2023', 'jscurlocks@nifty.com');
insert into employee (id, name, birthday, email) values (30, 'Terence Trethowan', '3/31/2023', 'ttrethowant@apple.com');
insert into employee (id, name, birthday, email) values (31, 'Jessey Kempshall', '3/18/2023', 'jkempshallu@salon.com');
insert into employee (id, name, birthday, email) values (32, 'Carmela Saltern', '1/21/2023', 'csalternv@jigsy.com');
insert into employee (id, name, birthday, email) values (33, 'Archambault Mintram', '10/16/2022', 'amintramw@squidoo.com');
insert into employee (id, name, birthday, email) values (34, 'Hammad Puddle', '8/21/2022', 'hpuddlex@spotify.com');
insert into employee (id, name, birthday, email) values (35, 'Chaddie Byrd', '7/20/2022', 'cbyrdy@indiegogo.com');
insert into employee (id, name, birthday, email) values (36, 'Justina Handrek', '8/16/2022', 'jhandrekz@tmall.com');
insert into employee (id, name, birthday, email) values (37, 'Ysabel Mungin', '4/16/2023', 'ymungin10@marketwatch.com');
insert into employee (id, name, birthday, email) values (38, 'Aurora Merryfield', '2/24/2023', 'amerryfield11@epa.gov');
insert into employee (id, name, birthday, email) values (39, 'Valentine Mucklo', '12/23/2022', 'vmucklo12@icio.us');
insert into employee (id, name, birthday, email) values (40, 'Rod Thundercliffe', '1/15/2023', 'rthundercliffe13@ameblo.jp');
insert into employee (id, name, birthday, email) values (41, 'Jeffie Skally', '10/15/2022', 'jskally14@seattletimes.com');
insert into employee (id, name, birthday, email) values (42, 'Derby Eul', '10/22/2022', 'deul15@yolasite.com');
insert into employee (id, name, birthday, email) values (43, 'Sibylla Kmieciak', '7/2/2022', 'skmieciak16@oaic.gov.au');
insert into employee (id, name, birthday, email) values (44, 'Eddy McClelland', '10/31/2022', 'emcclelland17@answers.com');
insert into employee (id, name, birthday, email) values (45, 'Will Flohard', '4/3/2023', 'wflohard18@cam.ac.uk');
insert into employee (id, name, birthday, email) values (46, 'Lana Rohan', '12/5/2022', 'lrohan19@ycombinator.com');
insert into employee (id, name, birthday, email) values (47, 'Desmund Petcher', '6/17/2022', 'dpetcher1a@amazonaws.com');
insert into employee (id, name, birthday, email) values (48, 'Darcey Creus', '4/20/2023', 'dcreus1b@indiatimes.com');
insert into employee (id, name, birthday, email) values (49, 'Xena Beckett', '6/25/2022', 'xbeckett1c@nifty.com');
insert into employee (id, name, birthday, email) values (50, 'Marijo Ramlot', '5/17/2023', 'mramlot1d@so-net.ne.jp');
```

### 3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```
UPDATE employee
SET id = 51, name = 'Jane Doe', birthday = '1996/04/30'
WHERE id = 1;
```

```
UPDATE employee
SET id = 52, name = 'Robert Tart', birthday = '1954/02/02'
WHERE name = 'Darcey Creus';
```

```
UPDATE employee
SET id = 53, name = 'Bernard Shaw'
WHERE email = 'gsalterne4@cbc.ca';
```

```
UPDATE employee
SET email = 'ysabel@mungin.com'
WHERE name = 'Ysabel Mungin';
```

```
UPDATE employee
SET name = 'Phill Pearl', birthday = '1999/01/10'
WHERE id = 40;
```
### 4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```
DELETE FROM employee
WHERE birthday = '2022-10-07';
```

```
DELETE FROM employee
WHERE id = 37;
```

```
DELETE FROM employee
WHERE name = 'Sibylla Kmieciak';
```

```
DELETE FROM employee
WHERE email = 'xbeckett1c@nifty.com';
```

```
DELETE FROM employee
WHERE name = 'Aggi Vater';
```
[Ödev 8 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev8)

### ÖDEV 9

## 1.  city  tablosu ile  country  tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT city, country FROM city
JOIN country ON city.country_id = country.country_id;
```

## 2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT payment_id, first_name, last_name FROM customer
JOIN payment ON customer.customer_id = payment.customer_id;
```

## 3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```
SELECT rental_id, first_name, last_name FROM customer
JOIN rental ON rental.customer_id = customer.customer_id;
```

[Ödev 9 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev9)

## ÖDEV 10

### 1. city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

```
SELECT city.city, country.country FROM city
LEFT JOIN country ON city.country_id = country.country_id;
```

### 2. customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

```
SELECT customer.first_name, customer.last_name, payment.payment_id FROM customer
RIGHT JOIN payment ON customer.customer_id = payment.customer_id;
```

### 3. customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

```
SELECT customer.first_name, customer.last_name, rental.rental_id FROM customer
FULL JOIN rental ON customer.customer_id = rental.customer_id;
```

[Ödev 10 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev10)

## ÖDEV 11

### 1. actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

```
(SELECT first_name FROM actor)
UNION
(SELECT first_name FROM customer);
```

### 2. actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

```
(SELECT first_name FROM actor)
INTERSECT
(SELECT first_name FROM customer);
```

### 3. actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```
(SELECT first_name FROM actor)
EXCEPT
(SELECT first_name FROM customer);
```

### 4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

```
(SELECT first_name FROM actor)
UNION ALL
(SELECT first_name FROM customer);

(SELECT first_name FROM actor)
INTERSECT ALL
(SELECT first_name FROM customer);

(SELECT first_name FROM actor)
EXCEPT ALL
(SELECT first_name FROM customer);
```

[Ödev 11 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev11)

## ÖDEV 12

### 1. film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

```
SELECT COUNT(*) FROM film
WHERE length > (SELECT AVG(length) FROM film);
```

### 2. film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

```
SELECT COUNT(*) FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);
```

### 3. film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

```
SELECT * FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)
AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);
```

### 4. payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

```
SELECT * FROM payment
WHERE amount = (SELECT MAX(amount) FROM payment);
```

[Ödev 12 Patika Linki](https://academy.patika.dev/tr/courses/sql/Odev12)

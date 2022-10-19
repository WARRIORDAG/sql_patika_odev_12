# sql_patika_odev_12   www.patika.dev
sql_patika_odev_12
--answer 1
SELECT COUNT(length) FROM film
WHERE length>
(
	SELECT AVG(length) FROM film 

);

-- answer 2  film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

SELECT COUNT(rental_rate) FROM film
WHERE rental_rate = ANY
(
	SELECT MAX(rental_rate) FROM film 

);

--ANSWER 3  film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
SELECT COUNT(*) FROM film
WHERE rental_rate = 
(SELECT MIN(rental_rate) FROM film) AND
replacement_cost = 
(SELECT MIN(replacement_cost) FROM film);


-- answer 4  payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
SELECT first_name, amount FROM payment
INNER JOIN customer ON payment.customer_id = customer.customer_id
ORDER BY amount DESC


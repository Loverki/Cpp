# Cpp
Code for leetcode


--CREATE TABLE BOOK_SALES( 
--   sale_id INT PRIMARY KEY,
--   book_title VARCHAR(15),
--   author VARCHAR(15),
--   category VARCHAR(15),
--   price NUMBER(10),
--   quantity NUMBER(5),
--   customer_name VARCHAR(20),
--   city VARCHAR(10),
--   sale_date DATE,
--   payment_mode VARCHAR(15)
--);

INSERT INTO BOOK_SALES VALUES(1, 'Project Hail', 'A. Weir', 'Fiction', 520, 1, 'Karan Malhotra', 'Ahmedabad', TO_DATE('2025-08-01', 'YYYY-MM-DD'), 'Credit Card');
INSERT INTO BOOK_SALES VALUES(2, 'Brave New', 'A. Huxley', 'Fiction', 450, 2, 'Sneha Rao', 'Jaipur', TO_DATE('2025-08-02', 'YYYY-MM-DD'), 'Cash');
INSERT INTO BOOK_SALES VALUES(3, 'Foundation', 'I. Asimov', 'Science', 620, 1, 'Aditya Roy', 'Indore', TO_DATE('2025-08-03', 'YYYY-MM-DD'), 'UPI');
INSERT INTO BOOK_SALES VALUES(4, 'Cosmos', 'C. Sagan', 'Science', 790, 2, 'Mira Joshi', 'Surat', TO_DATE('2025-08-04', 'YYYY-MM-DD'), 'Debit Card');
INSERT INTO BOOK_SALES VALUES(5, 'Algo+Design', 'T. Cormen', 'Textbook', 1000, 1, 'Harshita Pillai', 'Bhopal', TO_DATE('2025-08-05', 'YYYY-MM-DD'), 'Credit Card');
INSERT INTO BOOK_SALES VALUES(6, 'Refactoring', 'M. Fowler', 'Textbook', 880, 1, 'Rajat Bansal', 'Nagpur', TO_DATE('2025-08-06', 'YYYY-MM-DD'), 'Cash');
INSERT INTO BOOK_SALES VALUES(7, 'Siddhartha', 'H. Hesse', 'Novel', 320, 3, 'Lavanya Singh', 'Lucknow', TO_DATE('2025-08-07', 'YYYY-MM-DD'), 'UPI');
INSERT INTO BOOK_SALES VALUES(8, 'Kafka Shore', 'H. Murakami', 'Novel', 460, 2, 'Dev Mehra', 'Delhi', TO_DATE('2025-08-08', 'YYYY-MM-DD'), 'Credit Card');
INSERT INTO BOOK_SALES VALUES(9, 'Contact', 'C. Sagan', 'Science', 640, 1, 'Rina Fernandes', 'Mumbai', TO_DATE('2025-08-09', 'YYYY-MM-DD'), 'UPI');
INSERT INTO BOOK_SALES VALUES(10, 'Catcher Rye', 'J.D. Salinger', 'Fiction', 390, 2, 'Siddharth Jain', 'Chandigarh', TO_DATE('2025-08-10', 'YYYY-MM-DD'), 'Debit Card');
INSERT INTO BOOK_SALES VALUES(11, 'Logic Design', 'M. Morris', 'Textbook', 990, 1, 'Trisha Kulkarni', 'Pune', TO_DATE('2025-08-11', 'YYYY-MM-DD'), 'Cash');
INSERT INTO BOOK_SALES VALUES(12, 'Beloved', 'T. Morrison', 'Novel', 420, 2, 'Vikram Malani', 'Bangalore', TO_DATE('2025-08-12', 'YYYY-MM-DD'), 'UPI');
INSERT INTO BOOK_SALES VALUES(13, 'Twilight', 'S. Meyer', 'Fiction', 570, 4, 'Zara Sheikh', 'Hyderabad', TO_DATE('2025-08-13', 'YYYY-MM-DD'), 'Credit Card');
INSERT INTO BOOK_SALES VALUES(14, 'PhysicsFund', 'D. Halliday', 'Textbook', 1100, 1, 'Nitesh Rawat', 'Kolkata', TO_DATE('2025-08-14', 'YYYY-MM-DD'), 'Cash');
INSERT INTO BOOK_SALES VALUES(15, 'Dracula', 'B. Stoker', 'Novel', 490, 2, 'Alisha Thomas', 'Delhi', TO_DATE('2025-08-15', 'YYYY-MM-DD'), 'UPI');


--UPDATE BOOK_SALES
--SET price = price * 1.10
--WHERE category = 'Textbook';

--DELETE BOOK_SALES
--WHERE city = 'DemoCity';
----
--CREATE TABLE BOOK_SALES_1( 
--   sale_id INT PRIMARY KEY,
--   book_title VARCHAR(15),
--   author VARCHAR(15),
--   category VARCHAR(15),
--   price NUMBER(10),
--   quantity NUMBER(5),
--   customer_name VARCHAR(20),
--   city VARCHAR(10),
--   sale_date DATE,
--   payment_mode VARCHAR(15)
--);

--MERGE INTO BOOK_SALES_1 tgt
--USING BOOK_SALES src
--ON (tgt.customer_name = src.customer_name)
--WHEN MATCHED THEN
--    UPDATE SET tgt.city = src.city
--WHEN NOT MATCHED THEN
--    INSERT (
--        sale_id, book_title, author, category,
--        price, quantity, customer_name, city,
--        sale_date, payment_mode
--    )
--    VALUES (
--        src.sale_id, src.book_title, src.author, src.category,
--        src.price, src.quantity, src.customer_name, src.city,
--        src.sale_date, src.payment_mode
--    );
--
--SELECT * FROM BOOK_SALES
--WHERE category = 'Fiction' AND price > 500;

--SELECT * FROM BOOK_SALES
--WHERE quantity BETWEEN 2 AND 5;

--SELECT * FROM BOOK_SALES
--WHERE city IN('Hyderabad','Chennai','Bamgalore');

--SELECT * FROM BOOK_SALES
--WHERE book_title LIKE 'Data%';

--SELECT DISTINCT category
--FROM BOOK_SALES;

--SELECT sale_id,book_title,city,price FROM BOOK_SALES
--ORDER BY price DESC;

--SELECT sale_id,book_title,category,price FROM BOOK_SALES
--ORDER BY category ASC,price DESC;

--SELECT COUNT(*) AS Total_sales 
--FROM BOOK_SALES;

--SELECT 
--MIN(price) AS Lowest_price,
--MAX(price) AS Highest_price,
--AVG(price) AS Average_price
--FROM BOOK_SALES;


--SELECT SUM(quantity) AS total_quantity
--FROM BOOK_SALES;

--SELECT category, COUNT(*) AS total_quantity
--FROM BOOK_SALES
--GROUP BY category;

--SELECT city, SUM(price*quantity) AS total_revenue
--FROM BOOK_SALES
--GROUP BY city;

--
--SELECT category, SUM(quantity) AS quantity
--FROM BOOK_SALES
--GROUP BY category
--HAVING SUM(quantity) > 8;
--
--SELECT city, AVG(price) AS avg_price
--FROM BOOK_SALES
--GROUP BY city
--HAVING AVG(price) > 400;

SELECT payment_mode, MAX(price) AS Max_price
FROM BOOK_SALES
GROUP BY payment_mode
HAVING MAX(price) >= 800;


--SELECT * FROM BOOK_SALES




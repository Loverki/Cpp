# Cpp
Code for leetcode


--CREATE TABLE MEMBERS( 
--   member_id INT PRIMARY KEY,
--   full_name VARCHAR(15),
--   gender VARCHAR2(1),
--   age NUMBER(4),
--   city VARCHAR(10),
--   membership_type VARCHAR2(8),
--   join_date DATE,
--   expiry_date DATE,
--   fee_paid NUMBER(20),
--   discount VARCHAR(10),
--   workouts_per_week NUMBER(1),
--   trainer_name VARCHAR(15)
--);


--INSERT INTO MEMBERS VALUES (1, 'Amit Sharma', 'M', 28, 'Delhi', 'Annual', TO_DATE('2024-01-10','YYYY-MM-DD'), TO_DATE('2025-01-10','YYYY-MM-DD'), 15000, '10%', 5, 'Ravi Kumar');
--INSERT INTO MEMBERS VALUES (2, 'Neha Verma', 'F', 24, 'Mumbai', 'Monthly', TO_DATE('2025-08-01','YYYY-MM-DD'), TO_DATE('2025-08-31','YYYY-MM-DD'), 1500, '0%', 3, 'Sneha Patil');
--INSERT INTO MEMBERS VALUES (3, 'Rahul Mehta', 'M', 35, 'Bangalore', 'Quarterly', TO_DATE('2025-07-15','YYYY-MM-DD'), TO_DATE('2025-10-15','YYYY-MM-DD'), 4000, '5%', 4, 'Vikram Rao');
--INSERT INTO MEMBERS VALUES (4, 'Priya Desai', 'F', 30, 'Ahmedabad', 'Annual', TO_DATE('2024-12-01','YYYY-MM-DD'), TO_DATE('2025-12-01','YYYY-MM-DD'), 14000, '10%', 6, 'Meena Shah');
--INSERT INTO MEMBERS VALUES (5, 'Karan Singh', 'M', 27, 'Jaipur', 'Monthly', TO_DATE('2025-08-01','YYYY-MM-DD'), TO_DATE('2025-08-31','YYYY-MM-DD'), 1300, '0%', 2, 'Ajay Rana');
--INSERT INTO MEMBERS VALUES (6, 'Anjali Nair', 'F', 22, 'Kochi', 'Quarterly', TO_DATE('2025-06-25','YYYY-MM-DD'), TO_DATE('2025-09-25','YYYY-MM-DD'), 4200, '10%', 4, 'Divya Menon');
--INSERT INTO MEMBERS VALUES (7, 'Suresh Reddy', 'M', 40, 'Hyderabad', 'Annual', TO_DATE('2025-04-10','YYYY-MM-DD'), TO_DATE('2026-04-10','YYYY-MM-DD'), 16000, '15%', 5, 'Rajesh Iyer');
--INSERT INTO MEMBERS VALUES (8, 'Megha Kapoor', 'F', 29, 'Chandigarh', 'Monthly', TO_DATE('2025-08-10','YYYY-MM-DD'), TO_DATE('2025-09-10','YYYY-MM-DD'), 1600, '5%', 3, 'Pooja Singh');
--INSERT INTO MEMBERS VALUES (9, 'Arjun Yadav', 'M', 26, 'Lucknow', 'Quarterly', TO_DATE('2025-05-01','YYYY-MM-DD'), TO_DATE('2025-08-01','YYYY-MM-DD'), 3900, '10%', 4, 'Kunal Tiwari');
--INSERT INTO MEMBERS VALUES (10, 'Isha Bhatia', 'F', 31, 'Pune', 'Annual', TO_DATE('2025-08-01','YYYY-MM-DD'), TO_DATE('2026-08-01','YYYY-MM-DD'), 15500, '12%', 6, 'Namrata Rao');
--INSERT INTO MEMBERS VALUES (11, 'Rohan Joshi', 'M', 33, 'Nagpur', 'Monthly', TO_DATE('2025-08-01','YYYY-MM-DD'), TO_DATE('2025-08-31','YYYY-MM-DD'), 1200, '0%', 2, 'Dev Mishra');
--INSERT INTO MEMBERS VALUES (12, 'Sneha Pillai', 'F', 25, 'Thiruvan', 'Quarterly', TO_DATE('2025-07-05','YYYY-MM-DD'), TO_DATE('2025-10-05','YYYY-MM-DD'), 4500, '10%', 4, 'Hari Nair');
--INSERT INTO MEMBERS VALUES (13, 'Vikrant Chauhan', 'M', 38, 'Indore', 'Annual', TO_DATE('2024-09-01','YYYY-MM-DD'), TO_DATE('2025-09-01','YYYY-MM-DD'), 14500, '10%', 5, 'Prakash Jain');
--INSERT INTO MEMBERS VALUES (14, 'Pallavi Sinha', 'F', 32, 'Patna', 'Monthly', TO_DATE('2025-08-01','YYYY-MM-DD'), TO_DATE('2025-08-31','YYYY-MM-DD'), 1300, '5%', 3, 'Manoj Das');
--INSERT INTO MEMBERS VALUES (15, 'Tarun Roy', 'M', 29, 'Kolkata', 'Quarterly', TO_DATE('2025-06-10','YYYY-MM-DD'), TO_DATE('2025-09-10','YYYY-MM-DD'), 4000, '10%', 4, 'Rekha Ghosh');



--
--UPDATE MEMBERS
--SET fee_paid = fee_paid * 1.05
--WHERE membership_type = 'Annual';

--DELETE MEMBERS
--WHERE membership_type = 'Monthly' AND fee_paid < 1000;

--CREATE TABLE STG_MEMBERS(
--   member_id INT,
--   city VARCHAR(20),
--   trainer_name VARCHAR(20)
--
--); 


--MERGE INTO MEMBERS a
--USING STG_MEMBERS a1
--ON (a.member_id = a1.member_id)
--WHEN MATCHED THEN
--    UPDATE SET
--        a.city = a1.city,
--        a.trainer_name = a1.trainer_name
--WHEN NOT MATCHED THEN
--INSERT (
--        member_id, full_name, gender, age, city,
--        membership_type, join_date, expiry_date,
--        fee_paid, discount, workouts_per_week, trainer_name
--    )
--    VALUES (
--        a1.member_id, 'DEFAULT', 'N', 0, a1.city,
--        'DEFAULT', SYSDATE, ADD_MONTHS(SYSDATE, 1),
--        0, '0', 0, a1.trainer_name
--    );
--    
--INSERT INTO STG_MEMBERS VALUES (3, 'Delhi', 'New Trainer');
--INSERT INTO STG_MEMBERS VALUES (20, 'Goa', 'Kiran Rao');  


--SELECT * FROM MEMBERS
--WHERE city = 'Hyderabad' AND membership_type = 'Annual'

--SELECT * FROM MEMBERS
--WHERE age BETWEEN 20 AND 30

--SELECT * FROM MEMBERS
--WHERE city IN('Hyderabad','Chennai','Delhi');


--SELECT * FROM MEMBERS
--WHERE full_name LIKE 'A%';

--SELECT DISTINCT membership_type
--FROM MEMBERS;
--
--SELECT member_id,full_name,gender,fee_paid FROM MEMBERS 
--ORDER BY fee_paid DESC;

--SELECT member_id,full_name,age,city FROM MEMBERS 
--ORDER BY city ASC, age DESC;
--
--SELECT COUNT(*) AS Total_members 
--FROM MEMBERS

--SELECT 
--MIN(fee_paid) AS Minimum_fee_paid,
--MAX(fee_paid) AS Maximum_fee_paid,
--AVG(fee_paid) AS Average_fee_paid
--FROM MEMBERS
--WHERE fee_paid > 0;

--SELECT SUM(TO_NUMBER(REPLACE(discount, '%', '')))  Total_discountAS
--FROM MEMBERS

--SELECT city, COUNT(*) AS total_members
--FROM MEMBERS
--GROUP BY city;

--SELECT membership_type, AVG(fee_paid) AS Average_fee_paid
--FROM MEMBERS
--GROUP BY membership_type;

--SELECT trainer_name, SUM(workouts_per_week) AS total_workout
--FROM MEMBERS
--GROUP BY trainer_name;

--SELECT city, COUNT(*) AS best_city
--FROM MEMBERS
--GROUP BY city
--HAVING COUNT(*) > 0;

--SELECT membership_type, AVG(fee_paid) AS paid_amount
--FROM MEMBERS
--GROUP BY membership_type
--HAVING AVG(fee_paid) > 3000;

--SELECT trainer_name, SUM(workouts_per_week) AS total_workout
--FROM MEMBERS
--GROUP BY trainer_name
--HAVING SUM(workouts_per_week) > 4;

--SELECT * FROM MEMBERS


# For Ordering in ascending order
ORDER BY column_name ASC;
Example:
SELECT * FROM users WHERE gender = 'MALE' AND salary > 60000 ORDER BY salary  ASC;

# For Ordering in descending order
ORDER BY column_name DESC;  
Example:
SELECT * FROM users WHERE gender = 'MALE' AND salary > 60000 ORDER BY salary DESC;

# to order by multiple columns
ORDER BY column1 ASC, column2 DESC; 

# Example:
SELECT * FROM users WHERE gender = 'MALE' AND salary > 60000 ORDER BY salary DESC, age ASC;

# To Limit the number of records returned
LIMIT number;       
Example:        
SELECT * FROM users WHERE gender = 'MALE' AND salary > 60000 ORDER BY salary DESC LIMIT 5;
         or 
SELECT * FROM users WHERE gender = 'MALE' AND salary > 60000 LIMIT 5;
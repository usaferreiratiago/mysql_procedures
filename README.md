# mysql_procedures

DELIMITER $$

DROP PROCEDURE IF EXISTS simple_loop$$

CREATE PROCEDURE simple_loop()
BEGIN 
    DECLARE counter INT DEFAULT();

    my_simple_loop: LOOP
	SET counter=counter+1;
	IF counter=10 THEN
		LEAVE my_imple_loop;
	END IF;
    END LOOP my_simple_loop;
    SELECT 'I can count to 10';
DELIMITER;


___________________________________________________


DELIMITER $$

DROP PROCEDURE IF EXISTS customer_sales$$

CREATE PROCEDURE customer_sales(in_customer_id INT)
	READS SQL DATA
BEGIN 
    DECLARE total_sales NUMERIC(8,2);

    SELECT SUM(sale_value)
	INTO total_sales
	FROM sales
	WHERE customer_id=in_customer_id;
	
	SELECT CONCAT('Total sales for', in_customer_id'is',total_sales);
	END;

DELIMITER;

_____________________________________________________




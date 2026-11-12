```Mysql
DELIMITER $$ 
CREATE
	TRIGGER my_trigger BEFORE INSERT
	ON employee
	FOR EACH ROW BEGING
		INSERT INTO trigger_test values('added new employee');
	END$$;
DELIMITER;



```
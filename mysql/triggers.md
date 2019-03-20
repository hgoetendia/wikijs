<!-- TITLE: Triggers -->
<!-- SUBTITLE: A quick summary of Triggers -->

# Show triggers


```text
MariaDB [accounts]> SHOW triggers;

MariaDB [accounts]> 

```


# After update


```mysql
DELIMITER //
CREATE TRIGGER `UPDATE_SUMMARY_FINISHED_STATUS_MT` AFTER UPDATE ON `mt` 
FOR EACH ROW 

BEGIN

DECLARE v_sent_to varchar (256);

IF NEW.status <> OLD.status THEN

    IF NEW.sent_to_smpp IS NULL THEN
        IF NEW.sms_target IS NULL THEN
            set v_sent_to := 'DESCONOCIDO';
        ELSE
            set v_sent_to := NEW.sms_target;
        END IF; 
    ELSE
       set v_sent_to := NEW.sent_to_smpp;
    END IF;
    
    IF NEW.status = 2 THEN
        INSERT INTO summary_finished_status (id_user, f_actualization, sent_to, STATUS_DELIVERED) VALUES (NEW.id_user, COALESCE(NEW.dispatch_time, now()) , v_sent_to  ,1) ON DUPLICATE KEY UPDATE STATUS_DELIVERED=STATUS_DELIVERED+1;
        REPLACE INTO mt_current_month  SELECT * FROM mt WHERE id_mt=NEW.id_mt;
        
    ELSEIF  NEW.status = 7 THEN
        INSERT INTO summary_finished_status (id_user, f_actualization, sent_to, STATUS_GENERIC_FAILED) VALUES (NEW.id_user, COALESCE(NEW.dispatch_time, now()), v_sent_to ,1) ON DUPLICATE KEY UPDATE STATUS_GENERIC_FAILED=STATUS_GENERIC_FAILED+1;
        REPLACE INTO mt_current_month  SELECT * FROM mt WHERE id_mt=NEW.id_mt;

    ELSEIF NEW.status = 9 THEN
        INSERT INTO summary_finished_status (id_user, f_actualization, sent_to, STATUS_CANCELLED) VALUES (NEW.id_user, COALESCE(NEW.dispatch_time, now()), v_sent_to ,1) ON DUPLICATE KEY UPDATE STATUS_CANCELLED=STATUS_CANCELLED+1;
        REPLACE INTO mt_current_month  SELECT * FROM mt WHERE id_mt=NEW.id_mt;


    ELSEIF NEW.status = 11 THEN
        INSERT INTO summary_finished_status (id_user, f_actualization, sent_to, STATUS_EXPIRED) VALUES (NEW.id_user, COALESCE(NEW.dispatch_time, now()), v_sent_to ,1) ON DUPLICATE KEY UPDATE STATUS_EXPIRED=STATUS_EXPIRED+1;
        REPLACE INTO mt_current_month  SELECT * FROM mt WHERE id_mt=NEW.id_mt;

    ELSEIF NEW.status = 12 THEN
        INSERT INTO summary_finished_status (id_user, f_actualization, sent_to, STATUS_BADMESSAGE) VALUES (NEW.id_user, COALESCE(NEW.dispatch_time, now()), v_sent_to ,1) ON DUPLICATE KEY UPDATE STATUS_BADMESSAGE=STATUS_BADMESSAGE+1;
        REPLACE INTO mt_current_month  SELECT * FROM mt WHERE id_mt=NEW.id_mt;
    END IF;

END IF;
END//

DELIMITER ;
```

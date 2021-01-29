# mysql-trigger
mysql-trigger


    DELIMITER $$
    CREATE TRIGGER salons_trigger
    BEFORE INSERT ON salon
    FOR EACH ROW BEGIN
        SET NEW.salon_id = IFNULL((SELECT MAX(salon_id) + 1 FROM salon WHERE owner = NEW.owner), 1);
    END $$
    DELIMITER ;

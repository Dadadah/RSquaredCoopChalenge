### Challenge

#### Part one, MySQL
```
DROP TABLE `ORDER`;
DROP TABLE `BUYER`;

CREATE TABLE `ORDER` (ID INT PRIMARY KEY, PRODUCT_ID INT NOT NULL, BUYER_ID INT NOT NULL, ORDER_VOLUME INT NOT NULL, ORDER_TOTAL_COST FLOAT NOT NULL);
CREATE TABLE `BUYER` (ID INT PRIMARY KEY, NAME VARCHAR(30) NOT NULL);
ALTER TABLE `ORDER` ADD CONSTRAINT `ORDER_BUYER_ID_FK` FOREIGN KEY (BUYER_ID) REFERENCES BUYER(ID);

INSERT INTO `ORDER` VALUES(1, 2, 3, 10, 100);
INSERT INTO `ORDER` VALUES(2, 3, 2, 35, 235);
INSERT INTO `ORDER` VALUES(3, 4, 5, 15, 30);
INSERT INTO `ORDER` VALUES(4, 3, 4, 20, 45);
INSERT INTO `ORDER` VALUES(5, 1, 3, 5, 5.5);
INSERT INTO `ORDER` VALUES(6, 7, 1, 65, 475);
INSERT INTO `ORDER` VALUES(7, 6, 2, 30, 35);
INSERT INTO `ORDER` VALUES(8, 7, 3, 15, 25);
INSERT INTO `ORDER` VALUES(9, 1, 5, 10, 150);
INSERT INTO `ORDER` VALUES(10, 2, 4, 25, 20);

INSERT INTO `BUYER` VALUES(1, 'John');
INSERT INTO `BUYER` VALUES(2, 'Sarah');
INSERT INTO `BUYER` VALUES(3, 'Marcus');
INSERT INTO `BUYER` VALUES(4, 'Janay');
INSERT INTO `BUYER` VALUES(5, 'Franco');

SELECT b.NAME, COUNT(o.ID) 'NUM_ORDERS', SUM(o.ORDER_VOLUME) 'TOTAL_VOLUME', FORMAT(SUM(o.ORDER_TOTAL_COST), 2) 'TOTAL_SPENT'
FROM `BUYER` b
JOIN `ORDER` o ON b.ID = o.BUYER_ID
GROUP BY b.NAME
ORDER BY b.ID;
```

*A note on convention - I was taught that when making tables to always name them singular. This is just a convention I follow and can be easily changed.*

#### Part two, mass find/replace

There are two ways I would approach this, depending on what was available to me and what is acceptable.
- First, most text editors now come with a directory file find and replace. This is the easiest way to do this operation, however the text editor may not be available.

- If this option were not available, I would write a bash script to search the file tree and replace the lines. For example:
```
#!/bin/bash

```

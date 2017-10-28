# class-activity
work in class
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 2
Server version: 10.1.21-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| test               |
+--------------------+
2 rows in set (0.00 sec)

MariaDB [(none)]> use test;
Database changed
MariaDB [test]> CREATE TABLE IF NOT EXISTS `countries` (  `COUNTRY_ID` varchar(2) NOT NULL,  `COUNTRY_NAME` varchar(40) DEFAULT NULL,  `REGION_ID` decimal(10,0) DEFAULT NULL,  PRIMARY KEY (`COUNTRY_ID`),  KEY `COUNTR_REG_FK` (`REGION_ID`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.01 sec)

MariaDB [test]> INSERT INTO `countries` (`COUNTRY_ID`, `COUNTRY_NAME`, `REGION_ID`) VALUES('AR', 'Argentina', '2'),('AU', 'Australia', '3'),('BE', 'Belgium', '1'),('BR', 'Brazil', '2'),('CA', 'Canada', '2'),('CH', 'Switzerland', '1'),('CN', 'China', '3'),('DE', 'Germany', '1'),('DK', 'Denmark', '1'),('EG', 'Egypt', '4'),('FR', 'France', '1'),('HK', 'HongKong', '3'),('IL', 'Israel', '4'),('IN', 'India', '3'),('IT', 'Italy', '1'),('JP', 'Japan', '3'),('KW', 'Kuwait', '4'),('MX', 'Mexico', '2'),('NG', 'Nigeria', '4'),('NL', 'Netherlands', '1'),('SG', 'Singapore', '3'),('UK', 'United Kingdom', '1'),('US', 'United States of America', '2'),('ZM', 'Zambia', '4'),('ZW', 'Zimbabwe', '4');
Query OK, 25 rows affected (0.00 sec)
Records: 25  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `departments` (  `DEPARTMENT_ID` decimal(4,0) NOT NULL DEFAULT '0',  `DEPARTMENT_NAME` varchar(30) NOT NULL,  `MANAGER_ID` decimal(6,0) DEFAULT NULL,  `LOCATION_ID` decimal(4,0) DEFAULT NULL,  PRIMARY KEY (`DEPARTMENT_ID`),  KEY `DEPT_MGR_FK` (`MANAGER_ID`),  KEY `DEPT_LOCATION_IX` (`LOCATION_ID`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.01 sec)

MariaDB [test]> INSERT INTO `departments` (`DEPARTMENT_ID`, `DEPARTMENT_NAME`, `MANAGER_ID`, `LOCATION_ID`) VALUES('10', 'Administration', '200', '1700'),('20', 'Marketing', '201', '1800'),('30', 'Purchasing', '114', '1700'),('40', 'Human Resources', '203', '2400'),('50', 'Shipping', '121', '1500'),('60', 'IT', '103', '1400'),('70', 'Public Relations', '204', '2700'),('80', 'Sales', '145', '2500'),('90', 'Executive', '100', '1700'),('100', 'Finance', '108', '1700'),('110', 'Accounting', '205', '1700'),('120', 'Treasury', '0', '1700'),('130', 'Corporate Tax', '0', '1700'),('140', 'Control And Credit', '0', '1700'),('150', 'Shareholder Services', '0', '1700'),('160', 'Benefits', '0', '1700'),('170', 'Manufacturing', '0', '1700'),('180', 'Construction', '0', '1700'),('190', 'Contracting', '0', '1700'),('200', 'Operations', '0', '1700'),('210', 'IT Support', '0', '1700'),('220', 'NOC', '0', '1700'),('230', 'IT Helpdesk', '0', '1700'),('240', 'Government Sales', '0', '1700'),('250', 'Retail Sales', '0', '1700'),('260', 'Recruiting', '0', '1700'),('270', 'Payroll', '0', '1700');
Query OK, 27 rows affected (0.00 sec)
Records: 27  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `employees` (  `EMPLOYEE_ID` decimal(6,0) NOT NULL DEFAULT '0',  `FIRST_NAME` varchar(20) DEFAULT NULL,  `LAST_NAME` varchar(25) NOT NULL,  `EMAIL` varchar(25) NOT NULL,  `PHONE_NUMBER` varchar(20) DEFAULT NULL,  `HIRE_DATE` date NOT NULL,  `JOB_ID` varchar(10) NOT NULL,  `SALARY` decimal(8,2) DEFAULT NULL,  `COMMISSION_PCT` decimal(2,2) DEFAULT NULL,  `MANAGER_ID` decimal(6,0) DEFAULT NULL,  `DEPARTMENT_ID` decimal(4,0) DEFAULT NULL,  PRIMARY KEY (`EMPLOYEE_ID`),  UNIQUE KEY `EMP_EMAIL_UK` (`EMAIL`),  KEY `EMP_DEPARTMENT_IX` (`DEPARTMENT_ID`),  KEY `EMP_JOB_IX` (`JOB_ID`),  KEY `EMP_MANAGER_IX` (`MANAGER_ID`),  KEY `EMP_NAME_IX` (`LAST_NAME`,`FIRST_NAME`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> INSERT INTO `employees` (`EMPLOYEE_ID`, `FIRST_NAME`, `LAST_NAME`, `EMAIL`, `PHONE_NUMBER`, `HIRE_DATE`, `JOB_ID`, `SALARY`, `COMMISSION_PCT`, `MANAGER_ID`, `DEPARTMENT_ID`) VALUES('100', 'Steven', 'King', 'SKING', '515.123.4567', '1987-06-17', 'AD_PRES', '24000.00', '0.00', '0', '90'),('101', 'Neena', 'Kochhar', 'NKOCHHAR', '515.123.4568', '1987-06-18', 'AD_VP', '17000.00', '0.00', '100', '90'),('102', 'Lex', 'De Haan', 'LDEHAAN', '515.123.4569', '1987-06-19', 'AD_VP', '17000.00', '0.00', '100', '90'),('103', 'Alexander', 'Hunold', 'AHUNOLD', '590.423.4567', '1987-06-20', 'IT_PROG', '9000.00', '0.00', '102', '60'),('104', 'Bruce', 'Ernst', 'BERNST', '590.423.4568', '1987-06-21', 'IT_PROG', '6000.00', '0.00', '103', '60'),('105', 'David', 'Austin', 'DAUSTIN', '590.423.4569', '1987-06-22', 'IT_PROG', '4800.00', '0.00', '103', '60'),('106', 'Valli', 'Pataballa', 'VPATABAL', '590.423.4560', '1987-06-23', 'IT_PROG', '4800.00', '0.00', '103', '60'),('107', 'Diana', 'Lorentz', 'DLORENTZ', '590.423.5567', '1987-06-24', 'IT_PROG', '4200.00', '0.00', '103', '60'),('108', 'Nancy', 'Greenberg', 'NGREENBE', '515.124.4569', '1987-06-25', 'FI_MGR', '12000.00', '0.00', '101', '100'),('109', 'Daniel', 'Faviet', 'DFAVIET', '515.124.4169', '1987-06-26', 'FI_ACCOUNT', '9000.00', '0.00', '108', '100'),('110', 'John', 'Chen', 'JCHEN', '515.124.4269', '1987-06-27', 'FI_ACCOUNT', '8200.00', '0.00', '108', '100'),('111', 'Ismael', 'Sciarra', 'ISCIARRA', '515.124.4369', '1987-06-28', 'FI_ACCOUNT', '7700.00', '0.00', '108', '100'),('112', 'Jose Manuel', 'Urman', 'JMURMAN', '515.124.4469', '1987-06-29', 'FI_ACCOUNT', '7800.00', '0.00', '108', '100'),('113', 'Luis', 'Popp', 'LPOPP', '515.124.4567', '1987-06-30', 'FI_ACCOUNT', '6900.00', '0.00', '108', '100'),('114', 'Den', 'Raphaely', 'DRAPHEAL', '515.127.4561', '1987-07-01', 'PU_MAN', '11000.00', '0.00', '100', '30'),('115', 'Alexander', 'Khoo', 'AKHOO', '515.127.4562', '1987-07-02', 'PU_CLERK', '3100.00', '0.00', '114', '30'),('116', 'Shelli', 'Baida', 'SBAIDA', '515.127.4563', '1987-07-03', 'PU_CLERK', '2900.00', '0.00', '114', '30'),('117', 'Sigal', 'Tobias', 'STOBIAS', '515.127.4564', '1987-07-04', 'PU_CLERK', '2800.00', '0.00', '114', '30'),('118', 'Guy', 'Himuro', 'GHIMURO', '515.127.4565', '1987-07-05', 'PU_CLERK', '2600.00', '0.00', '114', '30'),('119', 'Karen', 'Colmenares', 'KCOLMENA', '515.127.4566', '1987-07-06', 'PU_CLERK', '2500.00', '0.00', '114', '30'),('120', 'Matthew', 'Weiss', 'MWEISS', '650.123.1234', '1987-07-07', 'ST_MAN', '8000.00', '0.00', '100', '50'),('121', 'Adam', 'Fripp', 'AFRIPP', '650.123.2234', '1987-07-08', 'ST_MAN', '8200.00', '0.00', '100', '50'),('122', 'Payam', 'Kaufling', 'PKAUFLIN', '650.123.3234', '1987-07-09', 'ST_MAN', '7900.00', '0.00', '100', '50'),('123', 'Shanta', 'Vollman', 'SVOLLMAN', '650.123.4234', '1987-07-10', 'ST_MAN', '6500.00', '0.00', '100', '50'),('124', 'Kevin', 'Mourgos', 'KMOURGOS', '650.123.5234', '1987-07-11', 'ST_MAN', '5800.00', '0.00', '100', '50'),('125', 'Julia', 'Nayer', 'JNAYER', '650.124.1214', '1987-07-12', 'ST_CLERK', '3200.00', '0.00', '120', '50'),('126', 'Irene', 'Mikkilineni', 'IMIKKILI', '650.124.1224', '1987-07-13', 'ST_CLERK', '2700.00', '0.00', '120', '50'),('127', 'James', 'Landry', 'JLANDRY', '650.124.1334', '1987-07-14', 'ST_CLERK', '2400.00', '0.00', '120', '50'),('128', 'Steven', 'Markle', 'SMARKLE', '650.124.1434', '1987-07-15', 'ST_CLERK', '2200.00', '0.00', '120', '50'),('129', 'Laura', 'Bissot', 'LBISSOT', '650.124.5234', '1987-07-16', 'ST_CLERK', '3300.00', '0.00', '121', '50'),('130', 'Mozhe', 'Atkinson', 'MATKINSO', '650.124.6234', '1987-07-17', 'ST_CLERK', '2800.00', '0.00', '121', '50'),('131', 'James', 'Marlow', 'JAMRLOW', '650.124.7234', '1987-07-18', 'ST_CLERK', '2500.00', '0.00', '121', '50'),('132', 'TJ', 'Olson', 'TJOLSON', '650.124.8234', '1987-07-19', 'ST_CLERK', '2100.00', '0.00', '121', '50'),('133', 'Jason', 'Mallin', 'JMALLIN', '650.127.1934', '1987-07-20', 'ST_CLERK', '3300.00', '0.00', '122', '50'),('134', 'Michael', 'Rogers', 'MROGERS', '650.127.1834', '1987-07-21', 'ST_CLERK', '2900.00', '0.00', '122', '50'),('135', 'Ki', 'Gee', 'KGEE', '650.127.1734', '1987-07-22', 'ST_CLERK', '2400.00', '0.00', '122', '50'),('136', 'Hazel', 'Philtanker', 'HPHILTAN', '650.127.1634', '1987-07-23', 'ST_CLERK', '2200.00', '0.00', '122', '50'),('137', 'Renske', 'Ladwig', 'RLADWIG', '650.121.1234', '1987-07-24', 'ST_CLERK', '3600.00', '0.00', '123', '50'),('138', 'Stephen', 'Stiles', 'SSTILES', '650.121.2034', '1987-07-25', 'ST_CLERK', '3200.00', '0.00', '123', '50'),('139', 'John', 'Seo', 'JSEO', '650.121.2019', '1987-07-26', 'ST_CLERK', '2700.00', '0.00', '123', '50'),('140', 'Joshua', 'Patel', 'JPATEL', '650.121.1834', '1987-07-27', 'ST_CLERK', '2500.00', '0.00', '123', '50'),('141', 'Trenna', 'Rajs', 'TRAJS', '650.121.8009', '1987-07-28', 'ST_CLERK', '3500.00', '0.00', '124', '50'),('142', 'Curtis', 'Davies', 'CDAVIES', '650.121.2994', '1987-07-29', 'ST_CLERK', '3100.00', '0.00', '124', '50'),('143', 'Randall', 'Matos', 'RMATOS', '650.121.2874', '1987-07-30', 'ST_CLERK', '2600.00', '0.00', '124', '50'),('144', 'Peter', 'Vargas', 'PVARGAS', '650.121.2004', '1987-07-31', 'ST_CLERK', '2500.00', '0.00', '124', '50'),('145', 'John', 'Russell', 'JRUSSEL', '011.44.1344.429268', '1987-08-01', 'SA_MAN', '14000.00', '0.40', '100', '80'),('146', 'Karen', 'Partners', 'KPARTNER', '011.44.1344.467268', '1987-08-02', 'SA_MAN', '13500.00', '0.30', '100', '80'),('147', 'Alberto', 'Errazuriz', 'AERRAZUR', '011.44.1344.429278', '1987-08-03', 'SA_MAN', '12000.00', '0.30', '100', '80'),('148', 'Gerald', 'Cambrault', 'GCAMBRAU', '011.44.1344.619268', '1987-08-04', 'SA_MAN', '11000.00', '0.30', '100', '80'),('149', 'Eleni', 'Zlotkey', 'EZLOTKEY', '011.44.1344.429018', '1987-08-05', 'SA_MAN', '10500.00', '0.20', '100', '80'),('150', 'Peter', 'Tucker', 'PTUCKER', '011.44.1344.129268', '1987-08-06', 'SA_REP', '10000.00', '0.30', '145', '80'),('151', 'David', 'Bernstein', 'DBERNSTE', '011.44.1344.345268', '1987-08-07', 'SA_REP', '9500.00', '0.25', '145', '80'),('152', 'Peter', 'Hall', 'PHALL', '011.44.1344.478968', '1987-08-08', 'SA_REP', '9000.00', '0.25', '145', '80'),('153', 'Christopher', 'Olsen', 'COLSEN', '011.44.1344.498718', '1987-08-09', 'SA_REP', '8000.00', '0.20', '145', '80'),('154', 'Nanette', 'Cambrault', 'NCAMBRAU', '011.44.1344.987668', '1987-08-10', 'SA_REP', '7500.00', '0.20', '145', '80'),('155', 'Oliver', 'Tuvault', 'OTUVAULT', '011.44.1344.486508', '1987-08-11', 'SA_REP', '7000.00', '0.15', '145', '80'),('156', 'Janette', 'King', 'JKING', '011.44.1345.429268', '1987-08-12', 'SA_REP', '10000.00', '0.35', '146', '80'),('157', 'Patrick', 'Sully', 'PSULLY', '011.44.1345.929268', '1987-08-13', 'SA_REP', '9500.00', '0.35', '146', '80'),('158', 'Allan', 'McEwen', 'AMCEWEN', '011.44.1345.829268', '1987-08-14', 'SA_REP', '9000.00', '0.35', '146', '80'),('159', 'Lindsey', 'Smith', 'LSMITH', '011.44.1345.729268', '1987-08-15', 'SA_REP', '8000.00', '0.30', '146', '80'),('160', 'Louise', 'Doran', 'LDORAN', '011.44.1345.629268', '1987-08-16', 'SA_REP', '7500.00', '0.30', '146', '80'),('161', 'Sarath', 'Sewall', 'SSEWALL', '011.44.1345.529268', '1987-08-17', 'SA_REP', '7000.00', '0.25', '146', '80'),('162', 'Clara', 'Vishney', 'CVISHNEY', '011.44.1346.129268', '1987-08-18', 'SA_REP', '10500.00', '0.25', '147', '80'),('163', 'Danielle', 'Greene', 'DGREENE', '011.44.1346.229268', '1987-08-19', 'SA_REP', '9500.00', '0.15', '147', '80'),('164', 'Mattea', 'Marvins', 'MMARVINS', '011.44.1346.329268', '1987-08-20', 'SA_REP', '7200.00', '0.10', '147', '80'),('165', 'David', 'Lee', 'DLEE', '011.44.1346.529268', '1987-08-21', 'SA_REP', '6800.00', '0.10', '147', '80'),('166', 'Sundar', 'Ande', 'SANDE', '011.44.1346.629268', '1987-08-22', 'SA_REP', '6400.00', '0.10', '147', '80'),('167', 'Amit', 'Banda', 'ABANDA', '011.44.1346.729268', '1987-08-23', 'SA_REP', '6200.00', '0.10', '147', '80'),('168', 'Lisa', 'Ozer', 'LOZER', '011.44.1343.929268', '1987-08-24', 'SA_REP', '11500.00', '0.25', '148', '80'),('169', 'Harrison', 'Bloom', 'HBLOOM', '011.44.1343.829268', '1987-08-25', 'SA_REP', '10000.00', '0.20', '148', '80'),('170', 'Tayler', 'Fox', 'TFOX', '011.44.1343.729268', '1987-08-26', 'SA_REP', '9600.00', '0.20', '148', '80'),('171', 'William', 'Smith', 'WSMITH', '011.44.1343.629268', '1987-08-27', 'SA_REP', '7400.00', '0.15', '148', '80'),('172', 'Elizabeth', 'Bates', 'EBATES', '011.44.1343.529268', '1987-08-28', 'SA_REP', '7300.00', '0.15', '148', '80'),('173', 'Sundita', 'Kumar', 'SKUMAR', '011.44.1343.329268', '1987-08-29', 'SA_REP', '6100.00', '0.10', '148', '80'),('174', 'Ellen', 'Abel', 'EABEL', '011.44.1644.429267', '1987-08-30', 'SA_REP', '11000.00', '0.30', '149', '80'),('175', 'Alyssa', 'Hutton', 'AHUTTON', '011.44.1644.429266', '1987-08-31', 'SA_REP', '8800.00', '0.25', '149', '80'),('176', 'Jonathon', 'Taylor', 'JTAYLOR', '011.44.1644.429265', '1987-09-01', 'SA_REP', '8600.00', '0.20', '149', '80'),('177', 'Jack', 'Livingston', 'JLIVINGS', '011.44.1644.429264', '1987-09-02', 'SA_REP', '8400.00', '0.20', '149', '80'),('178', 'Kimberely', 'Grant', 'KGRANT', '011.44.1644.429263', '1987-09-03', 'SA_REP', '7000.00', '0.15', '149', '0'),('179', 'Charles', 'Johnson', 'CJOHNSON', '011.44.1644.429262', '1987-09-04', 'SA_REP', '6200.00', '0.10', '149', '80'),('180', 'Winston', 'Taylor', 'WTAYLOR', '650.507.9876', '1987-09-05', 'SH_CLERK', '3200.00', '0.00', '120', '50'),('181', 'Jean', 'Fleaur', 'JFLEAUR', '650.507.9877', '1987-09-06', 'SH_CLERK', '3100.00', '0.00', '120', '50'),('182', 'Martha', 'Sullivan', 'MSULLIVA', '650.507.9878', '1987-09-07', 'SH_CLERK', '2500.00', '0.00', '120', '50'),('183', 'Girard', 'Geoni', 'GGEONI', '650.507.9879', '1987-09-08', 'SH_CLERK', '2800.00', '0.00', '120', '50'),('184', 'Nandita', 'Sarchand', 'NSARCHAN', '650.509.1876', '1987-09-09', 'SH_CLERK', '4200.00', '0.00', '121', '50'),('185', 'Alexis', 'Bull', 'ABULL', '650.509.2876', '1987-09-10', 'SH_CLERK', '4100.00', '0.00', '121', '50'),('186', 'Julia', 'Dellinger', 'JDELLING', '650.509.3876', '1987-09-11', 'SH_CLERK', '3400.00', '0.00', '121', '50'),('187', 'Anthony', 'Cabrio', 'ACABRIO', '650.509.4876', '1987-09-12', 'SH_CLERK', '3000.00', '0.00', '121', '50'),('188', 'Kelly', 'Chung', 'KCHUNG', '650.505.1876', '1987-09-13', 'SH_CLERK', '3800.00', '0.00', '122', '50'),('189', 'Jennifer', 'Dilly', 'JDILLY', '650.505.2876', '1987-09-14', 'SH_CLERK', '3600.00', '0.00', '122', '50'),('190', 'Timothy', 'Gates', 'TGATES', '650.505.3876', '1987-09-15', 'SH_CLERK', '2900.00', '0.00', '122', '50'),('191', 'Randall', 'Perkins', 'RPERKINS', '650.505.4876', '1987-09-16', 'SH_CLERK', '2500.00', '0.00', '122', '50'),('192', 'Sarah', 'Bell', 'SBELL', '650.501.1876', '1987-09-17', 'SH_CLERK', '4000.00', '0.00', '123', '50'),('193', 'Britney', 'Everett', 'BEVERETT', '650.501.2876', '1987-09-18', 'SH_CLERK', '3900.00', '0.00', '123', '50'),('194', 'Samuel', 'McCain', 'SMCCAIN', '650.501.3876', '1987-09-19', 'SH_CLERK', '3200.00', '0.00', '123', '50'),('195', 'Vance', 'Jones', 'VJONES', '650.501.4876', '1987-09-20', 'SH_CLERK', '2800.00', '0.00', '123', '50'),('196', 'Alana', 'Walsh', 'AWALSH', '650.507.9811', '1987-09-21', 'SH_CLERK', '3100.00', '0.00', '124', '50'),('197', 'Kevin', 'Feeney', 'KFEENEY', '650.507.9822', '1987-09-22', 'SH_CLERK', '3000.00', '0.00', '124', '50'),('198', 'Donald', 'OConnell', 'DOCONNEL', '650.507.9833', '1987-09-23', 'SH_CLERK', '2600.00', '0.00', '124', '50'),('199', 'Douglas', 'Grant', 'DGRANT', '650.507.9844', '1987-09-24', 'SH_CLERK', '2600.00', '0.00', '124', '50'),('200', 'Jennifer', 'Whalen', 'JWHALEN', '515.123.4444', '1987-09-25', 'AD_ASST', '4400.00', '0.00', '101', '10'),('201', 'Michael', 'Hartstein', 'MHARTSTE', '515.123.5555', '1987-09-26', 'MK_MAN', '13000.00', '0.00', '100', '20'),('202', 'Pat', 'Fay', 'PFAY', '603.123.6666', '1987-09-27', 'MK_REP', '6000.00', '0.00', '201', '20'),('203', 'Susan', 'Mavris', 'SMAVRIS', '515.123.7777', '1987-09-28', 'HR_REP', '6500.00', '0.00', '101', '40'),('204', 'Hermann', 'Baer', 'HBAER', '515.123.8888', '1987-09-29', 'PR_REP', '10000.00', '0.00', '101', '70'),('205', 'Shelley', 'Higgins', 'SHIGGINS', '515.123.8080', '1987-09-30', 'AC_MGR', '12000.00', '0.00', '101', '110'),('206', 'William', 'Gietz', 'WGIETZ', '515.123.8181', '1987-10-01', 'AC_ACCOUNT', '8300.00', '0.00', '205', '110');
Query OK, 107 rows affected (0.00 sec)
Records: 107  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `job_history` (  `EMPLOYEE_ID` decimal(6,0) NOT NULL,  `START_DATE` date NOT NULL,  `END_DATE` date NOT NULL,  `JOB_ID` varchar(10) NOT NULL,  `DEPARTMENT_ID` decimal(4,0) DEFAULT NULL,  PRIMARY KEY (`EMPLOYEE_ID`,`START_DATE`),  KEY `JHIST_DEPARTMENT_IX` (`DEPARTMENT_ID`),  KEY `JHIST_EMPLOYEE_IX` (`EMPLOYEE_ID`),  KEY `JHIST_JOB_IX` (`JOB_ID`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> INSERT INTO `job_history` (`EMPLOYEE_ID`, `START_DATE`, `END_DATE`, `JOB_ID`, `DEPARTMENT_ID`) VALUES('102', '1993-01-13', '1998-07-24', 'IT_PROG', '60'),('101', '1989-09-21', '1993-10-27', 'AC_ACCOUNT', '110'),('101', '1993-10-28', '1997-03-15', 'AC_MGR', '110'),('201', '1996-02-17', '1999-12-19', 'MK_REP', '20'),('114', '1998-03-24', '1999-12-31', 'ST_CLERK', '50'),('122', '1999-01-01', '1999-12-31', 'ST_CLERK', '50'),('200', '1987-09-17', '1993-06-17', 'AD_ASST', '90'),('176', '1998-03-24', '1998-12-31', 'SA_REP', '80'),('176', '1999-01-01', '1999-12-31', 'SA_MAN', '80'),('200', '1994-07-01', '1998-12-31', 'AC_ACCOUNT', '90'),('0', '0000-00-00', '0000-00-00', '', '0');
Query OK, 11 rows affected (0.00 sec)
Records: 11  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `jobs` (  `JOB_ID` varchar(10) NOT NULL DEFAULT '',  `JOB_TITLE` varchar(35) NOT NULL,  `MIN_SALARY` decimal(6,0) DEFAULT NULL,  `MAX_SALARY` decimal(6,0) DEFAULT NULL,  PRIMARY KEY (`JOB_ID`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.02 sec)

MariaDB [test]> INSERT INTO `jobs` (`JOB_ID`, `JOB_TITLE`, `MIN_SALARY`, `MAX_SALARY`) VALUES('AD_PRES', 'President', '20000', '40000'),('AD_VP', 'Administration Vice President', '15000', '30000'),('AD_ASST', 'Administration Assistant', '3000', '6000'),('FI_MGR', 'Finance Manager', '8200', '16000'),('FI_ACCOUNT', 'Accountant', '4200', '9000'),('AC_MGR', 'Accounting Manager', '8200', '16000'),('AC_ACCOUNT', 'Public Accountant', '4200', '9000'),('SA_MAN', 'Sales Manager', '10000', '20000'),('SA_REP', 'Sales Representative', '6000', '12000'),('PU_MAN', 'Purchasing Manager', '8000', '15000'),('PU_CLERK', 'Purchasing Clerk', '2500', '5500'),('ST_MAN', 'Stock Manager', '5500', '8500'),('ST_CLERK', 'Stock Clerk', '2000', '5000'),('SH_CLERK', 'Shipping Clerk', '2500', '5500'),('IT_PROG', 'Programmer', '4000', '10000'),('MK_MAN', 'Marketing Manager', '9000', '15000'),('MK_REP', 'Marketing Representative', '4000', '9000'),('HR_REP', 'Human Resources Representative', '4000', '9000'),('PR_REP', 'Public Relations Representative', '4500', '10500');
Query OK, 19 rows affected (0.00 sec)
Records: 19  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `locations` (  `LOCATION_ID` decimal(4,0) NOT NULL DEFAULT '0',  `STREET_ADDRESS` varchar(40) DEFAULT NULL,  `POSTAL_CODE` varchar(12) DEFAULT NULL,  `CITY` varchar(30) NOT NULL,  `STATE_PROVINCE` varchar(25) DEFAULT NULL,  `COUNTRY_ID` varchar(2) DEFAULT NULL,  PRIMARY KEY (`LOCATION_ID`),  KEY `LOC_CITY_IX` (`CITY`),  KEY `LOC_COUNTRY_IX` (`COUNTRY_ID`),  KEY `LOC_STATE_PROVINCE_IX` (`STATE_PROVINCE`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> INSERT INTO `locations` (`LOCATION_ID`, `STREET_ADDRESS`, `POSTAL_CODE`, `CITY`, `STATE_PROVINCE`, `COUNTRY_ID`) VALUES('1000', '1297 Via Cola di Rie', '989', 'Roma', '', 'IT'),('1100', '93091 Calle della Testa', '10934', 'Venice', '', 'IT'),('1200', '2017 Shinjuku-ku', '1689', 'Tokyo', 'Tokyo Prefecture', 'JP'),('1300', '9450 Kamiya-cho', '6823', 'Hiroshima', '', 'JP'),('1400', '2014 Jabberwocky Rd', '26192', 'Southlake', 'Texas', 'US'),('1500', '2011 Interiors Blvd', '99236', 'South San Francisco', 'California', 'US'),('1600', '2007 Zagora St', '50090', 'South Brunswick', 'New Jersey', 'US'),('1700', '2004 Charade Rd', '98199', 'Seattle', 'Washington', 'US'),('1800', '147 Spadina Ave', 'M5V 2L7', 'Toronto', 'Ontario', 'CA'),('1900', '6092 Boxwood St', 'YSW 9T2', 'Whitehorse', 'Yukon', 'CA'),('2000', '40-5-12 Laogianggen', '190518', 'Beijing', '', 'CN'),('2100', '1298 Vileparle (E)', '490231', 'Bombay', 'Maharashtra', 'IN'),('2200', '12-98 Victoria Street', '2901', 'Sydney', 'New South Wales', 'AU'),('2300', '198 Clementi North', '540198', 'Singapore', '', 'SG'),('2400', '8204 Arthur St', '', 'London', '', 'UK'),('2500', '"Magdalen Centre', ' The Oxford ', 'OX9 9ZB', 'Oxford', 'Ox'),('2600', '9702 Chester Road', '9629850293', 'Stretford', 'Manchester', 'UK'),('2700', 'Schwanthalerstr. 7031', '80925', 'Munich', 'Bavaria', 'DE'),('2800', 'Rua Frei Caneca 1360', '01307-002', 'Sao Paulo', 'Sao Paulo', 'BR'),('2900', '20 Rue des Corps-Saints', '1730', 'Geneva', 'Geneve', 'CH'),('3000', 'Murtenstrasse 921', '3095', 'Bern', 'BE', 'CH'),('3100', 'Pieter Breughelstraat 837', '3029SK', 'Utrecht', 'Utrecht', 'NL'),('3200', 'Mariano Escobedo 9991', '11932', 'Mexico City', '"Distrito Federal', '"');
Query OK, 23 rows affected (0.00 sec)
Records: 23  Duplicates: 0  Warnings: 0

MariaDB [test]> CREATE TABLE IF NOT EXISTS `regions` (  `REGION_ID` decimal(5,0) NOT NULL,  `REGION_NAME` varchar(25) DEFAULT NULL,  PRIMARY KEY (`REGION_ID`),  UNIQUE KEY `sss` (`REGION_NAME`)) ENGINE=MyISAM DEFAULT CHARSET=latin1;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> INSERT INTO `regions` (`REGION_ID`, `REGION_NAME`) VALUES('1', 'Europe\r'),('2', 'Americas\r'),('3', 'Asia\r'),('4', 'Middle East and Africa\r');
Query OK, 4 rows affected (0.00 sec)
Records: 4  Duplicates: 0  Warnings: 0

MariaDB [test]> select first_name, last_name, salary from employees where salary > (select salary from employees where last_name="Bull");
+-------------+------------+----------+
| first_name  | last_name  | salary   |
+-------------+------------+----------+
| Steven      | King       | 24000.00 |
| Neena       | Kochhar    | 17000.00 |
| Lex         | De Haan    | 17000.00 |
| Alexander   | Hunold     |  9000.00 |
| Bruce       | Ernst      |  6000.00 |
| David       | Austin     |  4800.00 |
| Valli       | Pataballa  |  4800.00 |
| Diana       | Lorentz    |  4200.00 |
| Nancy       | Greenberg  | 12000.00 |
| Daniel      | Faviet     |  9000.00 |
| John        | Chen       |  8200.00 |
| Ismael      | Sciarra    |  7700.00 |
| Jose Manuel | Urman      |  7800.00 |
| Luis        | Popp       |  6900.00 |
| Den         | Raphaely   | 11000.00 |
| Matthew     | Weiss      |  8000.00 |
| Adam        | Fripp      |  8200.00 |
| Payam       | Kaufling   |  7900.00 |
| Shanta      | Vollman    |  6500.00 |
| Kevin       | Mourgos    |  5800.00 |
| John        | Russell    | 14000.00 |
| Karen       | Partners   | 13500.00 |
| Alberto     | Errazuriz  | 12000.00 |
| Gerald      | Cambrault  | 11000.00 |
| Eleni       | Zlotkey    | 10500.00 |
| Peter       | Tucker     | 10000.00 |
| David       | Bernstein  |  9500.00 |
| Peter       | Hall       |  9000.00 |
| Christopher | Olsen      |  8000.00 |
| Nanette     | Cambrault  |  7500.00 |
| Oliver      | Tuvault    |  7000.00 |
| Janette     | King       | 10000.00 |
| Patrick     | Sully      |  9500.00 |
| Allan       | McEwen     |  9000.00 |
| Lindsey     | Smith      |  8000.00 |
| Louise      | Doran      |  7500.00 |
| Sarath      | Sewall     |  7000.00 |
| Clara       | Vishney    | 10500.00 |
| Danielle    | Greene     |  9500.00 |
| Mattea      | Marvins    |  7200.00 |
| David       | Lee        |  6800.00 |
| Sundar      | Ande       |  6400.00 |
| Amit        | Banda      |  6200.00 |
| Lisa        | Ozer       | 11500.00 |
| Harrison    | Bloom      | 10000.00 |
| Tayler      | Fox        |  9600.00 |
| William     | Smith      |  7400.00 |
| Elizabeth   | Bates      |  7300.00 |
| Sundita     | Kumar      |  6100.00 |
| Ellen       | Abel       | 11000.00 |
| Alyssa      | Hutton     |  8800.00 |
| Jonathon    | Taylor     |  8600.00 |
| Jack        | Livingston |  8400.00 |
| Kimberely   | Grant      |  7000.00 |
| Charles     | Johnson    |  6200.00 |
| Nandita     | Sarchand   |  4200.00 |
| Jennifer    | Whalen     |  4400.00 |
| Michael     | Hartstein  | 13000.00 |
| Pat         | Fay        |  6000.00 |
| Susan       | Mavris     |  6500.00 |
| Hermann     | Baer       | 10000.00 |
| Shelley     | Higgins    | 12000.00 |
| William     | Gietz      |  8300.00 |
+-------------+------------+----------+
63 rows in set (0.02 sec)

MariaDB [test]> select first_name, last_name salary from employees where salary =(select salary from employees where last_name = "Johnson");
+------------+---------+
| first_name | salary  |
+------------+---------+
| Amit       | Banda   |
| Charles    | Johnson |
+------------+---------+
2 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name, salary from employees where salary =(select salary from employees where last_name = "Johnson");
+------------+-----------+---------+
| first_name | last_name | salary  |
+------------+-----------+---------+
| Amit       | Banda     | 6200.00 |
| Charles    | Johnson   | 6200.00 |
+------------+-----------+---------+
2 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name from employees where department_id = 60;
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Alexander  | Hunold    |
| Bruce      | Ernst     |
| David      | Austin    |
| Valli      | Pataballa |
| Diana      | Lorentz   |
+------------+-----------+
5 rows in set (0.00 sec)

MariaDB [test]> select department_id from departments where department_name = 'IT';
+---------------+
| department_id |
+---------------+
|            60 |
+---------------+
1 row in set (0.00 sec)

MariaDB [test]> select first_name, last_name from employees where department_id = (select department_id from departments where department_name = 'IT');
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Alexander  | Hunold    |
| Bruce      | Ernst     |
| David      | Austin    |
| Valli      | Pataballa |
| Diana      | Lorentz   |
+------------+-----------+
5 rows in set (0.00 sec)

MariaDB [test]> select max(salary) from employees where department_id =(select department_id from departments where department_name = 'IT');
+-------------+
| max(salary) |
+-------------+
|     9000.00 |
+-------------+
1 row in set (0.00 sec)

MariaDB [test]> select* from employees
    -> ;
+-------------+-------------+-------------+----------+--------------------+------------+------------+----------+----------------+------------+---------------+
| EMPLOYEE_ID | FIRST_NAME  | LAST_NAME   | EMAIL    | PHONE_NUMBER       | HIRE_DATE  | JOB_ID     | SALARY   | COMMISSION_PCT | MANAGER_ID | DEPARTMENT_ID |
+-------------+-------------+-------------+----------+--------------------+------------+------------+----------+----------------+------------+---------------+
|         100 | Steven      | King        | SKING    | 515.123.4567       | 1987-06-17 | AD_PRES    | 24000.00 |           0.00 |          0 |            90 |
|         101 | Neena       | Kochhar     | NKOCHHAR | 515.123.4568       | 1987-06-18 | AD_VP      | 17000.00 |           0.00 |        100 |            90 |
|         102 | Lex         | De Haan     | LDEHAAN  | 515.123.4569       | 1987-06-19 | AD_VP      | 17000.00 |           0.00 |        100 |            90 |
|         103 | Alexander   | Hunold      | AHUNOLD  | 590.423.4567       | 1987-06-20 | IT_PROG    |  9000.00 |           0.00 |        102 |            60 |
|         104 | Bruce       | Ernst       | BERNST   | 590.423.4568       | 1987-06-21 | IT_PROG    |  6000.00 |           0.00 |        103 |            60 |
|         105 | David       | Austin      | DAUSTIN  | 590.423.4569       | 1987-06-22 | IT_PROG    |  4800.00 |           0.00 |        103 |            60 |
|         106 | Valli       | Pataballa   | VPATABAL | 590.423.4560       | 1987-06-23 | IT_PROG    |  4800.00 |           0.00 |        103 |            60 |
|         107 | Diana       | Lorentz     | DLORENTZ | 590.423.5567       | 1987-06-24 | IT_PROG    |  4200.00 |           0.00 |        103 |            60 |
|         108 | Nancy       | Greenberg   | NGREENBE | 515.124.4569       | 1987-06-25 | FI_MGR     | 12000.00 |           0.00 |        101 |           100 |
|         109 | Daniel      | Faviet      | DFAVIET  | 515.124.4169       | 1987-06-26 | FI_ACCOUNT |  9000.00 |           0.00 |        108 |           100 |
|         110 | John        | Chen        | JCHEN    | 515.124.4269       | 1987-06-27 | FI_ACCOUNT |  8200.00 |           0.00 |        108 |           100 |
|         111 | Ismael      | Sciarra     | ISCIARRA | 515.124.4369       | 1987-06-28 | FI_ACCOUNT |  7700.00 |           0.00 |        108 |           100 |
|         112 | Jose Manuel | Urman       | JMURMAN  | 515.124.4469       | 1987-06-29 | FI_ACCOUNT |  7800.00 |           0.00 |        108 |           100 |
|         113 | Luis        | Popp        | LPOPP    | 515.124.4567       | 1987-06-30 | FI_ACCOUNT |  6900.00 |           0.00 |        108 |           100 |
|         114 | Den         | Raphaely    | DRAPHEAL | 515.127.4561       | 1987-07-01 | PU_MAN     | 11000.00 |           0.00 |        100 |            30 |
|         115 | Alexander   | Khoo        | AKHOO    | 515.127.4562       | 1987-07-02 | PU_CLERK   |  3100.00 |           0.00 |        114 |            30 |
|         116 | Shelli      | Baida       | SBAIDA   | 515.127.4563       | 1987-07-03 | PU_CLERK   |  2900.00 |           0.00 |        114 |            30 |
|         117 | Sigal       | Tobias      | STOBIAS  | 515.127.4564       | 1987-07-04 | PU_CLERK   |  2800.00 |           0.00 |        114 |            30 |
|         118 | Guy         | Himuro      | GHIMURO  | 515.127.4565       | 1987-07-05 | PU_CLERK   |  2600.00 |           0.00 |        114 |            30 |
|         119 | Karen       | Colmenares  | KCOLMENA | 515.127.4566       | 1987-07-06 | PU_CLERK   |  2500.00 |           0.00 |        114 |            30 |
|         120 | Matthew     | Weiss       | MWEISS   | 650.123.1234       | 1987-07-07 | ST_MAN     |  8000.00 |           0.00 |        100 |            50 |
|         121 | Adam        | Fripp       | AFRIPP   | 650.123.2234       | 1987-07-08 | ST_MAN     |  8200.00 |           0.00 |        100 |            50 |
|         122 | Payam       | Kaufling    | PKAUFLIN | 650.123.3234       | 1987-07-09 | ST_MAN     |  7900.00 |           0.00 |        100 |            50 |
|         123 | Shanta      | Vollman     | SVOLLMAN | 650.123.4234       | 1987-07-10 | ST_MAN     |  6500.00 |           0.00 |        100 |            50 |
|         124 | Kevin       | Mourgos     | KMOURGOS | 650.123.5234       | 1987-07-11 | ST_MAN     |  5800.00 |           0.00 |        100 |            50 |
|         125 | Julia       | Nayer       | JNAYER   | 650.124.1214       | 1987-07-12 | ST_CLERK   |  3200.00 |           0.00 |        120 |            50 |
|         126 | Irene       | Mikkilineni | IMIKKILI | 650.124.1224       | 1987-07-13 | ST_CLERK   |  2700.00 |           0.00 |        120 |            50 |
|         127 | James       | Landry      | JLANDRY  | 650.124.1334       | 1987-07-14 | ST_CLERK   |  2400.00 |           0.00 |        120 |            50 |
|         128 | Steven      | Markle      | SMARKLE  | 650.124.1434       | 1987-07-15 | ST_CLERK   |  2200.00 |           0.00 |        120 |            50 |
|         129 | Laura       | Bissot      | LBISSOT  | 650.124.5234       | 1987-07-16 | ST_CLERK   |  3300.00 |           0.00 |        121 |            50 |
|         130 | Mozhe       | Atkinson    | MATKINSO | 650.124.6234       | 1987-07-17 | ST_CLERK   |  2800.00 |           0.00 |        121 |            50 |
|         131 | James       | Marlow      | JAMRLOW  | 650.124.7234       | 1987-07-18 | ST_CLERK   |  2500.00 |           0.00 |        121 |            50 |
|         132 | TJ          | Olson       | TJOLSON  | 650.124.8234       | 1987-07-19 | ST_CLERK   |  2100.00 |           0.00 |        121 |            50 |
|         133 | Jason       | Mallin      | JMALLIN  | 650.127.1934       | 1987-07-20 | ST_CLERK   |  3300.00 |           0.00 |        122 |            50 |
|         134 | Michael     | Rogers      | MROGERS  | 650.127.1834       | 1987-07-21 | ST_CLERK   |  2900.00 |           0.00 |        122 |            50 |
|         135 | Ki          | Gee         | KGEE     | 650.127.1734       | 1987-07-22 | ST_CLERK   |  2400.00 |           0.00 |        122 |            50 |
|         136 | Hazel       | Philtanker  | HPHILTAN | 650.127.1634       | 1987-07-23 | ST_CLERK   |  2200.00 |           0.00 |        122 |            50 |
|         137 | Renske      | Ladwig      | RLADWIG  | 650.121.1234       | 1987-07-24 | ST_CLERK   |  3600.00 |           0.00 |        123 |            50 |
|         138 | Stephen     | Stiles      | SSTILES  | 650.121.2034       | 1987-07-25 | ST_CLERK   |  3200.00 |           0.00 |        123 |            50 |
|         139 | John        | Seo         | JSEO     | 650.121.2019       | 1987-07-26 | ST_CLERK   |  2700.00 |           0.00 |        123 |            50 |
|         140 | Joshua      | Patel       | JPATEL   | 650.121.1834       | 1987-07-27 | ST_CLERK   |  2500.00 |           0.00 |        123 |            50 |
|         141 | Trenna      | Rajs        | TRAJS    | 650.121.8009       | 1987-07-28 | ST_CLERK   |  3500.00 |           0.00 |        124 |            50 |
|         142 | Curtis      | Davies      | CDAVIES  | 650.121.2994       | 1987-07-29 | ST_CLERK   |  3100.00 |           0.00 |        124 |            50 |
|         143 | Randall     | Matos       | RMATOS   | 650.121.2874       | 1987-07-30 | ST_CLERK   |  2600.00 |           0.00 |        124 |            50 |
|         144 | Peter       | Vargas      | PVARGAS  | 650.121.2004       | 1987-07-31 | ST_CLERK   |  2500.00 |           0.00 |        124 |            50 |
|         145 | John        | Russell     | JRUSSEL  | 011.44.1344.429268 | 1987-08-01 | SA_MAN     | 14000.00 |           0.40 |        100 |            80 |
|         146 | Karen       | Partners    | KPARTNER | 011.44.1344.467268 | 1987-08-02 | SA_MAN     | 13500.00 |           0.30 |        100 |            80 |
|         147 | Alberto     | Errazuriz   | AERRAZUR | 011.44.1344.429278 | 1987-08-03 | SA_MAN     | 12000.00 |           0.30 |        100 |            80 |
|         148 | Gerald      | Cambrault   | GCAMBRAU | 011.44.1344.619268 | 1987-08-04 | SA_MAN     | 11000.00 |           0.30 |        100 |            80 |
|         149 | Eleni       | Zlotkey     | EZLOTKEY | 011.44.1344.429018 | 1987-08-05 | SA_MAN     | 10500.00 |           0.20 |        100 |            80 |
|         150 | Peter       | Tucker      | PTUCKER  | 011.44.1344.129268 | 1987-08-06 | SA_REP     | 10000.00 |           0.30 |        145 |            80 |
|         151 | David       | Bernstein   | DBERNSTE | 011.44.1344.345268 | 1987-08-07 | SA_REP     |  9500.00 |           0.25 |        145 |            80 |
|         152 | Peter       | Hall        | PHALL    | 011.44.1344.478968 | 1987-08-08 | SA_REP     |  9000.00 |           0.25 |        145 |            80 |
|         153 | Christopher | Olsen       | COLSEN   | 011.44.1344.498718 | 1987-08-09 | SA_REP     |  8000.00 |           0.20 |        145 |            80 |
|         154 | Nanette     | Cambrault   | NCAMBRAU | 011.44.1344.987668 | 1987-08-10 | SA_REP     |  7500.00 |           0.20 |        145 |            80 |
|         155 | Oliver      | Tuvault     | OTUVAULT | 011.44.1344.486508 | 1987-08-11 | SA_REP     |  7000.00 |           0.15 |        145 |            80 |
|         156 | Janette     | King        | JKING    | 011.44.1345.429268 | 1987-08-12 | SA_REP     | 10000.00 |           0.35 |        146 |            80 |
|         157 | Patrick     | Sully       | PSULLY   | 011.44.1345.929268 | 1987-08-13 | SA_REP     |  9500.00 |           0.35 |        146 |            80 |
|         158 | Allan       | McEwen      | AMCEWEN  | 011.44.1345.829268 | 1987-08-14 | SA_REP     |  9000.00 |           0.35 |        146 |            80 |
|         159 | Lindsey     | Smith       | LSMITH   | 011.44.1345.729268 | 1987-08-15 | SA_REP     |  8000.00 |           0.30 |        146 |            80 |
|         160 | Louise      | Doran       | LDORAN   | 011.44.1345.629268 | 1987-08-16 | SA_REP     |  7500.00 |           0.30 |        146 |            80 |
|         161 | Sarath      | Sewall      | SSEWALL  | 011.44.1345.529268 | 1987-08-17 | SA_REP     |  7000.00 |           0.25 |        146 |            80 |
|         162 | Clara       | Vishney     | CVISHNEY | 011.44.1346.129268 | 1987-08-18 | SA_REP     | 10500.00 |           0.25 |        147 |            80 |
|         163 | Danielle    | Greene      | DGREENE  | 011.44.1346.229268 | 1987-08-19 | SA_REP     |  9500.00 |           0.15 |        147 |            80 |
|         164 | Mattea      | Marvins     | MMARVINS | 011.44.1346.329268 | 1987-08-20 | SA_REP     |  7200.00 |           0.10 |        147 |            80 |
|         165 | David       | Lee         | DLEE     | 011.44.1346.529268 | 1987-08-21 | SA_REP     |  6800.00 |           0.10 |        147 |            80 |
|         166 | Sundar      | Ande        | SANDE    | 011.44.1346.629268 | 1987-08-22 | SA_REP     |  6400.00 |           0.10 |        147 |            80 |
|         167 | Amit        | Banda       | ABANDA   | 011.44.1346.729268 | 1987-08-23 | SA_REP     |  6200.00 |           0.10 |        147 |            80 |
|         168 | Lisa        | Ozer        | LOZER    | 011.44.1343.929268 | 1987-08-24 | SA_REP     | 11500.00 |           0.25 |        148 |            80 |
|         169 | Harrison    | Bloom       | HBLOOM   | 011.44.1343.829268 | 1987-08-25 | SA_REP     | 10000.00 |           0.20 |        148 |            80 |
|         170 | Tayler      | Fox         | TFOX     | 011.44.1343.729268 | 1987-08-26 | SA_REP     |  9600.00 |           0.20 |        148 |            80 |
|         171 | William     | Smith       | WSMITH   | 011.44.1343.629268 | 1987-08-27 | SA_REP     |  7400.00 |           0.15 |        148 |            80 |
|         172 | Elizabeth   | Bates       | EBATES   | 011.44.1343.529268 | 1987-08-28 | SA_REP     |  7300.00 |           0.15 |        148 |            80 |
|         173 | Sundita     | Kumar       | SKUMAR   | 011.44.1343.329268 | 1987-08-29 | SA_REP     |  6100.00 |           0.10 |        148 |            80 |
|         174 | Ellen       | Abel        | EABEL    | 011.44.1644.429267 | 1987-08-30 | SA_REP     | 11000.00 |           0.30 |        149 |            80 |
|         175 | Alyssa      | Hutton      | AHUTTON  | 011.44.1644.429266 | 1987-08-31 | SA_REP     |  8800.00 |           0.25 |        149 |            80 |
|         176 | Jonathon    | Taylor      | JTAYLOR  | 011.44.1644.429265 | 1987-09-01 | SA_REP     |  8600.00 |           0.20 |        149 |            80 |
|         177 | Jack        | Livingston  | JLIVINGS | 011.44.1644.429264 | 1987-09-02 | SA_REP     |  8400.00 |           0.20 |        149 |            80 |
|         178 | Kimberely   | Grant       | KGRANT   | 011.44.1644.429263 | 1987-09-03 | SA_REP     |  7000.00 |           0.15 |        149 |             0 |
|         179 | Charles     | Johnson     | CJOHNSON | 011.44.1644.429262 | 1987-09-04 | SA_REP     |  6200.00 |           0.10 |        149 |            80 |
|         180 | Winston     | Taylor      | WTAYLOR  | 650.507.9876       | 1987-09-05 | SH_CLERK   |  3200.00 |           0.00 |        120 |            50 |
|         181 | Jean        | Fleaur      | JFLEAUR  | 650.507.9877       | 1987-09-06 | SH_CLERK   |  3100.00 |           0.00 |        120 |            50 |
|         182 | Martha      | Sullivan    | MSULLIVA | 650.507.9878       | 1987-09-07 | SH_CLERK   |  2500.00 |           0.00 |        120 |            50 |
|         183 | Girard      | Geoni       | GGEONI   | 650.507.9879       | 1987-09-08 | SH_CLERK   |  2800.00 |           0.00 |        120 |            50 |
|         184 | Nandita     | Sarchand    | NSARCHAN | 650.509.1876       | 1987-09-09 | SH_CLERK   |  4200.00 |           0.00 |        121 |            50 |
|         185 | Alexis      | Bull        | ABULL    | 650.509.2876       | 1987-09-10 | SH_CLERK   |  4100.00 |           0.00 |        121 |            50 |
|         186 | Julia       | Dellinger   | JDELLING | 650.509.3876       | 1987-09-11 | SH_CLERK   |  3400.00 |           0.00 |        121 |            50 |
|         187 | Anthony     | Cabrio      | ACABRIO  | 650.509.4876       | 1987-09-12 | SH_CLERK   |  3000.00 |           0.00 |        121 |            50 |
|         188 | Kelly       | Chung       | KCHUNG   | 650.505.1876       | 1987-09-13 | SH_CLERK   |  3800.00 |           0.00 |        122 |            50 |
|         189 | Jennifer    | Dilly       | JDILLY   | 650.505.2876       | 1987-09-14 | SH_CLERK   |  3600.00 |           0.00 |        122 |            50 |
|         190 | Timothy     | Gates       | TGATES   | 650.505.3876       | 1987-09-15 | SH_CLERK   |  2900.00 |           0.00 |        122 |            50 |
|         191 | Randall     | Perkins     | RPERKINS | 650.505.4876       | 1987-09-16 | SH_CLERK   |  2500.00 |           0.00 |        122 |            50 |
|         192 | Sarah       | Bell        | SBELL    | 650.501.1876       | 1987-09-17 | SH_CLERK   |  4000.00 |           0.00 |        123 |            50 |
|         193 | Britney     | Everett     | BEVERETT | 650.501.2876       | 1987-09-18 | SH_CLERK   |  3900.00 |           0.00 |        123 |            50 |
|         194 | Samuel      | McCain      | SMCCAIN  | 650.501.3876       | 1987-09-19 | SH_CLERK   |  3200.00 |           0.00 |        123 |            50 |
|         195 | Vance       | Jones       | VJONES   | 650.501.4876       | 1987-09-20 | SH_CLERK   |  2800.00 |           0.00 |        123 |            50 |
|         196 | Alana       | Walsh       | AWALSH   | 650.507.9811       | 1987-09-21 | SH_CLERK   |  3100.00 |           0.00 |        124 |            50 |
|         197 | Kevin       | Feeney      | KFEENEY  | 650.507.9822       | 1987-09-22 | SH_CLERK   |  3000.00 |           0.00 |        124 |            50 |
|         198 | Donald      | OConnell    | DOCONNEL | 650.507.9833       | 1987-09-23 | SH_CLERK   |  2600.00 |           0.00 |        124 |            50 |
|         199 | Douglas     | Grant       | DGRANT   | 650.507.9844       | 1987-09-24 | SH_CLERK   |  2600.00 |           0.00 |        124 |            50 |
|         200 | Jennifer    | Whalen      | JWHALEN  | 515.123.4444       | 1987-09-25 | AD_ASST    |  4400.00 |           0.00 |        101 |            10 |
|         201 | Michael     | Hartstein   | MHARTSTE | 515.123.5555       | 1987-09-26 | MK_MAN     | 13000.00 |           0.00 |        100 |            20 |
|         202 | Pat         | Fay         | PFAY     | 603.123.6666       | 1987-09-27 | MK_REP     |  6000.00 |           0.00 |        201 |            20 |
|         203 | Susan       | Mavris      | SMAVRIS  | 515.123.7777       | 1987-09-28 | HR_REP     |  6500.00 |           0.00 |        101 |            40 |
|         204 | Hermann     | Baer        | HBAER    | 515.123.8888       | 1987-09-29 | PR_REP     | 10000.00 |           0.00 |        101 |            70 |
|         205 | Shelley     | Higgins     | SHIGGINS | 515.123.8080       | 1987-09-30 | AC_MGR     | 12000.00 |           0.00 |        101 |           110 |
|         206 | William     | Gietz       | WGIETZ   | 515.123.8181       | 1987-10-01 | AC_ACCOUNT |  8300.00 |           0.00 |        205 |           110 |
+-------------+-------------+-------------+----------+--------------------+------------+------------+----------+----------------+------------+---------------+
107 rows in set (0.00 sec)

MariaDB [test]> desc employees;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| EMPLOYEE_ID    | decimal(6,0) | NO   | PRI | 0       |       |
| FIRST_NAME     | varchar(20)  | YES  |     | NULL    |       |
| LAST_NAME      | varchar(25)  | NO   | MUL | NULL    |       |
| EMAIL          | varchar(25)  | NO   | UNI | NULL    |       |
| PHONE_NUMBER   | varchar(20)  | YES  |     | NULL    |       |
| HIRE_DATE      | date         | NO   |     | NULL    |       |
| JOB_ID         | varchar(10)  | NO   | MUL | NULL    |       |
| SALARY         | decimal(8,2) | YES  |     | NULL    |       |
| COMMISSION_PCT | decimal(2,2) | YES  |     | NULL    |       |
| MANAGER_ID     | decimal(6,0) | YES  | MUL | NULL    |       |
| DEPARTMENT_ID  | decimal(4,0) | YES  | MUL | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
11 rows in set (0.00 sec)

MariaDB [test]> desc departments;
+-----------------+--------------+------+-----+---------+-------+
| Field           | Type         | Null | Key | Default | Extra |
+-----------------+--------------+------+-----+---------+-------+
| DEPARTMENT_ID   | decimal(4,0) | NO   | PRI | 0       |       |
| DEPARTMENT_NAME | varchar(30)  | NO   |     | NULL    |       |
| MANAGER_ID      | decimal(6,0) | YES  | MUL | NULL    |       |
| LOCATION_ID     | decimal(4,0) | YES  | MUL | NULL    |       |
+-----------------+--------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

MariaDB [test]> desc locations;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| LOCATION_ID    | decimal(4,0) | NO   | PRI | 0       |       |
| STREET_ADDRESS | varchar(40)  | YES  |     | NULL    |       |
| POSTAL_CODE    | varchar(12)  | YES  |     | NULL    |       |
| CITY           | varchar(30)  | NO   | MUL | NULL    |       |
| STATE_PROVINCE | varchar(25)  | YES  | MUL | NULL    |       |
| COUNTRY_ID     | varchar(2)   | YES  | MUL | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
6 rows in set (0.01 sec)

MariaDB [test]> select country_id from locations;
+------------+
| country_id |
+------------+
| "          |
| AU         |
| BR         |
| CA         |
| CA         |
| CH         |
| CH         |
| CN         |
| DE         |
| IN         |
| IT         |
| IT         |
| JP         |
| JP         |
| NL         |
| Ox         |
| SG         |
| UK         |
| UK         |
| US         |
| US         |
| US         |
| US         |
+------------+
23 rows in set (0.00 sec)

MariaDB [test]> select country_id from locations where country_id = US';
    '> ;
    '> '
    -> '
    '> '
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '';
;
'
'
'' at line 1
MariaDB [test]> SELECT COUNTRY_ID FROM LOCATIONS WHERE COUNTRY_ID ='US';
+------------+
| COUNTRY_ID |
+------------+
| US         |
| US         |
| US         |
| US         |
+------------+
4 rows in set (0.00 sec)

MariaDB [test]> SELECT department_id from departments where location_id in (select location_id from locations where country_id ='us';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 1
MariaDB [test]> SELECT department_id from departments where location_id in (select location_id from locations where country_id ='us');
+---------------+
| department_id |
+---------------+
|            60 |
|            50 |
|            10 |
|            30 |
|            90 |
|           100 |
|           110 |
|           120 |
|           130 |
|           140 |
|           150 |
|           160 |
|           170 |
|           180 |
|           190 |
|           200 |
|           210 |
|           220 |
|           230 |
|           240 |
|           250 |
|           260 |
|           270 |
+---------------+
23 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name, department_id from employees where department_id in (SELECT department_id from departments where location_id in (select location_id from locations where country_id ='us'));
+-------------+-------------+---------------+
| first_name  | last_name   | department_id |
+-------------+-------------+---------------+
| Alexander   | Hunold      |            60 |
| Bruce       | Ernst       |            60 |
| David       | Austin      |            60 |
| Valli       | Pataballa   |            60 |
| Diana       | Lorentz     |            60 |
| Matthew     | Weiss       |            50 |
| Adam        | Fripp       |            50 |
| Payam       | Kaufling    |            50 |
| Shanta      | Vollman     |            50 |
| Kevin       | Mourgos     |            50 |
| Julia       | Nayer       |            50 |
| Irene       | Mikkilineni |            50 |
| James       | Landry      |            50 |
| Steven      | Markle      |            50 |
| Laura       | Bissot      |            50 |
| Mozhe       | Atkinson    |            50 |
| James       | Marlow      |            50 |
| TJ          | Olson       |            50 |
| Jason       | Mallin      |            50 |
| Michael     | Rogers      |            50 |
| Ki          | Gee         |            50 |
| Hazel       | Philtanker  |            50 |
| Renske      | Ladwig      |            50 |
| Stephen     | Stiles      |            50 |
| John        | Seo         |            50 |
| Joshua      | Patel       |            50 |
| Trenna      | Rajs        |            50 |
| Curtis      | Davies      |            50 |
| Randall     | Matos       |            50 |
| Peter       | Vargas      |            50 |
| Winston     | Taylor      |            50 |
| Jean        | Fleaur      |            50 |
| Martha      | Sullivan    |            50 |
| Girard      | Geoni       |            50 |
| Nandita     | Sarchand    |            50 |
| Alexis      | Bull        |            50 |
| Julia       | Dellinger   |            50 |
| Anthony     | Cabrio      |            50 |
| Kelly       | Chung       |            50 |
| Jennifer    | Dilly       |            50 |
| Timothy     | Gates       |            50 |
| Randall     | Perkins     |            50 |
| Sarah       | Bell        |            50 |
| Britney     | Everett     |            50 |
| Samuel      | McCain      |            50 |
| Vance       | Jones       |            50 |
| Alana       | Walsh       |            50 |
| Kevin       | Feeney      |            50 |
| Donald      | OConnell    |            50 |
| Douglas     | Grant       |            50 |
| Jennifer    | Whalen      |            10 |
| Den         | Raphaely    |            30 |
| Alexander   | Khoo        |            30 |
| Shelli      | Baida       |            30 |
| Sigal       | Tobias      |            30 |
| Guy         | Himuro      |            30 |
| Karen       | Colmenares  |            30 |
| Steven      | King        |            90 |
| Neena       | Kochhar     |            90 |
| Lex         | De Haan     |            90 |
| Nancy       | Greenberg   |           100 |
| Daniel      | Faviet      |           100 |
| John        | Chen        |           100 |
| Ismael      | Sciarra     |           100 |
| Jose Manuel | Urman       |           100 |
| Luis        | Popp        |           100 |
| Shelley     | Higgins     |           110 |
| William     | Gietz       |           110 |
+-------------+-------------+---------------+
68 rows in set (0.01 sec)

MariaDB [test]> desc employes;
ERROR 1146 (42S02): Table 'test.employes' doesn't exist
MariaDB [test]> desc employees
    -> ;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| EMPLOYEE_ID    | decimal(6,0) | NO   | PRI | 0       |       |
| FIRST_NAME     | varchar(20)  | YES  |     | NULL    |       |
| LAST_NAME      | varchar(25)  | NO   | MUL | NULL    |       |
| EMAIL          | varchar(25)  | NO   | UNI | NULL    |       |
| PHONE_NUMBER   | varchar(20)  | YES  |     | NULL    |       |
| HIRE_DATE      | date         | NO   |     | NULL    |       |
| JOB_ID         | varchar(10)  | NO   | MUL | NULL    |       |
| SALARY         | decimal(8,2) | YES  |     | NULL    |       |
| COMMISSION_PCT | decimal(2,2) | YES  |     | NULL    |       |
| MANAGER_ID     | decimal(6,0) | YES  | MUL | NULL    |       |
| DEPARTMENT_ID  | decimal(4,0) | YES  | MUL | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
11 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name, from employees
    -> WHERE manager_id in
    -> (select employee_id FROM employees
    -> WHERE department_id
    -> IN (SELECT department_id
    -> FROM departments WHERE location_id
    -> IN (SELECT location_id FROM locations WHERE country_id='us')));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'from employees
WHERE manager_id in
(select employee_id FROM employees
WHERE dep' at line 1
MariaDB [test]> select first_name, last_name from employees
    -> WHERE manager_id in
    -> (select employee_id FROM employees
    ->  WHERE department_id
    -> IN (SELECT department_id
    -> FROM departments WHERE location_id
    -> IN (SELECT location_id FROM locations WHERE country_id='us')));
+-------------+-------------+
| first_name  | last_name   |
+-------------+-------------+
| Neena       | Kochhar     |
| Lex         | De Haan     |
| Alexander   | Hunold      |
| Bruce       | Ernst       |
| David       | Austin      |
| Valli       | Pataballa   |
| Diana       | Lorentz     |
| Nancy       | Greenberg   |
| Daniel      | Faviet      |
| John        | Chen        |
| Ismael      | Sciarra     |
| Jose Manuel | Urman       |
| Luis        | Popp        |
| Den         | Raphaely    |
| Alexander   | Khoo        |
| Shelli      | Baida       |
| Sigal       | Tobias      |
| Guy         | Himuro      |
| Karen       | Colmenares  |
| Matthew     | Weiss       |
| Adam        | Fripp       |
| Payam       | Kaufling    |
| Shanta      | Vollman     |
| Kevin       | Mourgos     |
| Julia       | Nayer       |
| Irene       | Mikkilineni |
| James       | Landry      |
| Steven      | Markle      |
| Laura       | Bissot      |
| Mozhe       | Atkinson    |
| James       | Marlow      |
| TJ          | Olson       |
| Jason       | Mallin      |
| Michael     | Rogers      |
| Ki          | Gee         |
| Hazel       | Philtanker  |
| Renske      | Ladwig      |
| Stephen     | Stiles      |
| John        | Seo         |
| Joshua      | Patel       |
| Trenna      | Rajs        |
| Curtis      | Davies      |
| Randall     | Matos       |
| Peter       | Vargas      |
| John        | Russell     |
| Karen       | Partners    |
| Alberto     | Errazuriz   |
| Gerald      | Cambrault   |
| Eleni       | Zlotkey     |
| Winston     | Taylor      |
| Jean        | Fleaur      |
| Martha      | Sullivan    |
| Girard      | Geoni       |
| Nandita     | Sarchand    |
| Alexis      | Bull        |
| Julia       | Dellinger   |
| Anthony     | Cabrio      |
| Kelly       | Chung       |
| Jennifer    | Dilly       |
| Timothy     | Gates       |
| Randall     | Perkins     |
| Sarah       | Bell        |
| Britney     | Everett     |
| Samuel      | McCain      |
| Vance       | Jones       |
| Alana       | Walsh       |
| Kevin       | Feeney      |
| Donald      | OConnell    |
| Douglas     | Grant       |
| Jennifer    | Whalen      |
| Michael     | Hartstein   |
| Susan       | Mavris      |
| Hermann     | Baer        |
| Shelley     | Higgins     |
| William     | Gietz       |
+-------------+-------------+
75 rows in set (0.00 sec)

MariaDB [test]> desc employees;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| EMPLOYEE_ID    | decimal(6,0) | NO   | PRI | 0       |       |
| FIRST_NAME     | varchar(20)  | YES  |     | NULL    |       |
| LAST_NAME      | varchar(25)  | NO   | MUL | NULL    |       |
| EMAIL          | varchar(25)  | NO   | UNI | NULL    |       |
| PHONE_NUMBER   | varchar(20)  | YES  |     | NULL    |       |
| HIRE_DATE      | date         | NO   |     | NULL    |       |
| JOB_ID         | varchar(10)  | NO   | MUL | NULL    |       |
| SALARY         | decimal(8,2) | YES  |     | NULL    |       |
| COMMISSION_PCT | decimal(2,2) | YES  |     | NULL    |       |
| MANAGER_ID     | decimal(6,0) | YES  | MUL | NULL    |       |
| DEPARTMENT_ID  | decimal(4,0) | YES  | MUL | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
11 rows in set (0.00 sec)

MariaDB [test]> select manager_id from employees;
+------------+
| manager_id |
+------------+
|          0 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        101 |
|        101 |
|        101 |
|        101 |
|        101 |
|        102 |
|        103 |
|        103 |
|        103 |
|        103 |
|        108 |
|        108 |
|        108 |
|        108 |
|        108 |
|        114 |
|        114 |
|        114 |
|        114 |
|        114 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        145 |
|        145 |
|        145 |
|        145 |
|        145 |
|        145 |
|        146 |
|        146 |
|        146 |
|        146 |
|        146 |
|        146 |
|        147 |
|        147 |
|        147 |
|        147 |
|        147 |
|        147 |
|        148 |
|        148 |
|        148 |
|        148 |
|        148 |
|        148 |
|        149 |
|        149 |
|        149 |
|        149 |
|        149 |
|        149 |
|        201 |
|        205 |
+------------+
107 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name from employees where employee_id in (select manager_id from employees_;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 1
MariaDB [test]> select first_name, last_name from employees where employee_id in (select manager_id from employees);
+------------+-----------+
| first_name | last_name |
+------------+-----------+
| Steven     | King      |
| Neena      | Kochhar   |
| Lex        | De Haan   |
| Alexander  | Hunold    |
| Nancy      | Greenberg |
| Den        | Raphaely  |
| Matthew    | Weiss     |
| Adam       | Fripp     |
| Payam      | Kaufling  |
| Shanta     | Vollman   |
| Kevin      | Mourgos   |
| John       | Russell   |
| Karen      | Partners  |
| Alberto    | Errazuriz |
| Gerald     | Cambrault |
| Eleni      | Zlotkey   |
| Michael    | Hartstein |
| Shelley    | Higgins   |
+------------+-----------+
18 rows in set (0.00 sec)

MariaDB [test]> desc employees;
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| EMPLOYEE_ID    | decimal(6,0) | NO   | PRI | 0       |       |
| FIRST_NAME     | varchar(20)  | YES  |     | NULL    |       |
| LAST_NAME      | varchar(25)  | NO   | MUL | NULL    |       |
| EMAIL          | varchar(25)  | NO   | UNI | NULL    |       |
| PHONE_NUMBER   | varchar(20)  | YES  |     | NULL    |       |
| HIRE_DATE      | date         | NO   |     | NULL    |       |
| JOB_ID         | varchar(10)  | NO   | MUL | NULL    |       |
| SALARY         | decimal(8,2) | YES  |     | NULL    |       |
| COMMISSION_PCT | decimal(2,2) | YES  |     | NULL    |       |
| MANAGER_ID     | decimal(6,0) | YES  | MUL | NULL    |       |
| DEPARTMENT_ID  | decimal(4,0) | YES  | MUL | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
11 rows in set (0.00 sec)

MariaDB [test]> desc manager_id;
ERROR 1146 (42S02): Table 'test.manager_id' doesn't exist
MariaDB [test]>  select first_name, last_name,employee_id,manager_id from employees where employee_id in (select manager_id from employees group by manager_id);
+------------+-----------+-------------+------------+
| first_name | last_name | employee_id | manager_id |
+------------+-----------+-------------+------------+
| Steven     | King      |         100 |          0 |
| Neena      | Kochhar   |         101 |        100 |
| Lex        | De Haan   |         102 |        100 |
| Alexander  | Hunold    |         103 |        102 |
| Nancy      | Greenberg |         108 |        101 |
| Den        | Raphaely  |         114 |        100 |
| Matthew    | Weiss     |         120 |        100 |
| Adam       | Fripp     |         121 |        100 |
| Payam      | Kaufling  |         122 |        100 |
| Shanta     | Vollman   |         123 |        100 |
| Kevin      | Mourgos   |         124 |        100 |
| John       | Russell   |         145 |        100 |
| Karen      | Partners  |         146 |        100 |
| Alberto    | Errazuriz |         147 |        100 |
| Gerald     | Cambrault |         148 |        100 |
| Eleni      | Zlotkey   |         149 |        100 |
| Michael    | Hartstein |         201 |        100 |
| Shelley    | Higgins   |         205 |        101 |
+------------+-----------+-------------+------------+
18 rows in set (0.00 sec)

MariaDB [test]> select average salary from employees;
ERROR 1054 (42S22): Unknown column 'average' in 'field list'
MariaDB [test]> select avg(salary
    -> );
ERROR 1054 (42S22): Unknown column 'salary' in 'field list'
MariaDB [test]> select avg(salary) from employees;
+-------------+
| avg(salary) |
+-------------+
| 6461.682243 |
+-------------+
1 row in set (0.00 sec)

MariaDB [test]> select first_name, last_name, salary from employees where salary >(select avg(salary) from employees);
+-------------+------------+----------+
| first_name  | last_name  | salary   |
+-------------+------------+----------+
| Steven      | King       | 24000.00 |
| Neena       | Kochhar    | 17000.00 |
| Lex         | De Haan    | 17000.00 |
| Alexander   | Hunold     |  9000.00 |
| Nancy       | Greenberg  | 12000.00 |
| Daniel      | Faviet     |  9000.00 |
| John        | Chen       |  8200.00 |
| Ismael      | Sciarra    |  7700.00 |
| Jose Manuel | Urman      |  7800.00 |
| Luis        | Popp       |  6900.00 |
| Den         | Raphaely   | 11000.00 |
| Matthew     | Weiss      |  8000.00 |
| Adam        | Fripp      |  8200.00 |
| Payam       | Kaufling   |  7900.00 |
| Shanta      | Vollman    |  6500.00 |
| John        | Russell    | 14000.00 |
| Karen       | Partners   | 13500.00 |
| Alberto     | Errazuriz  | 12000.00 |
| Gerald      | Cambrault  | 11000.00 |
| Eleni       | Zlotkey    | 10500.00 |
| Peter       | Tucker     | 10000.00 |
| David       | Bernstein  |  9500.00 |
| Peter       | Hall       |  9000.00 |
| Christopher | Olsen      |  8000.00 |
| Nanette     | Cambrault  |  7500.00 |
| Oliver      | Tuvault    |  7000.00 |
| Janette     | King       | 10000.00 |
| Patrick     | Sully      |  9500.00 |
| Allan       | McEwen     |  9000.00 |
| Lindsey     | Smith      |  8000.00 |
| Louise      | Doran      |  7500.00 |
| Sarath      | Sewall     |  7000.00 |
| Clara       | Vishney    | 10500.00 |
| Danielle    | Greene     |  9500.00 |
| Mattea      | Marvins    |  7200.00 |
| David       | Lee        |  6800.00 |
| Lisa        | Ozer       | 11500.00 |
| Harrison    | Bloom      | 10000.00 |
| Tayler      | Fox        |  9600.00 |
| William     | Smith      |  7400.00 |
| Elizabeth   | Bates      |  7300.00 |
| Ellen       | Abel       | 11000.00 |
| Alyssa      | Hutton     |  8800.00 |
| Jonathon    | Taylor     |  8600.00 |
| Jack        | Livingston |  8400.00 |
| Kimberely   | Grant      |  7000.00 |
| Michael     | Hartstein  | 13000.00 |
| Susan       | Mavris     |  6500.00 |
| Hermann     | Baer       | 10000.00 |
| Shelley     | Higgins    | 12000.00 |
| William     | Gietz      |  8300.00 |
+-------------+------------+----------+
51 rows in set (0.01 sec)

MariaDB [test]> desc jobs;
+------------+--------------+------+-----+---------+-------+
| Field      | Type         | Null | Key | Default | Extra |
+------------+--------------+------+-----+---------+-------+
| JOB_ID     | varchar(10)  | NO   | PRI |         |       |
| JOB_TITLE  | varchar(35)  | NO   |     | NULL    |       |
| MIN_SALARY | decimal(6,0) | YES  |     | NULL    |       |
| MAX_SALARY | decimal(6,0) | YES  |     | NULL    |       |
+------------+--------------+------+-----+---------+-------+
4 rows in set (0.01 sec)

MariaDB [test]> select min_salary from jobs where employees.job_id = jobs.job_id;
ERROR 1054 (42S22): Unknown column 'employees.job_id' in 'where clause'
MariaDB [test]> select first_name, last_name, salary
    -> FROM employees
    -> WHERE employees.salary = (select min_salary
    -> FROM jobs
    -> WHERE jobs
    -> WHERE employees.job_id = jobs.job_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'WHERE employees.job_id = jobs.job_id)' at line 6
MariaDB [test]>  select first_name, last_name, salary
    -> FROM employees
    -> WHERE employees.salary = (select min_salary
    -> FROM jobs
    -> WHERE employees.job_id = jobs.job_id);
+------------+------------+---------+
| first_name | last_name  | salary  |
+------------+------------+---------+
| Karen      | Colmenares | 2500.00 |
| Martha     | Sullivan   | 2500.00 |
| Randall    | Perkins    | 2500.00 |
+------------+------------+---------+
3 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name, saalry from employees WHERE salary > (select salary from employees where last_name = 'bell') order by first_name;
ERROR 1054 (42S22): Unknown column 'saalry' in 'field list'
MariaDB [test]> select first_name, last_name, salary from employees WHERE salary > (select salary from employees where last_name = 'bell') order by first_name;
+-------------+------------+----------+
| first_name  | last_name  | salary   |
+-------------+------------+----------+
| Adam        | Fripp      |  8200.00 |
| Alberto     | Errazuriz  | 12000.00 |
| Alexander   | Hunold     |  9000.00 |
| Alexis      | Bull       |  4100.00 |
| Allan       | McEwen     |  9000.00 |
| Alyssa      | Hutton     |  8800.00 |
| Amit        | Banda      |  6200.00 |
| Bruce       | Ernst      |  6000.00 |
| Charles     | Johnson    |  6200.00 |
| Christopher | Olsen      |  8000.00 |
| Clara       | Vishney    | 10500.00 |
| Daniel      | Faviet     |  9000.00 |
| Danielle    | Greene     |  9500.00 |
| David       | Lee        |  6800.00 |
| David       | Austin     |  4800.00 |
| David       | Bernstein  |  9500.00 |
| Den         | Raphaely   | 11000.00 |
| Diana       | Lorentz    |  4200.00 |
| Eleni       | Zlotkey    | 10500.00 |
| Elizabeth   | Bates      |  7300.00 |
| Ellen       | Abel       | 11000.00 |
| Gerald      | Cambrault  | 11000.00 |
| Harrison    | Bloom      | 10000.00 |
| Hermann     | Baer       | 10000.00 |
| Ismael      | Sciarra    |  7700.00 |
| Jack        | Livingston |  8400.00 |
| Janette     | King       | 10000.00 |
| Jennifer    | Whalen     |  4400.00 |
| John        | Russell    | 14000.00 |
| John        | Chen       |  8200.00 |
| Jonathon    | Taylor     |  8600.00 |
| Jose Manuel | Urman      |  7800.00 |
| Karen       | Partners   | 13500.00 |
| Kevin       | Mourgos    |  5800.00 |
| Kimberely   | Grant      |  7000.00 |
| Lex         | De Haan    | 17000.00 |
| Lindsey     | Smith      |  8000.00 |
| Lisa        | Ozer       | 11500.00 |
| Louise      | Doran      |  7500.00 |
| Luis        | Popp       |  6900.00 |
| Mattea      | Marvins    |  7200.00 |
| Matthew     | Weiss      |  8000.00 |
| Michael     | Hartstein  | 13000.00 |
| Nancy       | Greenberg  | 12000.00 |
| Nandita     | Sarchand   |  4200.00 |
| Nanette     | Cambrault  |  7500.00 |
| Neena       | Kochhar    | 17000.00 |
| Oliver      | Tuvault    |  7000.00 |
| Pat         | Fay        |  6000.00 |
| Patrick     | Sully      |  9500.00 |
| Payam       | Kaufling   |  7900.00 |
| Peter       | Hall       |  9000.00 |
| Peter       | Tucker     | 10000.00 |
| Sarath      | Sewall     |  7000.00 |
| Shanta      | Vollman    |  6500.00 |
| Shelley     | Higgins    | 12000.00 |
| Steven      | King       | 24000.00 |
| Sundar      | Ande       |  6400.00 |
| Sundita     | Kumar      |  6100.00 |
| Susan       | Mavris     |  6500.00 |
| Tayler      | Fox        |  9600.00 |
| Valli       | Pataballa  |  4800.00 |
| William     | Smith      |  7400.00 |
| William     | Gietz      |  8300.00 |
+-------------+------------+----------+
64 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name from employees where salary =( select min(salary from employees);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'from employees)' at line 1
MariaDB [test]> select first_name, last_name from employees where salary = (select min (salary) from employees);
ERROR 1370 (42000): execute command denied to user ''@'localhost' for routine 'test.min'
MariaDB [test]> select avg (salary) from employees ;
+--------------+
| avg (salary) |
+--------------+
|  6461.682243 |
+--------------+
1 row in set (0.00 sec)

MariaDB [test]> select first_name, last_name, salary from employees where salary> (select avg(salary) from employees group by department_id);
ERROR 1242 (21000): Subquery returns more than 1 row
MariaDB [test]> select avg(salary) from employees group by department_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ')' at line 1
MariaDB [test]> select avg(salary) from employees group by department_id;
+--------------+
| avg(salary)  |
+--------------+
|  7000.000000 |
|  4400.000000 |
|  9500.000000 |
|  4150.000000 |
|  6500.000000 |
|  3475.555556 |
|  5760.000000 |
| 10000.000000 |
|  8955.882353 |
| 19333.333333 |
|  8600.000000 |
| 10150.000000 |
+--------------+
12 rows in set (0.00 sec)

MariaDB [test]> select first_name, last_name, salary from employees where salary> (select avg(salary) from employees group by department_id);
ERROR 1242 (21000): Subquery returns more than 1 row
MariaDB [test]> select first_name, last_name , salary
    -> from employees
    -> where salary>
    -> (select avg (salary)
    -> from employees
    -> group by department_id);
ERROR 1242 (21000): Subquery returns more than 1 row
MariaDB [test]> select first_name, last_name, salary from employees where salary = all (select avg(salary) from employees group by department_id);
Empty set (0.00 sec)

MariaDB [test]> select first_name, last_name, salary from employees where salary = all (select avg(salary) from employees group by department_id);
Empty set (0.00 sec)

MariaDB [test]> Empty set (0.00 sec)select first_name, last_name, salary from employees where salary = any (select avg(salary) from employees group by department_id);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'Empty set (0.00 sec)select first_name, last_name, salary from employees where sa' at line 1
MariaDB [test]> select first_name, last_name, salary from employees where salary = any (select avg(salary) from employees group by department_id);
+------------+-----------+----------+
| first_name | last_name | salary   |
+------------+-----------+----------+
| Shanta     | Vollman   |  6500.00 |
| Peter      | Tucker    | 10000.00 |
| David      | Bernstein |  9500.00 |
| Oliver     | Tuvault   |  7000.00 |
| Janette    | King      | 10000.00 |
| Patrick    | Sully     |  9500.00 |
| Sarath     | Sewall    |  7000.00 |
| Danielle   | Greene    |  9500.00 |
| Harrison   | Bloom     | 10000.00 |
| Jonathon   | Taylor    |  8600.00 |
| Kimberely  | Grant     |  7000.00 |
| Jennifer   | Whalen    |  4400.00 |
| Susan      | Mavris    |  6500.00 |
| Hermann    | Baer      | 10000.00 |
+------------+-----------+----------+
14 rows in set (0.00 sec)

MariaDB [test]> desc jobs;
ERROR 1030 (HY000): Got error 22 "Invalid argument" from storage engine Aria
MariaDB [test]> select * from jobs;
+------------+---------------------------------+------------+------------+
| JOB_ID     | JOB_TITLE                       | MIN_SALARY | MAX_SALARY |
+------------+---------------------------------+------------+------------+
| AD_PRES    | President                       |      20000 |      40000 |
| AD_VP      | Administration Vice President   |      15000 |      30000 |
| AD_ASST    | Administration Assistant        |       3000 |       6000 |
| FI_MGR     | Finance Manager                 |       8200 |      16000 |
| FI_ACCOUNT | Accountant                      |       4200 |       9000 |
| AC_MGR     | Accounting Manager              |       8200 |      16000 |
| AC_ACCOUNT | Public Accountant               |       4200 |       9000 |
| SA_MAN     | Sales Manager                   |      10000 |      20000 |
| SA_REP     | Sales Representative            |       6000 |      12000 |
| PU_MAN     | Purchasing Manager              |       8000 |      15000 |
| PU_CLERK   | Purchasing Clerk                |       2500 |       5500 |
| ST_MAN     | Stock Manager                   |       5500 |       8500 |
| ST_CLERK   | Stock Clerk                     |       2000 |       5000 |
| SH_CLERK   | Shipping Clerk                  |       2500 |       5500 |
| IT_PROG    | Programmer                      |       4000 |      10000 |
| MK_MAN     | Marketing Manager               |       9000 |      15000 |
| MK_REP     | Marketing Representative        |       4000 |       9000 |
| HR_REP     | Human Resources Representative  |       4000 |       9000 |
| PR_REP     | Public Relations Representative |       4500 |      10500 |
+------------+---------------------------------+------------+------------+
19 rows in set (0.00 sec)

MariaDB [test]> desc jobd;
ERROR 1030 (HY000): Got error 22 "Invalid argument" from storage engine Aria
MariaDB [test]> desc job_id;
ERROR 1030 (HY000): Got error 22 "Invalid argument" from storage engine Aria
MariaDB [test]> desc salary;
ERROR 1030 (HY000): Got error 22 "Invalid argument" from storage engine Aria
MariaDB [test]> des salary;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'des salary' at line 1
MariaDB [test]> dec salary;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'dec salary' at line 1
MariaDB [test]> decs salary;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'decs salary' at line 1
MariaDB [test]> desc employees;
ERROR 1030 (HY000): Got error 22 "Invalid argument" from storage engine Aria
MariaDB [test]> select first_name, last_name, salary from employees where salary = all (select avg(salary) from employees group by department_id);
Empty set (0.00 sec)

MariaDB [test]> select first_name, last_nmae , job_id, salary from employees where salary>
    -> all select salary from employees
    -> ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'select salary from employees' at line 2
MariaDB [test]> select first_name, last_nmae , job_id, salary from employees where sal
    -> ;
ERROR 1054 (42S22): Unknown column 'last_nmae' in 'field list'
MariaDB [test]> SELECT b.first_name,b.last_name
    -> from employees b where not exists
    -> (select 'X' from employees a
    -> where a. manager_id = b.employee_id);
+-------------+-------------+
| first_name  | last_name   |
+-------------+-------------+
| Bruce       | Ernst       |
| David       | Austin      |
| Valli       | Pataballa   |
| Diana       | Lorentz     |
| Daniel      | Faviet      |
| John        | Chen        |
| Ismael      | Sciarra     |
| Jose Manuel | Urman       |
| Luis        | Popp        |
| Alexander   | Khoo        |
| Shelli      | Baida       |
| Sigal       | Tobias      |
| Guy         | Himuro      |
| Karen       | Colmenares  |
| Julia       | Nayer       |
| Irene       | Mikkilineni |
| James       | Landry      |
| Steven      | Markle      |
| Laura       | Bissot      |
| Mozhe       | Atkinson    |
| James       | Marlow      |
| TJ          | Olson       |
| Jason       | Mallin      |
| Michael     | Rogers      |
| Ki          | Gee         |
| Hazel       | Philtanker  |
| Renske      | Ladwig      |
| Stephen     | Stiles      |
| John        | Seo         |
| Joshua      | Patel       |
| Trenna      | Rajs        |
| Curtis      | Davies      |
| Randall     | Matos       |
| Peter       | Vargas      |
| Peter       | Tucker      |
| David       | Bernstein   |
| Peter       | Hall        |
| Christopher | Olsen       |
| Nanette     | Cambrault   |
| Oliver      | Tuvault     |
| Janette     | King        |
| Patrick     | Sully       |
| Allan       | McEwen      |
| Lindsey     | Smith       |
| Louise      | Doran       |
| Sarath      | Sewall      |
| Clara       | Vishney     |
| Danielle    | Greene      |
| Mattea      | Marvins     |
| David       | Lee         |
| Sundar      | Ande        |
| Amit        | Banda       |
| Lisa        | Ozer        |
| Harrison    | Bloom       |
| Tayler      | Fox         |
| William     | Smith       |
| Elizabeth   | Bates       |
| Sundita     | Kumar       |
| Ellen       | Abel        |
| Alyssa      | Hutton      |
| Jonathon    | Taylor      |
| Jack        | Livingston  |
| Kimberely   | Grant       |
| Charles     | Johnson     |
| Winston     | Taylor      |
| Jean        | Fleaur      |
| Martha      | Sullivan    |
| Girard      | Geoni       |
| Nandita     | Sarchand    |
| Alexis      | Bull        |
| Julia       | Dellinger   |
| Anthony     | Cabrio      |
| Kelly       | Chung       |
| Jennifer    | Dilly       |
| Timothy     | Gates       |
| Randall     | Perkins     |
| Sarah       | Bell        |
| Britney     | Everett     |
| Samuel      | McCain      |
| Vance       | Jones       |
| Alana       | Walsh       |
| Kevin       | Feeney      |
| Donald      | OConnell    |
| Douglas     | Grant       |
| Jennifer    | Whalen      |
| Pat         | Fay         |
| Susan       | Mavris      |
| Hermann     | Baer        |
| William     | Gietz       |
+-------------+-------------+
89 rows in set (0.00 sec)

MariaDB [test]> select manager_id from employees;
+------------+
| manager_id |
+------------+
|          0 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        100 |
|        101 |
|        101 |
|        101 |
|        101 |
|        101 |
|        102 |
|        103 |
|        103 |
|        103 |
|        103 |
|        108 |
|        108 |
|        108 |
|        108 |
|        108 |
|        114 |
|        114 |
|        114 |
|        114 |
|        114 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        120 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        121 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        122 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        123 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        124 |
|        145 |
|        145 |
|        145 |
|        145 |
|        145 |
|        145 |
|        146 |
|        146 |
|        146 |
|        146 |
|        146 |
|        146 |
|        147 |
|        147 |
|        147 |
|        147 |
|        147 |
|        147 |
|        148 |
|        148 |
|        148 |
|        148 |
|        148 |
|        148 |
|        149 |
|        149 |
|        149 |
|        149 |
|        149 |
|        149 |
|        201 |
|        205 |
+------------+
107 rows in set (0.02 sec)

MariaDB [test]> select employee_id from employees where employee_id not in (select manager_id from employees group by manager_id);
+-------------+
| employee_id |
+-------------+
|         104 |
|         105 |
|         106 |
|         107 |
|         109 |
|         110 |
|         111 |
|         112 |
|         113 |
|         115 |
|         116 |
|         117 |
|         118 |
|         119 |
|         125 |
|         126 |
|         127 |
|         128 |
|         129 |
|         130 |
|         131 |
|         132 |
|         133 |
|         134 |
|         135 |
|         136 |
|         137 |
|         138 |
|         139 |
|         140 |
|         141 |
|         142 |
|         143 |
|         144 |
|         150 |
|         151 |
|         152 |
|         153 |
|         154 |
|         155 |
|         156 |
|         157 |
|         158 |
|         159 |
|         160 |
|         161 |
|         162 |
|         163 |
|         164 |
|         165 |
|         166 |
|         167 |
|         168 |
|         169 |
|         170 |
|         171 |
|         172 |
|         173 |
|         174 |
|         175 |
|         176 |
|         177 |
|         178 |
|         179 |
|         180 |
|         181 |
|         182 |
|         183 |
|         184 |
|         185 |
|         186 |
|         187 |
|         188 |
|         189 |
|         190 |
|         191 |
|         192 |
|         193 |
|         194 |
|         195 |
|         196 |
|         197 |
|         198 |
|         199 |
|         200 |
|         202 |
|         203 |
|         204 |
|         206 |
+-------------+
89 rows in set (0.00 sec)

MariaDB [test]> select 'x' from employees;
+---+
| x |
+---+
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
| x |
+---+
107 rows in set (0.00 sec)

MariaDB [test]> select employee_id, first_name, last_name,
    -> (select department_name from departments d
    -> where e.department_id = d.department_id) department
    -> from employees e order by department;
+-------------+-------------+-------------+------------------+
| employee_id | first_name  | last_name   | department       |
+-------------+-------------+-------------+------------------+
|         178 | Kimberely   | Grant       | NULL             |
|         205 | Shelley     | Higgins     | Accounting       |
|         206 | William     | Gietz       | Accounting       |
|         200 | Jennifer    | Whalen      | Administration   |
|         100 | Steven      | King        | Executive        |
|         102 | Lex         | De Haan     | Executive        |
|         101 | Neena       | Kochhar     | Executive        |
|         112 | Jose Manuel | Urman       | Finance          |
|         113 | Luis        | Popp        | Finance          |
|         111 | Ismael      | Sciarra     | Finance          |
|         110 | John        | Chen        | Finance          |
|         109 | Daniel      | Faviet      | Finance          |
|         108 | Nancy       | Greenberg   | Finance          |
|         203 | Susan       | Mavris      | Human Resources  |
|         103 | Alexander   | Hunold      | IT               |
|         104 | Bruce       | Ernst       | IT               |
|         105 | David       | Austin      | IT               |
|         107 | Diana       | Lorentz     | IT               |
|         106 | Valli       | Pataballa   | IT               |
|         202 | Pat         | Fay         | Marketing        |
|         201 | Michael     | Hartstein   | Marketing        |
|         204 | Hermann     | Baer        | Public Relations |
|         118 | Guy         | Himuro      | Purchasing       |
|         114 | Den         | Raphaely    | Purchasing       |
|         115 | Alexander   | Khoo        | Purchasing       |
|         116 | Shelli      | Baida       | Purchasing       |
|         117 | Sigal       | Tobias      | Purchasing       |
|         119 | Karen       | Colmenares  | Purchasing       |
|         163 | Danielle    | Greene      | Sales            |
|         162 | Clara       | Vishney     | Sales            |
|         161 | Sarath      | Sewall      | Sales            |
|         160 | Louise      | Doran       | Sales            |
|         159 | Lindsey     | Smith       | Sales            |
|         158 | Allan       | McEwen      | Sales            |
|         157 | Patrick     | Sully       | Sales            |
|         156 | Janette     | King        | Sales            |
|         155 | Oliver      | Tuvault     | Sales            |
|         154 | Nanette     | Cambrault   | Sales            |
|         153 | Christopher | Olsen       | Sales            |
|         164 | Mattea      | Marvins     | Sales            |
|         165 | David       | Lee         | Sales            |
|         167 | Amit        | Banda       | Sales            |
|         177 | Jack        | Livingston  | Sales            |
|         176 | Jonathon    | Taylor      | Sales            |
|         175 | Alyssa      | Hutton      | Sales            |
|         174 | Ellen       | Abel        | Sales            |
|         173 | Sundita     | Kumar       | Sales            |
|         172 | Elizabeth   | Bates       | Sales            |
|         171 | William     | Smith       | Sales            |
|         170 | Tayler      | Fox         | Sales            |
|         169 | Harrison    | Bloom       | Sales            |
|         168 | Lisa        | Ozer        | Sales            |
|         179 | Charles     | Johnson     | Sales            |
|         152 | Peter       | Hall        | Sales            |
|         145 | John        | Russell     | Sales            |
|         146 | Karen       | Partners    | Sales            |
|         147 | Alberto     | Errazuriz   | Sales            |
|         148 | Gerald      | Cambrault   | Sales            |
|         149 | Eleni       | Zlotkey     | Sales            |
|         150 | Peter       | Tucker      | Sales            |
|         151 | David       | Bernstein   | Sales            |
|         166 | Sundar      | Ande        | Sales            |
|         194 | Samuel      | McCain      | Shipping         |
|         193 | Britney     | Everett     | Shipping         |
|         192 | Sarah       | Bell        | Shipping         |
|         191 | Randall     | Perkins     | Shipping         |
|         190 | Timothy     | Gates       | Shipping         |
|         189 | Jennifer    | Dilly       | Shipping         |
|         188 | Kelly       | Chung       | Shipping         |
|         187 | Anthony     | Cabrio      | Shipping         |
|         186 | Julia       | Dellinger   | Shipping         |
|         195 | Vance       | Jones       | Shipping         |
|         196 | Alana       | Walsh       | Shipping         |
|         197 | Kevin       | Feeney      | Shipping         |
|         180 | Winston     | Taylor      | Shipping         |
|         120 | Matthew     | Weiss       | Shipping         |
|         121 | Adam        | Fripp       | Shipping         |
|         122 | Payam       | Kaufling    | Shipping         |
|         123 | Shanta      | Vollman     | Shipping         |
|         124 | Kevin       | Mourgos     | Shipping         |
|         125 | Julia       | Nayer       | Shipping         |
|         199 | Douglas     | Grant       | Shipping         |
|         198 | Donald      | OConnell    | Shipping         |
|         185 | Alexis      | Bull        | Shipping         |
|         184 | Nandita     | Sarchand    | Shipping         |
|         183 | Girard      | Geoni       | Shipping         |
|         135 | Ki          | Gee         | Shipping         |
|         136 | Hazel       | Philtanker  | Shipping         |
|         137 | Renske      | Ladwig      | Shipping         |
|         138 | Stephen     | Stiles      | Shipping         |
|         139 | John        | Seo         | Shipping         |
|         140 | Joshua      | Patel       | Shipping         |
|         141 | Trenna      | Rajs        | Shipping         |
|         142 | Curtis      | Davies      | Shipping         |
|         143 | Randall     | Matos       | Shipping         |
|         134 | Michael     | Rogers      | Shipping         |
|         133 | Jason       | Mallin      | Shipping         |
|         182 | Martha      | Sullivan    | Shipping         |
|         181 | Jean        | Fleaur      | Shipping         |
|         126 | Irene       | Mikkilineni | Shipping         |
|         127 | James       | Landry      | Shipping         |
|         128 | Steven      | Markle      | Shipping         |
|         129 | Laura       | Bissot      | Shipping         |
|         130 | Mozhe       | Atkinson    | Shipping         |
|         131 | James       | Marlow      | Shipping         |
|         132 | TJ          | Olson       | Shipping         |
|         144 | Peter       | Vargas      | Shipping         |
+-------------+-------------+-------------+------------------+
107 rows in set (0.00 sec)

MariaDB [test]> select avg(salary) from employees;
+-------------+
| avg(salary) |
+-------------+
| 6461.682243 |
+-------------+
1 row in set (0.00 sec)

MariaDB [test]> select avg(salary) from employees group by department_id;
+--------------+
| avg(salary)  |
+--------------+
|  7000.000000 |
|  4400.000000 |
|  9500.000000 |
|  4150.000000 |
|  6500.000000 |
|  3475.555556 |
|  5760.000000 |
| 10000.000000 |
|  8955.882353 |
| 19333.333333 |
|  8600.000000 |
| 10150.000000 |
+--------------+
12 rows in set (0.00 sec)

MariaDB [test]> select employee_id, first_name from employees as a where salary > (select avg(salary) from employees where department_id = a.department_id);
+-------------+------------+
| employee_id | first_name |
+-------------+------------+
|         100 | Steven     |
|         103 | Alexander  |
|         104 | Bruce      |
|         108 | Nancy      |
|         109 | Daniel     |
|         114 | Den        |
|         120 | Matthew    |
|         121 | Adam       |
|         122 | Payam      |
|         123 | Shanta     |
|         124 | Kevin      |
|         137 | Renske     |
|         141 | Trenna     |
|         145 | John       |
|         146 | Karen      |
|         147 | Alberto    |
|         148 | Gerald     |
|         149 | Eleni      |
|         150 | Peter      |
|         151 | David      |
|         152 | Peter      |
|         156 | Janette    |
|         157 | Patrick    |
|         158 | Allan      |
|         162 | Clara      |
|         163 | Danielle   |
|         168 | Lisa       |
|         169 | Harrison   |
|         170 | Tayler     |
|         174 | Ellen      |
|         184 | Nandita    |
|         185 | Alexis     |
|         188 | Kelly      |
|         189 | Jennifer   |
|         192 | Sarah      |
|         193 | Britney    |
|         201 | Michael    |
|         205 | Shelley    |
+-------------+------------+
38 rows in set (0.00 sec)

MariaDB [test]> set @j=0;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> select j, employee_id from (select 2j := 2j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 0;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ':= 2j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 0' at line 1
MariaDB [test]> select j, employee_id from (select 2j := @j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 0;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ':= @j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 0' at line 1
MariaDB [test]> select j, employee_id from (select @j := @j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 0;
+------+-------------+
| j    | employee_id |
+------+-------------+
|    2 |         101 |
|    4 |         103 |
|    6 |         105 |
|    8 |         107 |
|   10 |         109 |
|   12 |         111 |
|   14 |         113 |
|   16 |         115 |
|   18 |         117 |
|   20 |         119 |
|   22 |         121 |
|   24 |         123 |
|   26 |         125 |
|   28 |         127 |
|   30 |         129 |
|   32 |         131 |
|   34 |         133 |
|   36 |         135 |
|   38 |         137 |
|   40 |         139 |
|   42 |         141 |
|   44 |         143 |
|   46 |         145 |
|   48 |         147 |
|   50 |         149 |
|   52 |         151 |
|   54 |         153 |
|   56 |         155 |
|   58 |         157 |
|   60 |         159 |
|   62 |         161 |
|   64 |         163 |
|   66 |         165 |
|   68 |         167 |
|   70 |         169 |
|   72 |         171 |
|   74 |         173 |
|   76 |         175 |
|   78 |         177 |
|   80 |         179 |
|   82 |         181 |
|   84 |         183 |
|   86 |         185 |
|   88 |         187 |
|   90 |         189 |
|   92 |         191 |
|   94 |         193 |
|   96 |         195 |
|   98 |         197 |
|  100 |         199 |
|  102 |         201 |
|  104 |         203 |
|  106 |         205 |
+------+-------------+
53 rows in set (0.00 sec)

MariaDB [test]> select j, employee_id from (select @j := @j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 1;
+------+-------------+
| j    | employee_id |
+------+-------------+
|  109 |         101 |
|  111 |         103 |
|  113 |         105 |
|  115 |         107 |
|  117 |         109 |
|  119 |         111 |
|  121 |         113 |
|  123 |         115 |
|  125 |         117 |
|  127 |         119 |
|  129 |         121 |
|  131 |         123 |
|  133 |         125 |
|  135 |         127 |
|  137 |         129 |
|  139 |         131 |
|  141 |         133 |
|  143 |         135 |
|  145 |         137 |
|  147 |         139 |
|  149 |         141 |
|  151 |         143 |
|  153 |         145 |
|  155 |         147 |
|  157 |         149 |
|  159 |         151 |
|  161 |         153 |
|  163 |         155 |
|  165 |         157 |
|  167 |         159 |
|  169 |         161 |
|  171 |         163 |
|  173 |         165 |
|  175 |         167 |
|  177 |         169 |
|  179 |         171 |
|  181 |         173 |
|  183 |         175 |
|  185 |         177 |
|  187 |         179 |
|  189 |         181 |
|  191 |         183 |
|  193 |         185 |
|  195 |         187 |
|  197 |         189 |
|  199 |         191 |
|  201 |         193 |
|  203 |         195 |
|  205 |         197 |
|  207 |         199 |
|  209 |         201 |
|  211 |         203 |
|  213 |         205 |
+------+-------------+
53 rows in set (0.00 sec)

MariaDB [test]> set @j=0;
Query OK, 0 rows affected (0.00 sec)

MariaDB [test]> select j, employee_id from (select @j := @j + 1 as j, employee_id from employees) a where MOD(a.j,2) = 1;
+------+-------------+
| j    | employee_id |
+------+-------------+
|    1 |         100 |
|    3 |         102 |
|    5 |         104 |
|    7 |         106 |
|    9 |         108 |
|   11 |         110 |
|   13 |         112 |
|   15 |         114 |
|   17 |         116 |
|   19 |         118 |
|   21 |         120 |
|   23 |         122 |
|   25 |         124 |
|   27 |         126 |
|   29 |         128 |
|   31 |         130 |
|   33 |         132 |
|   35 |         134 |
|   37 |         136 |
|   39 |         138 |
|   41 |         140 |
|   43 |         142 |
|   45 |         144 |
|   47 |         146 |
|   49 |         148 |
|   51 |         150 |
|   53 |         152 |
|   55 |         154 |
|   57 |         156 |
|   59 |         158 |
|   61 |         160 |
|   63 |         162 |
|   65 |         164 |
|   67 |         166 |
|   69 |         168 |
|   71 |         170 |
|   73 |         172 |
|   75 |         174 |
|   77 |         176 |
|   79 |         178 |
|   81 |         180 |
|   83 |         182 |
|   85 |         184 |
|   87 |         186 |
|   89 |         188 |
|   91 |         190 |
|   93 |         192 |
|   95 |         194 |
|   97 |         196 |
|   99 |         198 |
|  101 |         200 |
|  103 |         202 |
|  105 |         204 |
|  107 |         206 |
+------+-------------+
54 rows in set (0.00 sec)

MariaDB [test]> select count (distinct)salary from employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'distinct)salary from employees' at line 1
MariaDB [test]> select count (distinct )salary from employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'distinct )salary from employees' at line 1
MariaDB [test]> select count(distinct) salary from employees;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ') salary from employees' at line 1
MariaDB [test]> select distinct (salary) from employees;
+----------+
| salary   |
+----------+
| 24000.00 |
| 17000.00 |
|  9000.00 |
|  6000.00 |
|  4800.00 |
|  4200.00 |
| 12000.00 |
|  8200.00 |
|  7700.00 |
|  7800.00 |
|  6900.00 |
| 11000.00 |
|  3100.00 |
|  2900.00 |
|  2800.00 |
|  2600.00 |
|  2500.00 |
|  8000.00 |
|  7900.00 |
|  6500.00 |
|  5800.00 |
|  3200.00 |
|  2700.00 |
|  2400.00 |
|  2200.00 |
|  3300.00 |
|  2100.00 |
|  3600.00 |
|  3500.00 |
| 14000.00 |
| 13500.00 |
| 10500.00 |
| 10000.00 |
|  9500.00 |
|  7500.00 |
|  7000.00 |
|  7200.00 |
|  6800.00 |
|  6400.00 |
|  6200.00 |
| 11500.00 |
|  9600.00 |
|  7400.00 |
|  7300.00 |
|  6100.00 |
|  8800.00 |
|  8600.00 |
|  8400.00 |
|  4100.00 |
|  3400.00 |
|  3000.00 |
|  3800.00 |
|  4000.00 |
|  3900.00 |
|  4400.00 |
| 13000.00 |
|  8300.00 |
+----------+
57 rows in set (0.00 sec)

MariaDB [test]> select distinct (salary) from employees order by s1 desc;
ERROR 1054 (42S22): Unknown column 's1' in 'order clause'
MariaDB [test]> select distinct (salary) s1 from employees order by s1 desc;
+----------+
| s1       |
+----------+
| 24000.00 |
| 17000.00 |
| 14000.00 |
| 13500.00 |
| 13000.00 |
| 12000.00 |
| 11500.00 |
| 11000.00 |
| 10500.00 |
| 10000.00 |
|  9600.00 |
|  9500.00 |
|  9000.00 |
|  8800.00 |
|  8600.00 |
|  8400.00 |
|  8300.00 |
|  8200.00 |
|  8000.00 |
|  7900.00 |
|  7800.00 |
|  7700.00 |
|  7500.00 |
|  7400.00 |
|  7300.00 |
|  7200.00 |
|  7000.00 |
|  6900.00 |
|  6800.00 |
|  6500.00 |
|  6400.00 |
|  6200.00 |
|  6100.00 |
|  6000.00 |
|  5800.00 |
|  4800.00 |
|  4400.00 |
|  4200.00 |
|  4100.00 |
|  4000.00 |
|  3900.00 |
|  3800.00 |
|  3600.00 |
|  3500.00 |
|  3400.00 |
|  3300.00 |
|  3200.00 |
|  3100.00 |
|  3000.00 |
|  2900.00 |
|  2800.00 |
|  2700.00 |
|  2600.00 |
|  2500.00 |
|  2400.00 |
|  2200.00 |
|  2100.00 |
+----------+
57 rows in set (0.00 sec)

MariaDB [test]> select 5 max from employees where emp.salary =(select distinct (salary) s1 from employees order by s1 desc);
ERROR 1054 (42S22): Unknown column 'emp.salary' in 'where clause'
MariaDB [test]> select salary from employees limit 5;
+----------+
| salary   |
+----------+
| 24000.00 |
| 17000.00 |
| 17000.00 |
|  9000.00 |
|  6000.00 |
+----------+
5 rows in set (0.00 sec)

MariaDB [test]>

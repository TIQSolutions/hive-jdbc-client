# Apache Hive JDBC driver package

This project want provide a driver package to access Hive, Hive2 and Impala services via JDBC.
It refers to the maven artifacts provided by [Cloudera Inc.](http://www.cloudera.com/) shipped 
with their [Hive clone](https://github.com/cloudera/hive).

# Version status

# How to run tests
## Prerequisites

For running the test you should prepare an existing Hive service with a table called 'JdbcTest'.

	CREATE TABLE IF NOT EXISTS `JdbcTest` 
	( 
		`id` int , 
		`random` int , 
		`sum_randoms` bigint , 
		`var_1` string ,
		`var_2` string ,
		`var_3` string ,
		`var_4` string ,
		`var_5` string ,
		`var_6` string
	) 
	ROW FORMAT DELIMITED FIELDS TERMINATED BY ';'

Also you have to load the test data from `src/test/resources/test.csv` into this table. 

	LOAD DATA INPATH '<path_to_uploaded_file>/test.csv' INTO TABLE `JdbcTest`

## Running

To start only the tests: `mvn test -P test`  
To test and assembly at same time: `mvn verify -P test`

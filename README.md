# Apache Hive JDBC driver package

This project wants to provide a driver package to access Hive, Hive2 and Impala services via JDBC.
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

## Configuring

Copy the file 'src/test/resources/test.properties.sample' to 'src/test/resources/test.properties' and change it 
to match your environment.

## Running

To start only the tests: `mvn test -P test`  
To test and assembly at same time: `mvn verify -P test`

# How to contribute
## Test using a special environment

Please help us to verify the several branches with corresponding server environments. Before you run the
test suite, please make sure it is up to date with branch 'TestSuite'. Once you have tested, please 
submit an issue with label 'verification' and information about the versions of running hive and/or 
impala services. Please append the test results also.

## Extending the test suite

To extend the test suite, feel free to fork the project, switch to branch 'TestSuite', edit the 'JdbcTest' class 
and send us a pull request. Please add information about your test as described above.

## Optimize driver by excluding needless dependencies

As [Cloudera Inc.](http://www.cloudera.com/) provides server and client site dependencies together in there 
hive-jdbc pom, there are some needless dependencies for a driver package. Be confident to fork the project and
exclude unnecessary artefacts to get a smaller package. Do not forget to test and create a pull request with 
the results.

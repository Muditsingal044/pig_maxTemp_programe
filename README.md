# pig_maxTemp_programe
*********************************
MaxTemp Program:
*********************************

CMD ->

1. touch temperatures.csv

2. open temperatures.csv and paste it

year,temperature
2000,25.4
2000,26.8
2000,24.5
2001,27.2
2001,28.9
2001,26.1
2002,23.8
2002,25.6
2002,24.7
(ctrl+z)


4. hadoop fs -mkdir /pig_data
5. hadoop fs -put temperatures.csv /pig_data
6. pig

## grunt > cmd ...........

## Load data 
1. data = LOAD 'hdfs://localhost:9000/Pig_data/temperatures.csv' USING PigStorage(',') AS (year:int, temperature:double);

## Group data by year
2. grouped_data = GROUP data BY year;

## For each group (year), calculate the maximum temperature
3. max_temps = FOREACH grouped_data GENERATE group AS year, MAX(data.temperature) AS max_temperature;

## Store the results
4. STORE max_temps INTO 'output_directory1' USING PigStorage(',');

## output
5. fs -cat /output_directory1/part-r-00000


***************************************** THANKYOU ******************************************

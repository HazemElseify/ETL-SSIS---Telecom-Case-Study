# ETL-SSIS---Telecom-Case-Study

A telecommunications company contacted you as an ETL Consultant/Developer to do the data storage process

1. For a company that has a system that saves a csv file periodically every 5 minutes, this file includes the basic data of the various transactions made by customers during a specified period of time.

2. The company provided you with the following table which shows the data stored in the CSV file
1. 
ColumnName     |     DataType    |    Length   |   IsNullable    |   Sample
---------------|-----------------|-------------|-----------------|------------
ID             |       Int       |             |    False        |    156
IMSI           |      String     |      9      |    False        |   310120265
IMEI           |      String     |      14     |    True         |490154203237518
CELL |Int| |False |123
LAC| Int | |False |12
EVENT_TYPE| String| 1 |True |1
EVENT_TS| Timestamp| | False| 16/1/2020 7:45:43


3. The required processing (ETL) to be completed on this data before it is stored in the database
1. 
ColumnName |MappingRules  |TargetModel
-----------|--------------|----------
ID| As-is |Transaction_id
IMSI| As-is, reject the record if null |IMSI
IMSI |Join with IMSI reference and get subscriber id,add -99999 if null |subscriber_id
IMEI |Substring first 8 chars, if null or size is less than 15 add -99999 | TAC
IMEI |Substring last 6 chars, if null or size is less than 15 add -99999|SNR
IMEI |As-is |IMEI
CELL |As-is, reject the record if null |CELL
LAC  |As-is, reject the record if null |LAC
EVENT_TYPE |As-is |EVENT_TYPE
EVENT_TS |Validate the timestamp format to be YYYY-MM-DD HH:MM:SS, reject the record if null |EVENT_TS

4.  records rejected movements will be stored in a separate table, with the file name being recorded as CSV

5. create audit table During the process of recording data in the database, 
there is some additional data that needs to be recorded to ensure the quality of the data storage process

6. After completing the process of storing the data in the database according to the above conditions, move the csv file to
Another folder

7. reference <aref>https://www.youtube.com/playlist?list=PLcAbhg_RWLaK-lCH5GxnaVfyeGjrm3QH8








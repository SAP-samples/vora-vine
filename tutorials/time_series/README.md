
## Time Series in SAP Vora

### Create Series table 

1. Open the vora tools.

2. Select the '+' button on the left and select 'Create Partition Scheme'.

   ![Alt text](./images/TS1.JPG "Optional title")
   
3. Name the partition scheme as 'PS_TS' and provide the settings as below.

   ![Alt text](./images/TS2.JPG "Optional title")
   
4. Click on 'ADD' button and then 'CLOSE'. 

5. Again click on ‘+’ button and select ‘Create Series Table’.

   ![Alt text](./images/1.JPG "Optional title")

3. Enter name ‘SENSOR_DATA_MOD’ and Engine would remain same as Time Series. Choose File System as HDFS and file path as ‘/user/vora/sensor.csv’ and CSV Skip value would be 1.

   ![Alt text](./images/TS3.JPG "Optional title")

4. Click next to navigate to column details.
5. In column details, Edit the column names and give the name as TEMP, HUM, and TS.
6. Column with timestamp or date as data type can be selected as period column. Check period check box against TS column.

   ![Alt text](./images/TS4.JPG "Optional title")

7. In the right panel we can add additional property for series table. Add partition scheme 'PS_TS' by clicking the '+' sign and give partition parameter as 'TS'.

   ![Alt text](./images/TS5.JPG "Optional title")
   
   ![Alt text](./images/partition_parameter.JPG "Optional title")

8. Specify the range expression as given below.

   ![Alt text](./images/5.jpg "Optional title")
   
9. Click on Finish.

   ![Alt text](./images/TS6.JPG "Optional title")

### Create a view with Auto Correlation

1. Click on ‘+’ button in the left navigation tree, and select ‘Create View’ option.
2. Enter the view name as ‘VIEW_AC’. Type will remain sql. Click OK

   ![Alt text](./images/TS7.JPG "Optional title")

3. After creating view , add time series table function from the tool bar. Enter name as ‘TableFunction_AC’ 
4. Select Type ‘Auto Correlation’ and click on OK

   ![Alt text](./images/TS9.JPG "Optional title")

5. Add ‘SENDOR_DATA_MOD’ table using the ‘+’ option in the toolbar or drag and drop table from the left side panel.
6. Select ‘Temp’ as Descriptor and add 10 for Max Time Lag in the right-side pane.

   ![Alt text](./images/9.png "Optional title")

7. Go back to the main view using breadcrumb. Add all columns to the output.
8. Click on save to save the view and click on data preview to see the data preview.

   ![Alt text](./images/TS10.JPG "Optional title")

### Data Visualization for Time Series Engine

1. Click on ‘SENSOR_DATA_MOD’ to visualize ans select the 'CHART' tab.

   ![Alt text](./images/TS11.JPG "Optional title")

2. Select 'Granulize'

   ![Alt text](./images/TS12.JPG "Optional title")
   
3. Configure the below properties of chart.

   ![Alt text](./images/TS17.JPG "Optional title")

4. Click on ‘Apply’ to generate graph for time series table. Default chart selection would be line chart.

   ![Alt text](./images/TS16.JPG "Optional title")

5. We see two line chart. The below one is lower resolution chart.  Select a small section of lower chart. It will load higher resolution data on the selected range in the upper line chart.

   ![Alt text](./images/15.jpg "Optional title")








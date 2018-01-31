
## Time Series in SAP Vora

### Create Series table 

1. Open Sql Editor and create partition function
and partition scheme using the following command. Click on ‘Execute all’.

   ```sql
       CREATE PARTITION FUNCTION PF_TS(TS TIMESTAMP) AS RANGE
       BOUNDARIES(TIMESTAMP '2017-01-20 00:00:00', TIMESTAMP '2017-02-10 00:00:00')
       USING com.sap.spark.engines;         
    
       CREATE PARTITION SCHEME PS_TS USING PF_TS USING com.sap.spark.engines;
    ```
 
 
    ![Alt text](./images/1.png "Optional title")
 
2. Go to modeler and click on ‘+’ button and select ‘Create Series Table’.

   ![Alt text](./images/2.png "Optional title")

3. Enter name ‘SENSOR_DATA_MOD’ and Data Source Type would and Engine would remain same. Enter file path as ‘/user/vora/sensor.csv’ and CSV Skip value would be 1.

   ![Alt text](./images/3.jpg "Optional title")

4. Click next to navigate to column details.
5. Add columns by clicking on ‘add’ button as show below. Add three column TEMP, HUM, and TS in the table.
6. Column with timestamp or date as data type can be selected as period column. Check period check box against TS column.

   ![Alt text](./images/4.jpg "Optional title")

7. In the right panel we can add additional property for series table. Add partition scheme 'PS_TS' by clicking the '+' sign and give partition parameter as 'TS'.

   ![Alt text](./images/partitionscheme.JPG "Optional title")
   
   ![Alt text](./images/partition_parameter.JPG "Optional title")

8. Specify the range expression as given below.

   ![Alt text](./images/5.jpg "Optional title")

### Create a view with Auto Correlation

1. Click on ‘+’ button in the left navigation tree, and select ‘Create View’ option.
2. Enter the view name as ‘VIEW_AC’. Type will remain sql. Click OK

   ![Alt text](./images/7.png "Optional title")

3. After creating view , add time series table function from the tool bar. Enter name as ‘TableFunction_AC’ 
4. Select Type ‘Auto Correlation’ and click on OK

   ![Alt text](./images/8.png "Optional title")

5. Add ‘SENDOR_DATA_MOD’ table using the ‘+’ option in the toolbar or drag and drop table from the left side panel.
6. Select ‘Temp’ as Descriptor and add 10 for Max Time Lag in the right-side pane.

   ![Alt text](./images/9.png "Optional title")

7. Go back to the main view using breadcrumb. Add all columns to the output.
8. Click on save to save the view and click on data preview to see the data preview.

   ![Alt text](./images/10.jpg "Optional title")

### Data Visualization for Time Series Engine

1. Go to Data browser and click on ‘SENSOR_DATA_MOD’ to visualize.

   ![Alt text](./images/11.png "Optional title")

2. Click on the chart tab and select 'Granulize'
3. Configure the below properties of chart.

   ![Alt text](./images/12.jpg "Optional title")

4. Click on ‘Apply’ to generate graph for time series table. Default chart selection would be line chart.

   ![Alt text](./images/14.png "Optional title")

5. We see two line chart. The below one is lower resolution chart.  Select a small section of lower chart. It will load higher resolution data on the selected range in the upper line chart.

   ![Alt text](./images/15.jpg "Optional title")








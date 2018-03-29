
## Graph Engine in SAP Vora

### Create a Graph

1. Open the vora tools.

2. Select the '+' button on the left and select 'Create Partition Scheme'.

   ![Alt text](./images/1.jpg "Optional title")
   
3. Name the partition scheme as 'PSG_EMP_MOD' and provide the settings as below.

   ![Alt text](./images/2.jpg "Optional title")
   
4. Click on 'ADD' button and then 'CLOSE'. 
 
5. Enter the graph name as “EMPLOYEE_PARTITIONED”. Add “EMPLOYEES_GRAPH.jsg” file (/user/vora/EMPLOYEES_GRAPH.jsg). Click finish to create graph.

   ![Alt text](./images/3.jpg "Optional title")

6. Once graph is created, It will open the summary page for the graph with edge and node summary.

   ![Alt text](./images/4.jpg "Optional title")
 
7. Select “EMPLOYEE” node type in the drop down for Node Details panel. The list of employees will be displayed in table.

   ![Alt text](./images/5.jpg "Optional title")
   
8. For visualizing the graph, right click on the "EMPLOYEE_PARTITIONED" graph and select 'Data Preview'.

   ![Alt text](./images/Vis1.JPG "Optional title")
   
9. It will open the summary page of the graph. Switch to 'VISUALIZATION' tab. It will load the graphical representation of the graph.

   ![Alt text](./images/vis2.JPG "Optional title")
   
10. Select a node. The details of node will be displayed in the right-hand side pane.

   ![Alt text](./images/vis3.JPG "Optional title")
   
11. Click on config tab and Check “show node ID” check box. Click on apply. Node ID of each node will be displayed in the graph view.

   ![Alt text](./images/vis4.JPG "Optional title")
   
12. Switch back to GENERAL tab. Search node with node id 4 using search box. The corresponding node will be highlighted and node details will be loaded in the selection section on right pane.

   ![Alt text](./images/10.jpg "Optional title")
 
### Create a view with Graph

1. Go to the modeler and  Click on ‘+’ button in the navigation bar and select ‘create view’ option.

   ![Alt text](./images/6.jpg "Optional title")
   
2. Enter Name as ‘GRAPH_VIEW’. Type will remain same. Click OK

   ![Alt text](./images/7.jpg "Optional title")
 
3. Drag and drop the ‘EMPLOYEE_PARTITIONED’ graph from the left side pane. It will show the metadata viewer. 
4. Here you can see node, edges and their relationship.

   ![Alt text](./images/12.jpg "Optional title")

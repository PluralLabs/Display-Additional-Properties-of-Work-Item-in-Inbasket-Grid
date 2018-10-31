# Display Additional Properties of Work Item in Inbasket Grid

Adds a coloumn on InBasket Grid to Display property of  Work Item for Workflow Tasks

#### **How it works:**
Whenever workflow tasks is created additional property realted to work item is displayed in In-Basket Grid

#### **Project Details:**

 Built Using: Aras 11.0 SP12

#### **Browsers Tested:**  
Google Chrome 69

#### **Installation:**

**Important!** Always back up your code tree and database before applying an import package or code tree patch!


#### **Pre-requisites:**

 1. Aras Innovator installed (version 11.0 SP12)
 2. Display Properties in Inbasket Grid Package


#### **Installation Steps:**

 Backup your database and store the BAK file in a safe place.
 
> **Important!** To add property to the InBasket Item type follow the steps as below

 1. Log on to Aras Innovator with administrative privileges.
 2. Navigate to Administration --> ItemTypes. 
 3. From the grid, search for InBasket Task Item and open the Item for editing.  
 4. Click the Poly Sources tab. 
The Poly Source Items appear as below. 
<img width="957" alt="1" src="https://user-images.githubusercontent.com/37924741/47774291-9c865800-dd12-11e8-841d-3d35d8fe3622.PNG">
 You need to edit and add the property to each of the Poly Source Items.  Start with the Workflow Task Item. 
 5.  Right-click on the Workflow Task and select View ‘ItemType’. 
 The Workflow Task Item window appears. 
<img width="959" alt="2" src="https://user-images.githubusercontent.com/37924741/47777815-9183f580-dd1b-11e8-92f3-242f27ad6a7d.PNG">
 6. Click on lock icon to edit the Workflow Task Item. In the Properties tab, click  to create a new property.
 A blank row is added in the relationship grid. 
 7. Provide the required information for the property. Here we add the details for Description column.
 - Name: description
 - Label: Description
 - Data Type: Text
 8. Click Save, Unlock and Close on the Workflow Task Item window. 
 9. Repeat step 1 to step 8 for Project Task. 
 10. Close the InBasket Task Item window.  
 
 **Rebuilding SQL Views**
 
 > Rebuilding SQL View for Workflow Task Poly Source Item 
 1. Log on to Aras Innovator with administrative privileges.  
 2. Navigate to Administration --> SQLs.  
 3. Rebuild SQL view for Workflow Item Task.  
 4. From the search grid, search Workflow_Task_Step01_Drop.  
 5. Select Workflow_Task_Step01_Drop in the search grid, right-click and select **SQL Execute** from the context menu.  
 6. From the search grid, open Workflow_Task_Step02_Create_Tmp_View. 
 7. Click on lock icon to edit the Workflow_Task_Step02_Create_Tmp_View. 
 8.  In SQL field, add the following line: 
 **CONVERT(NVARCHAR(128), NULL) AS DESCRIPTION**
 <img width="576" alt="3" src="https://user-images.githubusercontent.com/37924741/47778901-e45eac80-dd1d-11e8-8ed6-4bdacc62f504.png">
 9. Click  Save and click  Unlock. 
 10. From **Actions** menu, click **SQL Execute**. 
 11. Close the window. 
 12. From the search grid, search Workflow_Task_Step03_Rename_View.
 13. Select Workflow_Task_Step03_Rename_View in the search grid, use the right mouse button (right-click) and select SQL Execute from the context menu. 
  
 > Rebuilding SQL View for Project Task Poly Source Item 
 1. From the search grid, search Project_Task_Step01_Drop.   
 2.  Select Project_Task_Step01_Drop in the search grid, right-click and select **SQL Execute** from the context menu. 
 3. From the search grid, open Project_Task_Step02_Create_Tmp_View.
 4. Click on lock icon to edit the Project_Task_Step02_Create_Tmp_View. 
 5. In SQL field, add the following line: 
**CONVERT(NVARCHAR(128), NULL) AS DESCRIPTION**
<img width="576" alt="4" src="https://user-images.githubusercontent.com/37924741/47779536-4e2b8600-dd1f-11e8-8c2b-0db9e41c9f08.png">
6. Click  Save and click  Unlock. 
7. From **Actions** menu, click **SQL Execute**. 
8. Close the window.  
9. From the search grid, search Project_Task_Step03_Rename_View.
10. Select Project_Task_Step03_Rename_View in the search grid, use right-click **SQL Execute** from the context menu. 
11. From the search grid, search Project_Task_Step04_Create_Trigger.
12. Select Project_Task_Step04_Create_Trigger in the search grid, right-click and select **SQL Execute** from the context menu. 

  >  Adding the column to the InBasket Task Item
  1.  Log on to Aras Innovator with administrative privileges.  
  2. Navigate to Administration --> ItemType.  
  3. From the grid, search for Workflow Task Item and open the Item for editing.  
  4. Save, unlock, and close the Workflow Task Item.  
  5. Repeat steps 3 and 4 for Project Task Item and Meeting Task Item
  6. From the grid, search for InBasket Task Item and open the Item for editing. 
  7.  In the Properties tab, create a new property. 
  8. A blank row is added in the relationship grid.   
  9. Provide the required information for the property.  
  10. In our example, we add the details for  Description column.
 - Name: description
 - Label: Description
 - Data Type: Text 
 11. Click Save, Unlock and Close in the InBasket Task Item window
 
 >  Import Package
 1. Open up the Aras Package Import tool.
 2. Enter your login credentials and click Login
**Note: You must login as root for the package import to succeed!**
3. Enter the package name in the TargetRelease field.
**Optional: Enter a description in the Description field.**
4. Enter the path to your local ..\ Display Properties in Inbasket Grid\imports.mf file in the Manifest File field.
15. Select Display Properties in Inbasket Grid in the Available for Import field.
16. Select Type = Merge and Mode = Thorough Mode.
17. Click Import in the top left corner.
18. Close the Aras Package Import tool.
 
#### **Usage:**
1. Once Workflow Task is created, property named description in work item will be displayed in Description Column on Inbasket Grid 
2. If Workflow Task belongs to Item Type Part, Express DCO, CAD, ECN,ECR discription will be dispalyed in newly added Description column else for other item types it will display as NA. One can customize item type and property as per requirement.

> Description Column does not support Search. This feature will be
> release in upcoming version of this project

#### **Contributing**

1.	Fork it!
2.	Create your feature branch: git checkout -b my-new-feature
3.	Commit your changes: git commit -am 'Add some feature'
4.	Push to the branch: git push origin my-new-feature
5.	Submit a pull request
For more information on contributing to this project, another Plural Labs project, or any Plural Community project, shoot us an email at info@pluraltechnology.com.

#### **Credits**
Display Additional Properties of Work Item in Inbasket Grid application created by Plural Aras Development Team.
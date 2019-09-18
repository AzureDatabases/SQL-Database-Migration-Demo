# SQL Database Migration Demo  

[About this demo](#about-this-demo)

[Part 1: Data Migration Assistance](#part-1-data-migration-assistance)

[Part 2: Azure Migration](#part-2-azure-migration)

[Part 3: SKU Recommendations](#part-3-sku-recommendations)  

[Part 4: SQL Migration Experience](#part-4-sql-migration-experience)  


## About this demo  

In this demo we’ll show you how we’re making it easier for customers to migrate to Azure with three key tools: Azure Migrate, Data Migration Assistant (DMA) and Azure Database Migration Service (DMS).
In this scenario a customer has decided to migrate to over 100 SQL Server 2008 R2 databases to Azure. We start with Data Migration Assistant (DMA) to assess and detect compatibility issues that can impact database functionality in your new version of SQL Server or Azure SQL Database. DMA recommends performance and reliability improvements for your target environment and allows you to move your schema, data, and uncontained objects from your source server to your target server.



## PART 1: Data Migration Assistance  

1. Connect to the virtual machine using the credentials provided in the lab details page.  

<img src="/images/lab-details-page.png">   

2. To open the **SQL Server Management Studio**, click on the SQL Server Management Studio icon on the Taskbar as shown below.     

<img src="/images/sqlmgmtstudio-select.png">   

3. Connect to SQL Instances. In the Connect to Server window from the Server name dropdown select SQLSERVER-01 (default sql instance).    

4. Select **Windows Authentication** in the Authentication dropdown.  

5. Click the **Connect** button to connect to the instance.  

<img src="/images/sqlserver-connect-ssms.png">   

6. In Object Explorer, expand the Database nodes corresponding to the loaded instance.  

<img src="/images/databases-loaded.png">   

7. Go to the Desktop, open **Microsoft Data Migration Assistant**      

<img src="/images/click-dma-icon.png">    

8. In Data Migration Assistant, click on **+** to start a new Migration project.   

9. Enter Project name: **Migration Demo** (User defined field so feel free to use any name you like).    

10. Select **SQL Server** from the **Source server type** drop down (Articulate or talk about the support for AWS RDS for SQL Server workloads)    

11. Select **Azure SQL Database Managed Instance** from the **Target server type** drop down.  

12. Click on **Create**.  

<img src="/images/enter-dma-details-01.png">  

13. Check **Check database compatibility** option.  

14. Check **Check feature parity** option.   

15. Once selected click **Next**. 

<img src="/images/select-report-type.png">  

16. For Server name, type the Source SQL server: **sqlserver-01** (that we connected to in step 4)  
17. In Authentication type, select **Windows Authentication**.
18. In Connection properties: Check: Encrypt Connection Check: Trust server certificate   
19. Click **Connect**.  

<img src="/images/connect-to-server-dma.png">  

20. In **Add sources** pane: Select all the databases by checking on the box corresponding to **sqlserver-01**. For a shorter demo just select the top 5 databases.

21. Click on **Add**.  

<img src="/images/select-all-db-dma.png">  

22. Click **Start Assessment**  

<img src="/images/start-assesment-mi-98db.png">  

23. Select **SQL Server feature parity**  

24. Select/Expand Unsupported feature.  

25. Point to the **Impact and generated recommendations**.  

<img src="/images/sqlserverparity-mi.png">  

26. Switch to the **Compatibility issues**.  

27. Toggle between databases to see Compatibility issues.  

28. Select **Adventure Work Associates** database.  

29. Select/Expand Migration blocker.  

30. Point to the **Impact and generated recommendations**.  

31. Click on **Upload to Azure Migrate** button. The **Upload to Azure Migrate** button will be greyed out in the begining, Once all databases are analyzed, **Upload to Azure Migrate** button becomes functional. This may take 2 to 5 minutes depending on number of databases you've selected.

<img src="/images/compatibilityissues-mi.png">     

32. You will be asked to login to your azure account. Sign in to your Azure Account using the credentials provided in the lab details page:  

<img src="/images/azure-credentials.png">  

33. Select the appropriate **Subscription** and the **Migration Project** and click on **Upload**.    

<img src="/images/upload-azure-migrate-mi.png">  

34. Wait for the upload to finish.  


## PART 2: Azure Migration   

1. Login to Azure https://portal.azure.com/signin with the credentials provided in the lab details page.  

<img src="/images/azure-credentials.png">  

2. On the Azure home page, Click on **Create a resource** search for **Azure Migrate** in the top search box.  

3. Select **Azure Migrate** from the services pane.    

<img src="/images/azure-migrate-azure-portal.png">  

4. Click on **Create**.  

<img src="/images/azure-migrate-click.png">  

5. Click **Assess and migrate databases**  

<img src="/images/asses-migrate-databases.png">    

6. Click on the **change** link to change the Migration project to be loaded.  

<img src="/images/change-migrate-project.png">   

7. Select the appropriate **Subscription** and **Migrate Project** and click on **OK**.  

<img src="/images/migrate-project-settings.png">  

8. The assesment we uploaded in the above steps will be displayed. It might take some time for all the information to be loaded.    

<img src="/images/uploaded-report-migrate.png">   

9. Click on the number next to **Assessed database instances**.  

<img src="/images/asses-number-of-instances.png">   

10. The readiness status and the number of databases will be displayed.  

<img src="/images/readiness-status-instance.png">   

11. The database readiness for different targets will be displayed.  

<img src="/images/database-readiness-targets.png">   

## PART 3: SKU Recommendations  
The SKU Recommendations feature of the DMA allows you to identify both the minimum recommended Azure SQL Database single database or managed instance SKU based on performance counters collected from the computer(s) hosting your databases. This feature provides recommendations related to pricing tier, compute level, and max data size, as well as estimated cost per month. In this case, the PowerShell scripts are pre-executed and the results are stored in the Desktop.  

1.  Navigate to the Desktop and click on the **prices_SQL_DB.html** file.  

<img src="/images/prices_sql_db_click.png">   

2.  In the **Subscription Information** region, enter the following details.  

    *  Subscription Id  
    *  Region  
    *  Resource group  
    *  Server Name  
    *  Server Admin Username  
    *  Server Admin Password  
    
These details will be used to generate the PowerShell script that can be used to provision the databases.    

<img src="/images/subscription-information-sqldb-html.png">  

3.  Adjust the sliders corresponding to **Compute Level** and **Max Data Size** if you wish to make changes to the default configuration. All the changes made by adjusting the sliders will be reflected in the PowerShell script that will be generated and the value corresponding to the **Est.Cost Per Month** will also change accordingly.  

<img src="/images/complevel-datasize-slider.png">  

4.  Check the box corresponding to **I already have a SQL Server License (up to 55% savings)**.  

5.  Click on the **Generate Provisioning Script** button if you wish to generate the powershell script that can be used to provision the databases. **C:\Users\migdemo\Downloads\**    

<img src="/images/generate-provisioning-script-sqldb.png">  

6.  To perform the above steps for SQL Managed Instance, navigate to the Desktop and click on the **prices_SQL_MI.html** file.  

<img src="/images/prices-sqlmi-html-click.png">   


7.  In the **Subscription Information** region, enter the following details.  

    *  Subscription Id  
    *  Resource group   
    *  Region   
    *  Instance Name  
    *  Instance Admin Username  
    *  Instance Admin Password  
    *  Vnet Name  
    *  Subnet Name
    
These details will be used to generate the PowerShell script that can be used to provision the Managed Instance.    

<img src="/images/subscription-information-sqlmi-html.png">    


8.  Adjust the sliders corresponding to **Compute Level** and **Max Data Size** if you wish to make changes to the default configuration. All the changes made by adjusting the sliders will be reflected in the PowerShell script that will be generated and the value corresponding to the **Est.Cost Per Month** will also change accordingly.  

<img src="/images/complevel-datasize-slider-sqlmi.png">  

9.  Check the box corresponding to **I already have a SQL Server License (up to 55% savings)**.  

10.  Click on the **Generate Provisioning Script** button if you wish to generate the powershell script that can be used to provision the databases. The script will be downloaded to **C:\Users\migdemo\Downloads\**.      

<img src="/images/generate-provisioning-script-sqldb.png">  

11. For the purpose of this demo, the scripts for provisioning Azure SQL Databases and Azure SQL Managed Instances are pre-generated and stored in **C:\Users\migdemo\Desktop\Generated Scripts**.

12. Click on **Generated Scripts** folder in the Desktop.  

<img src="/images/generatedscripts-desktop.png">  

13.  The scripts for provisioning the Azure SQL Databases(**sqldbScript.ps1**) and Azure SQL Managed Instance(**sqlmiScript.ps1**) will be present in the folder.  

<img src="/images/generatedscripts-content.png">   

## Part 4: SQL Migration Experience   

1. Login to the Azure Portal with the credentials provided in the Lab details page.  

<img src="/images/azure-credentials.png">   

2. Click on the Resource Group named **SQLMI-Shared-RG**

<img src="/images/click-sqlmishared-rg.png">   

3. Click on the **Azure Database Migration Service** named **SQLMigrationDemo-DMS**.  

<img src="/images/click-dms.png">   

4. The migration Projects available under the **SQLMigrationDemo-DMS** will be displayed as shown below. Click on the Azure Database Migration Project **Migrate-01**.   

<img src="/images/click-mig-project.png">   

5. The **Overview** section of the **Migrate-01** project will contain the following details:  
      *  **Source Server**:  The DNS Name of the Source.  
      *  **Source Version**: The version details of the Source.   
      *  **Target Server**:  The DNS Name of the Target. 
      *  **Target Version**: The version details of the target.  
      
<img src="/images/mig-project-overview.png">   


6. All the ongoing/completed activities will diplayed. To view the details of the migration activity named **Migrate2SQLMI**, click on the activity as shown below.  

<img src="/images/click-mig-activity.png">   

7. All the databses which are being migrated will be displayed as shown below. Click on the database **Adworks40** to view the status.    
<img src="/images/log-shipping-progress.png">   

8.  The migration details of the database will be displayed as below. Under the **Database Status** you can see that the current status is **Log Shipping in progress**. Once the sync is complete, the **Start Cutover** button will be active and the cutover can be performed by clicking the **Start Cutover** button.  

<img src="/images/start-cutover-grey.png">   


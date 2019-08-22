# SQL Database Migration Demo  

[About this demo](#about-this-demo)

[Part 1: Data Migration Assistance](https://github.com/SpektraSystems/Azure-MySQL-DMS-Lab/blob/master/Module%201:%20Azure%20Database%20for%20MySQL.md)

[Part 2: ](https://github.com/SpektraSystems/Azure-MySQL-DMS-Lab/blob/master/Module%202:%20Migrate%20MySQL%20to%20Azure%20Database%20for%20MySQL%20online%20using%20DMS.md)

## About this demo  

The way people consume books has changed, with audiobooks and digital downloads transforming the publishing industry. Nod Publishers wants to migrate their on-premises SQL 2008 R2 workload to the cloud. With this cloud transformation they can upscale user experience with the latest and greatest of cloud technologies. Nod Publishers is a digital platform that offers unlimited audiobooks and digital downloads to avid readers. Powered by Microsoft Azure, the Nod Publisher subscription platform uses advanced analytics to provide subscribers with personalized recommendations based on their interests—and it’s seen 100 percent growth year on year. This demo is based on the real customer scenario.  

### Goal  

The goal of this demo is to introduce SQL Server migration using Data Migration Assistance (DMA). In the second part of the demo we will publish our assessment to the Azure Migration Project. In the third part, we will estimate the Azure workloads cost per the SKU recommendations generated by DMA CLI.

# PART 1: Data Migration Assistance  

1. Connect to the virtual machine using the credentials provided in the lab details page.  

<img src="/images/lab-details-page.png">   

2. Open the **SQL Server Management Studio** as shown below:  

<img src="/images/sqlmgmtstudio-select.png">   

3. Connect to SQL Instances. In the Connect to Server window from the Server name dropdown select SQLSERVER-01 (default sql instance).    

5. Select **Windows Authentication** in the Authentication dropdown.  

6. Click the **Connect** button to connect to the instance.  

<img src="/images/sqlserver-connect-ssms.png">   

7. In Object Explorer, expand the Database nodes in both instances.  
10. Point to the transactional databases (default instance).  







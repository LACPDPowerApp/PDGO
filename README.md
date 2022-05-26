# PDGO PowerApp 

This document will go over how to copy sharepoint tables used in the PDGO power app over to the Public Defender Azure SQL database. You will need Outlook login credentials provided by LAC Public Defender IT Dept. 

## Export PDGO Tables
This link will direct to the sharepoint tables used by Public Defender (tables are also included in this repository): 

https://lacounty.sharepoint.com/teams/ITSupportApps/_layouts/15/viewlsts.aspx?view=14&CT=1637163871183&OR=OWA%2DNT&CID=8b9a2366%2Dabb5%2De930%2D56e7%2D600c9fcd4898

The tables that are used for PDGO are BalanceCollectionDev, HolidaysCollectionDev, HSsubmissionsDev, PDHRLogDev, PDHRRequestsDev, PDPhotosDev, PDStaffListDev, SupervisorUpdateDev. Export these tables into a folder.

## Download VPN Software

https://docs.pulsesecure.net/WebHelp/PCS/9.1R4/AG/Content/ps-pcs-gettingstartedguide/Download_Software.htm

On windows edit the file in this path:
- C:\Windows\System32\drivers\etc\hosts

Add these hosts:
- 10.51.207.5 pddevapps.database.windows.net
- 10.51.207.5 pddevapps.privatelink.database.windows.net

Go to this link to check if you are connected to VPN:
https://era.lacounty.gov/pd/mfa

Once connected to the VPN you will be able to access the Public Defender Azure server with MSSMS

## Download Microsoft SQL Server Management Studio
https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16

### Server Login
- Server: tcp:pddevapps.database.windows.net,1433
- Username: pdappsdevadmin
- pw: October@2021

Once credentials are granted on MS SQL Server Management Studio, you can now transfer the sharepoint tables onto SQL tables. 

Right click on the database on the side bar and in dropdown menu select Import Data

Select the table you want transferred to SQL table

Edit column datatypes

After following the pop up window the selected table should be imported into the Azure server.

## Power Apps Canvas

Go to view on the top bar and select Datasource

Add SQL server as a Datasource

Enter the SQL server Login info above

Select the tables that have been imported

Once the tables are imported multiple code changes are needed in order to make PDGO app work with SQL tables
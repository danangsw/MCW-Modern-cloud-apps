![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")


<div class="MCWHeader1">
Modern cloud apps
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
November 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Modern cloud apps hands-on lab step-by-step](#modern-cloud-apps-hands-on-lab-step-by-step)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Solution architecture](#solution-architecture)
    - [Requirements](#requirements)
    - [Help references](#help-references)
    - [Exercise 1: Proof of concept deployment](#exercise-1-proof-of-concept-deployment)
        - [Task 1: Deploy the e-commerce website, SQL Database, and storage](#task-1-deploy-the-e-commerce-website-sql-database-and-storage)
            - [Subtask 1: Create the Web App and SQL database instance](#subtask-1-create-the-web-app-and-sql-database-instance)
            - [Subtask 2: Provision the storage account](#subtask-2-provision-the-storage-account)
            - [Subtask 3: Update the configuration in the starter project](#subtask-3-update-the-configuration-in-the-starter-project)
            - [Subtask 4: Deploy the e-commerce Web App from Visual Studio](#subtask-4-deploy-the-e-commerce-web-app-from-visual-studio)
        - [Task 2: Setup SQL Database Geo-Replication](#task-2-setup-sql-database-geo-replication)
            - [Subtask 1: Add secondary database](#subtask-1-add-secondary-database)
            - [Subtask 2: Failover secondary SQL database -- OPTIONAL](#subtask-2-failover-secondary-sql-database----optional)
            - [Subtask 3: Test e-commerce Web App after Failover](#subtask-3-test-e-commerce-web-app-after-failover)
            - [Subtask 4: Revert Failover back to Primary database](#subtask-4-revert-failover-back-to-primary-database)
            - [Subtask 5: Test e-commerce Web App after reverting failover](#subtask-5-test-e-commerce-web-app-after-reverting-failover)
        - [Task 3: Deploying the call center admin website](#task-3-deploying-the-call-center-admin-website)
            - [Subtask 1: Provision the call center admin Web App](#subtask-1-provision-the-call-center-admin-web-app)
            - [Subtask 2: Update the configuration in the starter project](#subtask-2-update-the-configuration-in-the-starter-project)
            - [Subtask 3: Deploy the call center admin Web App from Visual Studio](#subtask-3-deploy-the-call-center-admin-web-app-from-visual-studio)
        - [Task 4: Deploying the payment gateway](#task-4-deploying-the-payment-gateway)
            - [Subtask 1: Provision the payment gateway API app](#subtask-1-provision-the-payment-gateway-api-app)
            - [Subtask 2: Deploy the Contoso.Apps.PaymentGateway project in Visual Studio](#subtask-2-deploy-the-contosoappspaymentgateway-project-in-visual-studio)
        - [Task 5: Deploying the offers Web API](#task-5-deploying-the-offers-web-api)
            - [Subtask 1: Provision the Offers Web API app](#subtask-1-provision-the-offers-web-api-app)
            - [Subtask 2: Configure cross-origin resource sharing (CORS)](#subtask-2-configure-cross-origin-resource-sharing-cors)
            - [Subtask 3: Update the configuration in the starter project](#subtask-3-update-the-configuration-in-the-starter-project-1)
            - [Subtask 4: Deploy the Contoso.Apps.SportsLeague.Offers project in Visual Studio](#subtask-4-deploy-the-contosoappssportsleagueoffers-project-in-visual-studio)
        - [Task 6: Update and deploy the e-commerce website](#task-6-update-and-deploy-the-e-commerce-website)
            - [Subtask 1: Update the Application Settings for the Web App that hosts the Contoso.Apps.SportsLeague.Web project](#subtask-1-update-the-application-settings-for-the-web-app-that-hosts-the-contosoappssportsleagueweb-project)
            - [Subtask 2: Validate App Settings are correct](#subtask-2-validate-app-settings-are-correct)
    - [Exercise 2: Enabling Telemetry with Application Insights](#exercise-2-enabling-telemetry-with-application-insights)
        - [Task 1: Configure the application for telemetry](#task-1-configure-the-application-for-telemetry)
            - [Subtask 1: Add Application Insights Telemetry to the e-commerce website project](#subtask-1-add-application-insights-telemetry-to-the-e-commerce-website-project)
            - [Subtask 2: Enable client side telemetry](#subtask-2-enable-client-side-telemetry)
            - [Subtask 3: Deploy the e-commerce Web App from Visual Studio](#subtask-3-deploy-the-e-commerce-web-app-from-visual-studio)
        - [Task 2: Creating the web performance test and load test](#task-2-creating-the-web-performance-test-and-load-test)
            - [Subtask 1: Create the load test](#subtask-1-create-the-load-test)
            - [Subtask 2: View the Application Insights logs](#subtask-2-view-the-application-insights-logs)
    - [Exercise 3: Automating backend processes with Azure Functions and Logic Apps](#exercise-3-automating-backend-processes-with-azure-functions-and-logic-apps)
        - [Task 1: Create an Azure Function to Generate PDF Receipts](#task-1-create-an-azure-function-to-generate-pdf-receipts)
        - [Task 2: Create an Azure Logic App to Process Orders](#task-2-create-an-azure-logic-app-to-process-orders)
    - [After the hands-on lab](#after-the-hands-on-lab)
        - [Task 1: Delete resources](#task-1-delete-resources)

<!-- /TOC -->

# Modern cloud apps hands-on lab step-by-step 

## Abstract and learning objectives 

In this hands-on lab, you will be challenged to implement an end-to-end scenario using a supplied sample that is based on Azure App Services, Microsoft Azure Functions, Azure SQL Database, Azure Logic Apps, and related services. The scenario will include implementing compute, storage, workflows, and monitoring, using various components of Microsoft Azure. 

Please note that as opposed to the whiteboard design session, the lab is not focused on maintaining PCI compliance and using more advanced security features such as App Service Environment, Network Security Groups, and Application Gateway. The hands-on lab can be implemented on your own, but it is highly recommended to pair up with other members working on the lab to model a real-world experience and to allow each member to share their expertise for the overall solution.

By the end of this hands-on lab, you will have learned how to use several key services within Azure to improve overall functionality of the original solution, and to increase the security and scalability of the new and improved design.

## Overview

The Cloud Workshop: Modern Cloud Apps lab is a hands-on exercise that will challenge you to implement an end-to-end scenario using a supplied sample that is based on Microsoft Azure App Services and related services. The scenario will include implementing compute, storage, security, and scale using various components of Microsoft Azure. The lab can be implemented on your own, but it is highly recommended to pair up with additional team members to more closely model a real-world experience, and to allow members to share their expertise for the overall solution.

## Solution architecture

![A diagram that depicts the various Azure PaaS services for the solution. Azure AD Org is used for authentication to the call center app. Azure AD B2C for authentication is used for authentication to the client app. SQL Database for the backend customer data. Azure App Services for the web and API apps. Order processing includes using Functions, Logic Apps, Queues and Storage. Azure App Insights is used for telemetry capture.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image2.png "Solution Architecture Diagram")

## Requirements

1.  Microsoft Azure subscription
2.  Local machine or a virtual machine configured Visual Studio 2017 Community Edition
    
## Help references

|    |            |
|----------|:-------------|
| **Description** | **Links** |
| SQL firewall | <https://azure.microsoft.com/en-us/documentation/articles/sql-database-configure-firewall-settings/> |
| Deploying a Web App | <https://azure.microsoft.com/en-us/documentation/articles/web-sites-deploy/> |
| Deploying an API app | <https://azure.microsoft.com/en-us/documentation/articles/app-service-dotnet-deploy-api-app/> |
| Accessing an API app from a JavaScript client | <https://azure.microsoft.com/en-us/documentation/articles/app-service-api-javascript-client/> |
| SQL Database Geo-Replication overview | <https://azure.microsoft.com/en-us/documentation/articles/sql-database-geo-replication-overview/> |
| What is Azure AD? | <https://azure.microsoft.com/en-us/documentation/articles/active-directory-whatis/> |
| Azure Web Apps authentication | <http://azure.microsoft.com/blog/2014/11/13/azure-websites-authentication-authorization/> |
| View your access and usage reports | <https://msdn.microsoft.com/en-us/library/azure/dn283934.aspx> |
| Custom branding an Azure AD Tenant | <https://msdn.microsoft.com/en-us/library/azure/Dn532270.aspx> |
| Service Principal Authentication | <https://docs.microsoft.com/en-us/azure/app-service-api/app-service-api-dotnet-service-principal-auth> |
| Consumer Site B2C | <https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-devquickstarts-web-dotnet> |
| Getting Started with Active Directory B2C | <https://azure.microsoft.com/en-us/trial/get-started-active-directory-b2c/> |
| How to Delete an Azure Active Directory | <https://blog.nicholasrogoff.com/2017/01/20/how-to-delete-an-azure-active-directory-add-tenant/> |
| Run performance tests on your app | <http://blogs.msdn.com/b/visualstudioalm/archive/2015/09/15/announcing-public-preview-for-performance-load-testing-of-azure-webapp.aspx> |
| Application Insights Custom Events | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-api-custom-events-metrics/> |
| Enabling Application Insights | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-start-monitoring-app-health-usage/> |
| Detect failures | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-asp-net-exceptions/> |
| Monitor performance problems | <https://azure.microsoft.com/en-us/documentation/articles/app-insights-web-monitor-performance/> |
| Creating a Logic App | <https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-create-a-logic-app/> |
| Logic app connectors | <https://azure.microsoft.com/en-us/documentation/articles/app-service-logic-connectors-list/> |
| Logic Apps Docs | <https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-what-are-logic-apps> |
| Azure Functions -- create first function | <https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-azure-function> |
| Azure Functions docs | <https://docs.microsoft.com/en-us/azure/logic-apps/logic-apps-azure-functions> |

## Exercise 1: Proof of concept deployment

Duration: 60 minutes

Contoso has asked you to create a proof of concept deployment in Microsoft Azure by deploying the web, database, and API applications for the solution as well as validating that the core functionality of the solution works. Ensure all resources use the same resource group previously created for the App Service Environment.

### Task 1: Deploy the e-commerce website, SQL Database, and storage

In this exercise, you will provision a website via the Azure **Web App + SQL** template using the Microsoft Azure Portal. You will then edit the necessary configuration files in the starter project and deploy the e-commerce website.

#### Subtask 1: Create the Web App and SQL database instance

1.  Navigate to the Azure Management portal, [http://portal.azure.com](http://portal.azure.com/), using a new tab or instance and login with your lab-provided Azure credentials.

2.  In the navigation menu to the left, select **+Create a resource** and in the Marketplace search text box, enter **Web App + SQL** and select the appropriate auto-suggestion.

    ![In the Azure Portal on the left, "+Create a resource", search box text and auto-suggestion are surrounded by red boxes.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image11.png "Azure Portal")

3.  In the new product blade, select **Create**.

    ![The Web App + SQL blade](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image13.png "Web App + SQL blade")


4.  On the Web App blade, specify the following configuration:

    -  A unique and valid name (until the green check mark appears). We've used ContosoAp2010. Make note of your selection.

    -  Select **contososports** resource group.

    -  **ContosoSportsPlan** as a new App Service Plan. Make sure it's in the same location as the **contososports** resource group you created earlier. Use the default **Standard S1** pricing tier. 

5. Select **SQL Database *Configure required settings***, and then **+ Create a new database**.

    ![The tile for the Create a new database option is displayed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image16.png " Create a new database")

6. On the **SQL Database** blade, specify **ContosSportsDB** as the database name and then select **Target** **Server *Configure required settings***.

    ![Screenshot of the Target Server Configure required settings option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image18.png "Target Server Configure required settings option")

7. On the **New server** blade, specify the following configuration:

    -  Server name: **A unique value (ensure the green checkmark appears)**

    -  Server admin login: **demouser**

    -  Password and Confirm Password: **Password.1!!**

    -  Ensure the **Location** is the same region as the Web app.

    ![Fields in the New server blade are circled and set to the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image19.png "New server blade")

8. Once the values are accepted in the **New server** blade, click **Select**.

    ![Screenshot of the Select button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image20.png "Select button")

9. On the **SQL Database** blade, click **Select**.

    ![Screenshot of the Select button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image20.png "Select button")

10. After the values are accepted on the **Web App + SQL** creation blade, check select **Create**.

    ![Screenshot of the Create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image21.png "Create button")

    > **Note**: This may take a couple minutes to provision the Web App and SQL Database resources.

11. After the Web App and SQL Database are provisioned, click **SQL databases** in the left-hand navigation menu followed by the name of the SQL Database you just created and select it.

    ![In the Azure Portal, on the left side, "SQL Databases" is surrounded by a red box. In the right pane, "ContosoSportsDB" is surrounded by a red box](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image22.png "Azure Portal")

12. On the **SQL Database** blade, click the **Show database connection strings** link.

    ![On the SQL Database blade, in the left pane, Overview is selected. In the right pane, under Essentials, the Connection strings (Show database connection strings) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image23.png "SQL Database blade")

13. On the **Database connection strings** blade, select and copy the **ADO.NET** connection string. Then, save it in **Notepad** for use later, being sure to replace the placeholders with your username and password with **demouser** and **Password.1!!**, respectively.

    ![In the Database connection strings blade, the ADO.NET connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image24.png "Database connection strings blade")

14. On the **Overview** screen of the **SQL Server** blade, click **Set server firewall**.

    ![In the SQL Server Blade, Overview section, the Set server firewall tile is in a red box.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image25.png "SQL Server Blade, Essentials section")

15. On the **Firewall Settings** blade, specify a new rule named **ALL**, with START IP **0.0.0.0**, and END IP **255.255.255.255**.

    ![Screenshot of the Rule name, Start IP. and End IP fields on the Firewall Settings blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "Firewall Settings blade")

    > **Note**: This is only done to make the lab easier to do. In production, you do **NOT** want to open up your SQL Database to all IP Addresses this way. Instead, you will want to specify just the IP Addresses you wish to allow through the Firewall.

16. Click **Save**.

    ![Screenshot of the Firewall settings Save button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image28.png "Firewall settings Save button")

17. On the **Success!** dialog box, click **OK**.

    ![Screenshot of the Success dialog box, which says that the server firewall rules have been successfully updated.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image29.png "Success dialog box")

18. Close all configuration blades.

#### Subtask 2: Provision the storage account

1.  Using a new tab or instance of your browser, navigate to the Azure Management portal <http://portal.azure.com>.

2.  From the navigation menu to the left, click **+Create a resource**, **Storage Accounts** and then click **+Add** at the top of the new blade.

    ![In the Azure Portal, in the navigation menu on the left, Storage Account is surrounded by a red box. To the right, the "+Add" tile is likewise surrounded](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image30.png "Azure Portal - Storage Accounts")

3.  On the **Create storage account** blade, specify the following configuration options:

    -  Name: Unique value for the storage account (ensure the green check mark appears).

    -  Specify the existing resource group **contososports**.

    -  Specify the same **Location** as the Contoso Sports resource group.

    -  Accept the defaults for all other settings.

    ![The fields in the Create Storage Account blade are set to the previously defined settings. In addition, the Name field set to contososports2101, Deployment model is Resource Manager, Account kind is General purpose, and Performance is standard.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image31.png "Create Storage Account blade")

4.  Click **Review + create**.

    ![Screenshot of the Review + create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image32.png "Create button")

5.  Click **Create** after Validation passed.

    ![Screenshot of the Create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image32a.png "Create button")

6.  Once the storage account has completed provisioning, open the storage account by clicking **Storage accounts** in the navigation menu to the left and clicking on the storage account name.

    ![The Storage Account menu link in the Azure Portal.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image33.png "Azure Portal, More services")

7.  On the **Storage account** blade, scroll down, and, under the **SETTINGS** menu area, select the **Access keys** option.

    ![In the Storage account blade, under Settings, Access keys is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image35.png "Storage account blade")

8.  On the **Access keys** blade, click the copy button by the **Connection String** field in the **key1** section. Paste the value into **Notepad** for later usage. 

    ![In the Access keys blade default keys section, the copy button for the key1 connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image36.png "Access keys blade, default keys section")

#### Subtask 3: Update the configuration in the starter project

1.  In the Azure Portal, click on **Resource Groups**. Then, click on the **contososports** resource group.

    ![In the Azure Portal left menu, Resource groups selected. In the Resource groups blade, under Name, contososports is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image37.png "Azure Portal")

2.  Click on the **Web App** (App Service type) created previously.

3.  On the **App Service** blade, scroll down in the left pane, and, under the **SETTINGS** menu, click on **Application settings**.

    ![In the App Service blade, under Settings, Application settings is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image38.png "App Service blade")

4.  Scroll down, and locate the **Application settings** section.

    ![The App settings section from the App Service blade displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image39.png "App Service blade")

5.  Add a new **Application setting** with the following values:

    -  Key: **AzureQueueConnectionString**

    -  Value: **Enter the Connection String for the Azure Account just created** from your Notepad file

    ![In the App settings section for the App Service blade, the new entry for AzureQueueConnectionString is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image40.png "App settings section")

6.  Locate **Connection Strings** below **Application Settings** in your Notepad file.

    ![The Connection Strings section for the App Service blade displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image41.png "Connection Strings section")

7.  Add a new **Connection String** with the following values:

    -  Name: **ContosoSportsLeague**

    -  Value: **Enter the Connection String for the SQL Database just created**

    -  Type: **SQLAzure**

    >**Important**: Ensure you replace the string placeholder values **{your\_username}** **{your\_password\_here}** with the username and password you setup during previously. 
    
    ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder value")

8.  Click **Save**.

    ![On the App Service blade, the Save button selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image44.png "App Service blade")

#### Subtask 4: Deploy the e-commerce Web App from Visual Studio

1.  Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** of Visual Studio.

    ![In Solution Explorer, under Solution \'Contoso.Apps.SportsLeague\' (7 projects), Web is expanded, and under Web, Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image45.png "Solution Explorer")

2.  Right-click the **Contoso.Apps.SportsLeague.Web** project, and click **Publish**.

    ![In Solution Explorer, Contoso.Apps.SportsLeague.Web is selected, and from its right-click menu, Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image46.png "Solution Explorer")

3.  Choose **Azure App Service** as the publish target, and choose **Select Existing** and then **Publish** at the bottom of the wizard.

![On the Publish tab, the Microsoft Azure App Service tile is selected, as is the radio button for Select Existing.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image47.png "Publish tab")

4.  If prompted, log on with your credentials, and ensure the subscription you published earlier are selected.

    ![Screenshot of the Microsoft account subscriptions tile.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image48.png "Microsoft account tile")

5.  Select the **Contoso Sports Web App** (with the name you created previously).

    ![Under Subscriptions, under contososports, contososportsweb0 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image49.png "Subscriptions")

6.  Click **OK**, and click **Publish** to publish the Web application.

7.  In the Visual Studio **Output** view, you will see a status that indicates the Web App was published successfully. 

    ![Screenshot of the Visual Studio Output view, with the Publish Succeeded message circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image50.png "Visual Studio Output view")

8.  A new browser should automatically open the new web applications. Validate the website by clicking the **Store** link on the menu. As long as products return, the connection to the database is successful.

    ![Screenshot of the Store link.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image51.png "Store link")

    >**Troubleshooting**: If the web site fails to show products, go back and double check all of your connection string entries and passwords.

### Task 2: Setup SQL Database Geo-Replication

In this exercise, the attendee will provision a secondary SQL Database and configure Geo-Replication using the Microsoft Azure Portal.

#### Subtask 1: Add secondary database

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2.  Click **SQL databases** in the navigation menu to the left, and click the name of the SQL Database you created previously.

    ![Screenshot of SQL Databases menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL Databases")

3.  Under the **SETTINGS** menu area, click on **Geo-Replication**.

    ![In the Settings section, Geo-Replication is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image53.png "Settings section")

4.  Select the Azure Region to place the Secondary within.

    ![The Geo-Replication blade has a map of the world with locations marked on it. Under the map, Primary is set to West US, which on the map has a blue checkmark.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image54.png "Geo-Replication blade")

    The Secondary Azure Region should be the Region Pair for the region the SQL Database is hosted in. Consult https://docs.microsoft.com/en-us/azure/best-practices-availability-paired-regions to see which region pair the location you are using for this lab is in.

5.  On the **Create secondary** blade, select **Secondary Type** as **Readable**.

6.  Select **Target server** ***Configure required settings***.
    
    ![the Target server Configure required settings option is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image55.png "Target server option")

7.  On the **New server** blade, specify the following configuration:

    -  Server name: **A unique value (ensure the green checkmark appears)**

    -  Server admin login: **demouser**

    -  Password and Confirm Password: **Password.1!!**

    ![The fields in the New Server blade display with the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image56.png "New Server blade")

8.  Once the values are accepted in the **New server** blade, click **Select**.

    ![Screenshot of the Select button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image20.png "Select button")

9.  On the **Create secondary** blade, click **OK**.

    ![Screenshot of the OK button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image57.png "OK button")

10. After the Geo-Replication has finished provisioning, click **SQL Databases** in the navigation menu to the left.

    ![The SQL databases option in the Azure Portal navigation menu](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL Databases")

11. Click the name of the Secondary SQL Database you just created.

    ![In the list of Databases, the ContosoSportsDB secondary replication role is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image58.png "Database list")

12. On the **SQL Database** blade, click the **Show database connection strings** link.

    ![On the SQL database blade, in the Essentials blade, the Connection strings (show database connection strings) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image59.png "SQL database blade")

13. On the **Database connection strings** blade, select and copy the **ADO.NET** connection string, and save it in Notepad for use later.

    ![On the Database connection strings blade, ADO.NET tab, the connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image60.png "Database connection strings blade")

14. On the SQL database blade in the Essentials section, click the SQL Database Server name link.

    ![On the SQL database blade in the Essentials section, the Server name (contososqlserver2.database.windows.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image61.png "SQL database blade, Essentials section")

15. On the **SQL Server** blade, click **Set Server Firewall** at the top.

    ![On the SQL Server blade, at the top, the Set Server Firewall tile is boxed in red.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image62.png "SQL Server blade, Essentials section")

16. On the **Firewall Settings** blade, specify a new rule named **ALL**, with START IP **0.0.0.0**, and END IP **255.255.255.255**.

    ![On the Firewall Settings blade, in the New rule section, a new rule has been created with the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image27.png "New rule section ")

17. Click **Save**.

    ![On the Firewall Settings blade, the Save button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image63.png "Save button")

18. On the **Success!** Dialog box, click **OK**.

    ![The Success dialog box message explains that the server firewall rules were successfully updated.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image29.png "Success dialog box")

19. Close all configuration blades.

#### Subtask 2: Failover secondary SQL database -- OPTIONAL

Since the Replication and Failover process can take anywhere from 10 to 30 minutes to complete, you have the choice to skip Subtask 2 through 5, and skip directly to Task 3. However, if you have the time, it is recommended that you complete these steps.

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2.  In the navigation menu to the left, click **SQL databases**, and click the name of the *primary* SQL Database you created previously.

    ![Screenshot of SQL Databases tile](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "Azure Portal")

3.  On the **Settings** blade, click **Geo-Replication**.

    ![On the Settings blade, under Settings, Geo-Replication is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image64.png "Settings section")

4.  On the **Geo-Replication** blade, select the *secondary* database.

    ![The Geo-Replication blade has a map of the world with locations marked on it. Under the map, Primary is set to West US, which on the map has a blue checkmark. Under Secondaries, East US is circled, and on the map displays with a green checkmark. A line connects the West Coast (blue) and East Coast (green) checkmarks.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image65.png "Geo-Replication blade")

5.  Click the **Forced Failover** button.

    ![the Forced Failover button is circled on the Secondary database blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image66.png "Secondary database blade")

6.  On the **Forced Failover** prompt, click **Yes**.

    ![On the East US Secondary database blade, in response to the questing asking if you are sure you want to proceed, the Yes button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image67.png "Failover prompt")

The failover may take a few minutes to complete. You can continue with the next Subtask modifying the Web App to point to the Secondary SQL Database while the Failover is pending.

#### Subtask 3: Test e-commerce Web App after Failover

1.  Once completed, in the Azure Portal, click on **SQL databases**, and select the NEW **ContosoSportsDB** secondary.

    ![On the SQL databases blade, under Name, the ContosoSportsDB Secondary replication role is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image68.png "SQL databases blade")

2.  Next, click on **Show database connection strings**, and copy it off thereby replacing the user and password.

    ![On the SQL database blade, on the left Overview is selected. On the right, under Essentials, the Connection strings (Show database connection strings) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image69.png "SQL database blade")

3.  From the Azure portal, click on **Resource Groups**, and select **contososports**.

    ![In the Azure Portal, on the left, Resource groups is circled. On the right, under Name, contososports is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image37.png "Azure Portal")

4.  Click on the **Web App** created earlier.

5.  On the **App Service** blade, scroll down in the left pane, and click on **Application settings**.

    ![On the App Service blade, under Settings, Application settings is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image38.png "App Service blade")

6.  Scroll down, and locate the **Connection strings** section.

7.  Update the **ContosoSportsLeague** Connection String to the value of the **original Secondary Azure SQL Database**.

    ![On the App Service blade, in the Connection strings section, the ContosoSportsLeague connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image70.png "App Service blade")

    >**Note**: Ensure you replace the string placeholder values **{your\_username}** and **{your\_password\_here}** with the username and password you respectively setup during creation (demouser & Password.1!!).

    ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder values")

8.  Click **Save**.

    ![On the App Service blade, the Save button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image44.png "App Service blade Save button")

9.  On the **App Service** blade, click on **Overview**.

    ![Screenshot of Overview menu option](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image71.png "App Service blade")

10. On the **Overview** pane, click on the **URL** for the Web App to open it in a new browser tab.

    ![On the App Service blade, in the Essentials section, the URL (http;//contososportsweb4azurewebsites.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image72.png "App Service blade Essentials section")

11. After the e-commerce Web App loads in Internet Explorer, click on **STORE** in the top navigation bar of the website.

    ![On the Contoso sports league website navigation bar, the Store button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image73.png "Contoso sports league website navigation bar")

12. Verify the product list from the database displays.

    ![Screenshot of the Contoso store webpage. Under Team Apparel, a Contoso hat, tank top, and hoodie display.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image74.png "Contoso store webpage")

#### Subtask 4: Revert Failover back to Primary database

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2.  In the new **SQL databases**, and click the name of the SQL Database you created previously.

    ![Screenshot of SQL Databases menu option.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image52.png "SQL Databases")

3.  On the **Settings** blade, click **Geo-Replication**.

    ![In the Settings section, Geo-Replication is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image64.png "Settings section")

4.  On the **Geo-Replication** blade, select the Secondary database.

    ![The Geo-Replication blade has a map of the world with locations marked on it. Under the map, Primary is set to East US, which on the map has a blue checkmark. Under Secondaries, West US is circled, and on the map displays with a green checkmark. A line connects the East US (blue) and West US (green) checkmarks.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image75.png "Geo-Replication blade")

5.  Click the **Forced Failover** button.

    ![The Forced Failover button in the Secondary Database blade is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image76.png "Secondary Database blade")

6.  On the **Forced Failover** prompt, click **Yes**.

    ![On the West US Secondary database blade, in response to the questing asking if you are sure you want to proceed, the Yes button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image77.png "Failover prompt")

The failover may take a few minutes to complete. You can continue with the next Subtask modifying the Web App to point back to the Primary SQL Database while the Failover is pending.

#### Subtask 5: Test e-commerce Web App after reverting failover

1.  In the Azure Portal, click on **Resource Groups** **\>** **contososports** resource group.

    ![In the left menu of the Azure Portal, Resource groups is selected. On the right, under Resource groups, contososports is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image37.png "Azure Portal")

2.  Click on the **Web App** created in a previous step.

3.  On the **App Service** blade, scroll down in the left pane, and click on **Application settings**.

    ![In the App Service blade Settings section, Application settings is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image38.png "App Service blade")

4.  Scroll down, and locate the **Connection strings** section.

5.  Update the **ContosoSportsLeague** Connection String back to the value of the Connection String for the **original Primary SQL Database**.

    ![In the App Service blade Connection strings section, the ContosoSportsLeague connection string is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image70.png "App Service blade")

    > **Note**: Ensure you replace the string placeholder values **{your\_username}** **{your\_password\_here}** with the username and password you respectively setup during creation (demouser & Password.1!!).

    ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder value")

6.  Click **Save**.

    ![The Save button is circled on the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image44.png "App Service blade")

7.  On the **App Service** blade, click on **Overview**.

    ![Overview is selected on the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image71.png "App Service blade")

8.  On the **Overview** pane, click on the **URL** for the Web App to open it in a new browser tab.

    ![In the App Service blade Essentials section, the URL (http:/contososportsweb4.azurewebsites.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image72.png "App Service blade, Essentials section")

9.  After the e-commerce Web App loads in Internet Explorer, click on **STORE** in the top navigation bar of the website.

    ![On the Contoso sports league website navigation bar, the Store button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image73.png "Contoso sports league website navigation bar")

10. Verify the product list from the database displays.

    ![Screenshot of the Contoso store webpage. Under Team Apparel, a Contoso hat, tank top, and hoodie display.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image74.png "Contoso store webpage")

### Task 3: Deploying the Call Center admin website

In this exercise, you will provision a website via the Azure Web App template using the Microsoft Azure Portal. You will then edit the necessary configuration files in the Starter Project and deploy the call center admin website.

#### Subtask 1: Provision the call center admin Web App 

1.  Using a new tab or instance of your browser, navigate to the Azure Management portal <http://portal.azure.com>.

2.  Select **+Create a new resource** **\>** **Web** **\>** **Web App**.

   ![In the left menu of the Azure Portal, the New button is selected. In middle section, under Marketplace, Web + mobile is selected. In the right, Web + mobile section, under Featured apps, Web App is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image78.png "Azure Portal")

3.  Specify a **unique URL** for the Web App, and ensure the **same App Service Plan** and **resource group** you have used throughout the lab are selected.

    ![On the Web App blade, the App name field is set to contososportsadmin2101.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image79.png "Web App blade")

4.  Click on **App Service plan/Location**, and select the **ContosoSportsPlan** used by the front-end Web app.

5.  After the values are accepted, click **Create**.

    ![Screenshot of the Create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image32.png "Create button")

#### Subtask 2: Update the configuration in the starter project

1.  Navigate to the **App Service** blade for the Call Center Admin App just provisioned.

    ![The App Service blade displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image80.png "App Service blade")

2.  On the **App Service** blade, click on **Application settings** in the left pane.

    ![In the Settings section of the App Service blade, Application settings is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image81.png "Settings section")

3.  Scroll down, and locate the **Connection strings** section.

4.  Add a new **Connection string** with the following values:

    -  Name: **ContosoSportsLeague**

    -  Value: **Enter the Connection String for the last SQL Database that was created**.

    -  Type: **SQL Database**

    ![The Connection Strings fields display the previously defined values.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image83.png "Connection Strings fields")

    >**Note**: Ensure you replace the string placeholder values **{your\_username}** **{your\_password\_here}** with the username and password you respectively setup during creation (demouser & Password.1!!).

    ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder values")

5.  Click **Save**.

    ![the Save button is circled on the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image44.png "App Service blade")

#### Subtask 3: Deploy the call center admin Web App from Visual Studio

1.  Navigate to the **Contoso.Apps.SportsLeague.Admin** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

    ![In Solution Explorer, under Solution Contoso.Apps.SportsLeague, The Web folder is expanded, and Contoso.Apps.SportsLeague.Admin is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image85.png "Solution Explorer")

2.  Right-click the **Contoso.Apps.SportsLeague.Admin** project, and click **Publish**.

    ![In Solution Explorer, the right-click menu for Contoso.Apps.SportsLeague.Admin displays, and Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image86.png "Right-Click menu")

3.  Choose **Microsoft Azure App Service** as the publish target, and choose **Select Existing**.

    ![On the Publish tab, Microsoft Azure App Service is selected. Below that, the radio button is selected for Select Existing.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image87.png "Publish tab")

4.  Select the **Web App** for the Call Center Admin App.

    ![In the App Service section, in the tree view at the bottom, the contososports folder is expanded, and contososportsadmin4 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image88.png "App Service section")

5.  Click **OK**, and click **Publish** to deploy the site.

6.  The website should load / display the following:

    ![The Contoso website displays the Contoso Sports League Admin webpage, which says that orders that display below are sorted by date, and you can click on an order to see its details. However, at this time, there is no data available under Completed Orders.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image89.png "Contoso website")

### Task 4: Deploying the payment gateway

In this exercise, the attendee will provision an Azure API app template using the Microsoft Azure Portal. The attendee will then deploy the payment gateway API to the API app.

#### Subtask 1: Provision the payment gateway API app

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2.  Click **+Create a resource**, type **API App** into the marketplace search box, and press **Enter**.

    ![In the Azure Portal left menu, New is selected. In the New blade, the search field is set to API App.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image90.png "Azure Portal")

3.  On the new **API App** blade, specify a unique name for the App Name, and ensure the previously used Resource Group and App Service Plan are selected.

    ![On the API App blade, the App name field is set to PaymentsAPIO, and is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image93.png "API App blade")

4.  After the values are accepted, click **Create**.

    ![Screenshot of the Create button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image32.png "Create button")

#### Subtask 2: Deploy the Contoso.Apps.PaymentGateway project in Visual Studio

1.  Navigate to the **Contoso.Apps.PaymentGateway** project located in the **APIs** folder using the **Solution Explorer** in Visual Studio.

    ![In Solution Explorer, under Solution Contoso.Apps.SportsLeague, the API folder is expanded, and Contoso.Apps.PaymentGateway is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image95.png "Solution Explorer")

2.  Right-click the **Contoso.Apps.PaymentGateway** project, and click **Publish**.

    ![In Solution Explorer, Contoso.Apps.PaymentGateway is selected, and in its right-click menu, Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image96.png "Solution Explorer")

3.  On the **Publish Web** dialog box, click **Microsoft Azure App Service**, and choose **Select Existing** and then **Publish**.

    ![In the Publish web dialog box, Microsoft Azure App Service is selected, as is the radio button for Select Existing.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image97.png "Publish web dialog box")

4.  Select the Payment Gateway API app created earlier, click **OK** **\>** **Publish**.

    ![In the App Service section, the contososports folder is expanded, and PaymentsAPIO is selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image98.png "App Service section")

5.  In the Visual Studio **Output** view, you will see a status indicating the Web App was published successfully.

    ![The Visual Studio output shows that the web app was published successfully. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image99.png "Visual Studio output")

6. Copy and paste the **URL** of the deployed **API App** for later use.

### Task 5: Deploying the Offers Web API

In this exercise, the attendee will provision an Azure API app template using the Microsoft Azure Portal. The attendee will then deploy the Offers Web API.

#### Subtask 1: Provision the Offers Web API app

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal (<http://portal.azure.com>).

2.  In the navigation menu to the left, click **+Create a resource** -\> **Web** -\> **API App**.

    ![In the Azure Portal left menu, New is selected. On the right, under New, API App is typed in the Search box.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image90.png "Azure Portal")

3.  On the new **API App** blade, specify a unique name for the **API App**, and ensure the previously used Resource Group and App Service Plan are selected.

    ![In the API App blade, OffersAPI4 is typed in the App name field.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image100.png "API App blade")

4.  After the values are accepted, click **Create**.

5.  When the Web App template has completed provisioning, open the new API App by, in the navigation menu to the left,
click **App Services** and then clicking the Offer API app you just created.

   ![In the Azure Portal, on the left More services is selected, and on the right under Web + Mobile, App Services displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image101.png "Azure Portal, More Services")

#### Subtask 2: Configure Cross-Origin Resource Sharing (CORS)

1.  On the **App Service** blade for the Offers API, under the **API** menu section, click **CORS**.

    ![In the App Service blade, under API, CORS is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image102.png "App Service blade")

2.  In the **ALLOWED ORIGINS** text box, specify "*" to allow all origins, and click **Save**.

    >**Note**: You should not normally do this in a production environment.

#### Subtask 3: Update the configuration in the starter project

1.  On the **App Service** blade for the Offers API, click on **Application settings**.

    ![In the App Service blade, under Settings, Application settings is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image103.png "App Service blade")

2.  In the **Connection Strings** section, add a new **Connection string** with the following values:

    -  Name: **ContosoSportsLeague**

    -  Value: **Enter the Connection String for the SQL Database that was created**.

    -  Type: **SQL Database**

        ![The Connection strings section now has a new string with the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image105.png "Connection strings section")

        >**Note**: Ensure you replace the string placeholder values **{your\_username}** **{your\_password\_here}** with the username and password you respectively setup during creation (demouser & Password.1!!).
    
        ![The password string placeholder value displays: Password={your\_password\_here};](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image43.png "String placeholder value")

3.  Click **Save**.

    ![The Save button is selected in the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image106.png "Save button")

#### Subtask 4: Deploy the Contoso.Apps.SportsLeague.Offers project in Visual Studio

1.  Navigate to the **Contoso.Apps.SportsLeague.Offers** project located in the **APIs** folder using the **Solution Explorer** in Visual Studio.

    ![In Solution Explorer, under Solution Contoso.Apps.SportsLeague, the API folder is expanded, and Contoso.Apps.SportsLeague.Offer is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image107.png "Solution Explorer")

2.  Right-click the **Contoso.Apps.SportsLeague.Offers** project, and select **Publish**.

    ![In Solution Explorer, from the Contoso.Apps.SportsLeague.Admin right-click menu, Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image108.png "Solution Explorer")

3.  On the **Publish Web** dialog box, click **Microsoft Azure App Service**, and choose **Select Existing**.

    ![On the Publish tab, the Microsoft Azure App Service tile is selected, and under it, the radio button for Select Existing is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image109.png "Publish tab")

4.  Select the Offers API app created earlier, and click **OK** **\>** **Publish**.

    ![In the App Service section, the contososports folder is expanded, and OffersAPI4 is selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image110.png "App Service section")

5.  In the Visual Studio **Output** view, you will see a status the API app was published successfully.

6.  Record the value of the deployed API app URL for later use.

### Task 6: Update and deploy the e-commerce website

#### Subtask 1: Update the Application Settings for the Web App that hosts the Contoso.Apps.SportsLeague.Web project

1.  Using a new tab or instance of your browser, navigate to the Azure Management Portal <http://portal.azure.com>.

2.  Click on **Resource groups** **\>** **contososports** resource group.

    ![In the Azure Portal left menu, Resource groups is selected. On the right, under Resource groups, under Name, contososports is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image112.png "Azure Portal")

3.  Click on the **App Service Web App** for the front-end web application.

    ![In the Resource Group blade on the right, under Name, contososportsweb2101 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image113.png "Resource Group blade")

4.  On the **App Service** blade, scroll down, and click on **Application settings** in the left pane.

    ![In the App Service blade, under settings, Application settings is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image103.png "App Service blade")

5.  Scroll down, and locate the **Applications settings** section.

    ![The App settings section of the App Service blade displays with AzureQueueConnectionString selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image115.png "App settings section")

6.  Add a new **Application Setting** with the following values:

    -  App Setting Name: **paymentsAPIUrl**

    -  Value: Enter the **HTTPS** URL for the Payments API App with **/api/nvp** appended to the end

    > **Example**: <https://paymentsapi0.azurewebsites.net/api/nvp>

    ![In the Application settings section of the App Service blade, the previously defined application setting values are selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image116.png "App settings")

7.  Add another **Application Setting** with the following values:

    -  App Setting Name: **offersAPIUrl**

    -  Value: Enter the **HTTPS** URL for the Offers API App with **/api/get** appended to the end

    > **Example**: <https://offersapi4.azurewebsites.net/api/get>

    ![In the Application settings section of the App Service blade, the previously defined application setting values are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image117.png "App settings section")

8.  Click on **Save**.

    ![The Save button is boxed in red on the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image44.png "App Service blade")

>**Note**: Ensure both of the API URLs are using **SSL** (https://), or you will see a CORS errors.

#### Subtask 2: Validate App Settings are correct

1.  On the **App Service** blade, click on **Overview**.

    ![Overview is selected on the left side of the App Service blade.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image119.png "App Service blade")

2.  In the **Overview** pane, click on the **URL** for the Web App to open it in a new browser tab.

    ![On the right side of the App Service blade, under Essentials, the URL (http://contososportsweb2101.azurewebsites.net) link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image120.png "App Service blade")

3.  On the homepage, you should see the latest offers populated from the Offers API.

    ![On the Contoso Sports League webpage, Today\'s offers display: Baseball socks, Road bike, and baseball mitt.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image121.png "Contoso Sports League webpage")

4.  Submit several test orders to ensure all pieces of the site are functional.

    ![On the Contoso Sports League webpage, the message Order Completed displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image122.png "Contoso Sports League webpage")

>**Leader Note:** If the attendee is still experiencing CORS errors, ensure the URLs to the Web App in Azure local host are exact.

## Exercise 2: Enabling Telemetry with Application Insights 

To configure the application for logging and diagnostics, you have been asked to configure Microsoft Azure Application Insights and add some custom telemetry.

>**Note**: You may need to create an Application Insights Resource in Azure portal depending on your subscription rights. After it is created, you can configure it and add to the project using the tasks below. To create a new Application Insights resource.

1.  Click **+Create a resource**. Search the Marketplace for Application Insights. **Select** Application Insights.

    ![In this screenshot a new application insights instance is created using the Azure portal.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image184.png "Screenshot of creating a resource")

2.  Click the **Create** button.

    ![A screenshot that provides an overview of Application Insights and a button to click Create.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image185.png "Application insights resource")

3. Enter the name as **Contoso.Apps.SportsLeague.Web.** Choose the existing resource group of **contososports**. Location should be the same location as your resource group.

    ![A dialog that shows the properties of the application insights resource](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image186.png "Application insights creation dialog")

### Task 1: Configure the application for telemetry

#### Subtask 1: Add Application Insights Telemetry to the e-commerce website project

1.  Open the Solution **Contoso.Apps.SportsLeague** in Visual Studio.

2.  Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

    ![In Solution Explorer, the Web folder is expanded, and Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image187.png "Solution Explorer")

3.  Right-click the **Contoso.Apps.SportsLeague.Web** project, and select **Add \| Application Insights Telemetry..**.

    ![In Solution Explorer, on the Web folder\'s right-click menu, Add is selected, and from its menu, Application Insight Telemetry is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image188.png "Solution Explorer")

4.  Expand the **Sending telemetry to** section.

    ![On the Application Insights tab, under Resource Settings, the expand arrow is circled for the Sending telemetry to section.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image189.png "Application Insights tab")

5.  Click on the **Configure settings...** link.

    ![In the Sending telemetry to section, the link to Configure settings is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image190.png "Sending telemetry to section")

6.  In the **Application Insights Configuration** dialog box, change the **Resource Group** to the **contososports** resource group used to host the Web App, and choose the New Application Insights Resource. Next, click **OK**, followed by **Update resource**.

    ![In the Application Insights Configuration dialog box, the Resource Group contososports is selected. In the Application Insights Resource drop-down list box, Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image191.png "Application Insights Configuration dialog box")

7.  Press **Finish** on the Application Insights window.

    >**Note**: You may also have to configure Trace Collection depending on your ID and subscription.

    ![The Finish button is circled in the Application Insights window.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image192.png "Application Insights window")

8.  Once it completes, it displays the following Output and opens a new browser window:

    ![Screenshot of Output.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image193.png "Output")

9.  Open the file **\\Helpers\\TelemetryHelper.cs** located in the **Contoso.Apps.SportsLeague.Web** project.

10. Add the following using statement to the top of the file:

    ```csharp
    using Microsoft.ApplicationInsights;
    ```

11. Add the following code to the **TrackException** method to instantiate the telemetry client and track exceptions:

    ```csharp
    var client = new TelemetryClient();
    client.TrackException(new Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry(exc));
    ```

12. Add the following code to the **TrackEvent** method to instantiate the telemetry client and track event data:

    ```csharp
    var client = new TelemetryClient();
    client.TrackEvent(eventName, properties);
    ```

13. Save the **TelemetryHelper.cs** file.

#### Subtask 2: Enable client side telemetry

1.  Open the Azure Management Portal (<http://portal.azure.com>). In the navigation menu to the left, click **All Services**. Filter by **Application Insights** and then select the appropriate result.

    ![On the left of the Azure Portal, All services is selected. On the right, Application Insights is in the search box and the result is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image194.png "Azure Portal")

2.  Click the Application Insights instance associated with the Contoso E-Commerce Site.

    ![Under Name, Contoso.Apps.SportsLeague.Web displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image195.png "Name section")

3.  In the tiles up top, click on **Getting Started**.

    ![From the Configure menu, Getting started is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image196.png "Configure menu")

4.  In the portal, navigate to How-to Guides-> Collect data-> Configure applications-> Web Pages -> JavaScript.

    ![Screenshot of the MONITOR AND DIAGNOSE CLIENT SIDE APPLICATION arrow.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image197.png "MONITOR AND DIAGNOSE CLIENT SIDE APPLICATION ")

5.  Select and copy the full contents of the JavaScript on the **Client application monitoring and diagnosis** blade.

    ![Under Guidance in the Client application monitoring and diagnosis blade, JavaScript displays. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image198.png "Client application monitoring and diagnosis blade")

6.  Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

7.  Open **Views \> Shared \> \_Layout.cshtml**.

    ![In Solution Explorer, under Views\\Shared, Layout.cshtml is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image199.png "Solution Explorer")

8.  Paste in the code before the **\</head\>** tag.

    ![In Layout.cshtml, code displays, and several lines are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image200.png "Layout.cshtml tab")

9.  Save the **\_Layout.cshtml** file.

#### Subtask 3: Deploy the e-commerce Web App from Visual Studio

1.  Navigate to the **Contoso.Apps.SportsLeague.Web** project located in the **Web** folder using the **Solution Explorer** in Visual Studio.

    ![In Solution Explorer, under the Web folder, Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image201.png "Solution Explorer")

2.  Right-click the **Contoso.Apps.SportsLeague.Web** project, and select **Publish**.

    ![From the Contoso.Apps.SportsLeague.Web right-click menu, Publish is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image202.png "Solution Explorer")

3.  Click **Publish** again when the Publish dialog appears.

    Launch a browser **outside of Visual Studio** for testing if the page is loaded in Visual Studio.

4.  Click a few links on the published E-Commerce website, and submit several orders to generate some sample telemetry.

### Task 2: Creating the web performance test and load test

#### Subtask 1: Create the load test

1.  Open the Azure Management Portal (<http://portal.azure.com>). In the navigation menu to the left, click **All Services**. Filter by **Application Insights** and then select the appropriate result.

    ![On the left of the Azure Portal, All services is selected. On the right, Application Insights is in the search box and the result is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image194.png "Azure Portal")

2.  Click the Application Insights instance associated with the Contoso E-Commerce Site.

    ![In the Name section, Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image204.png "Name section")

3.  Click **Performance Testing**.

    ![On the Configure menu, Performance Testing is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image205.png "Configure menu")

4.  Click the **Set Organization** button to associate/create an Azure DevOps account.

    ![On the Application Insights blade, Set Organization is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image206.png "Application Insights blade")

5.  On the Organization Settings tile, click **Or Create New**.

    ![On the Organization Settings tile, the Or Create New link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image207.png "Account tile")

6.  Specify a unique name for the account and select a region.

    >**Note**: The region may differ from the region you have deployed your resources.

    ![On the Organization Settings blade, under Azure DevOps Account, contososportsis selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image208.png "Account Settings blade")

7.  Click **Subscription**, and select **your Subscription**.

    ![The Subscription option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image209.png "Subscription option")

8.  Click **Select location**. Next, select a Location.

    ![The Select location option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image210.png "Select location option ")

    > **Note**: The location tile may disappear after setting your Subscription.

9.  Then, click **OK**.

    > **Note**: The Azure DevOps account creation will take a minute to complete.

10. Click **New**.

    ![On the Application Insights blade, the New button is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image211.png "Application Insights blade")

11. Click on **Configure Test Using**.

    ![The Configure Test Using option displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image212.png "Configure Test Using option")

12. Specify the **URL** to the Contoso E-Commerce site, and click **Done**.

    ![In the Configure test using blade, the https://contososportsweb3.azurewebsites URL is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image213.png "Configure test using")

13. Name the test **ContosoSportsTest**, and click the **Run test** button.

    ![On the New performance test blade, under Name, ContosoSportsTest is selected. At the bottom, the Run test button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image214.png "New performance test blade")

14. Wait until the load test has completed. This may take 5-10 minutes.

    ![In the Recent runs section, the load test for ContosoSportsTest has a state of Completed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image215.png "Recent runs section")

#### Subtask 2: View the Application Insights logs

1.  Using a new tab or instance of your browser, navigate to the Azure Management portal <http://portal.azure.com>.

2.  On the left menu area, click **All services**.

3.  On the **All Services** blade, filter for **Application Insights** and choose the appropriate result.

4.  On the **Application Insights** blade, select the Application Insights configuration you created for the e-commerce website.

    ![The Application Insights configuration option Contoso.Apps.SportsLeague.Web is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image216.png "Application Insights configuration option")

5.  View the performance timeline to see the overall number of requests and page load time.

    >**Note**: If necessary, click the informational tile at the top to go to the new Overview experience.

    ![The Health graph displays the performance overview timeline of overall requests and response times.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image217.png "Health graph")

6.  Under **USAGE (PREVIEW)** menu area. click the **Events** menu option. Then, click one of the bars in the bar chart in the lower part of the screen. 

    ![A screenshot using the Events button under the Usage Preview section](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image218.png "The Usage Preview section")

7.  After several minutes, you should see several custom events from your previous order testing. This is reported through the TelemetryClient's TrackEvent method.

    >**Note**: If you do not see data here, come back later after the lab is complete.

    ![In the Custom events section, OrderCompleted is 3, and SuccessfulPaymentAuth is 3.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image219.png "Custom events section")

## Exercise 3: Automating backend processes with Azure Functions and Logic Apps

Contoso wants to automate the process of generating receipts in PDF format and alerting users when their orders have been processed using Azure Logic App and Functions. To run custom snippets of C\# or node.js in logic apps, you can create custom functions through Azure Functions. [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) offers server-free computing in Microsoft Azure and are useful for performing these tasks:

-   Advanced formatting or compute of fields in logic apps

-   Perform calculations in a workflow

-   Extend the logic app functionality with functions that are supported in C\# or node.js

### Task 1: Create an Azure Function to Generate PDF Receipts

1.  Click the **+Create a resource** button found on the upper left-hand corner of the Azure portal and then click **Compute \> Function App**. Then in the new blade, select your Subscription, type an unique App name that identifies your function app, then specify the following settings:

    -   [**Resource Group**](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview): Use the existing resource group, **contososports**.

    -   [**Hosting plan**](https://docs.microsoft.com/en-us/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview): One of the following plans:

        -   **Hosting plan**: The default hosting plan type for Azure Functions is **Consumption Plan**. When you choose a consumption plan, you must also choose the **Location**. For now, select **App Service Plan**.

        -   **App Service plan**: An App Service plan requires you to create an **App Service plan/location** or select an existing one. These settings determine the [location, features, cost, and compute resources](https://azure.microsoft.com/pricing/details/app-service/) associated with your app. For now, select the existing App Service Plan you have been using so far in this lab. 

        -   **Storage account**: Each function app requires a storage account. Choose the existing storage account by clicking **Select Existing** and choosing the storage account in the **contososports** resource group.

    ![On the left side of the Portal, the Create a resource button is selected. In the middle, under New, Compute is selected. On the right, under Compute, Function App is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image221.png "Azure Portal")

2.  Click **Create** to provision and deploy the new function app.

    ![Under Function App, the App name field is set to ContosoFunctionApp, and at the bottom the Create button is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image222.png "Function App section")

3.  Open the Function App you just created. Click the **+** besides **Functions**, select **In-portal** and select **Continue**.

    ![In Function Apps Getting Started,In-Portal is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image223.png "Function Apps")

4.  In the **Azure Functions for .NET getting started** card, click the **More templates...#**. Select **Finish and view templates**.

    ![In the Azure Portal, under Azure Functions for .NET getting started dialog, the More templates tile is selected. .](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image224.png "Azure Portal")

5.  In the **Choose template** dialog, select **HTTP trigger**.

    ![In the New Function blade, settings are consistent with instructions.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image225.png "View files expand arrow")

5.  In the **HTTP trigger New Function** blade, name the function **ContosoMakePDF** and then click **Create**.

    ![In the New Function blade, settings are consistent with instructions.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image225a.png "View files expand arrow")

6.  Expand the **View files** area on the right of the code window and then click **Upload**.

    ![Screenshot of the Upload button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/function-view-files.png "Upload button")

    ![Screenshot of the Upload button.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image226.png "Upload button")

7.  Upload the following files in the (Contoso Sports League\\Contoso.CreatePDFReport) folder beneath: C:\\MCW:

    -   ViewModels.csx
    -   CreatePdfReport.csx
    -   run.csx
    -   sample.dat
    -   StorageMethods.csx
    -   Project.json

    ![The previously mentioned files display.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image227.png "Files")

8.  Click on **run.csx**, to refresh the code editor.

    ![In the Code Editor, on the right, run.csx is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image228.png "Code Editor")

9.  Expand the **Log** pane on the bottom.

    ![The arrow button besides the Logs tab is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image229.png "Logs window")

    >**Note**: You should see several messages about downloading dependent assemblies such as the Azure SDK and iText Sharp that were defined in the project.json file.

10. Select the name of your function app, and then click on **Platform Features** followed by **Application settings**.

    ![In the Azure Portal, under Function Apps, ContosoFunctionApp is selected. Under General Settings, Application settings is selected. The Platform Features link is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image230.png "Azure Portal")

10. In the **Application Settings**, add a new entry called **contososportsstorage**, and paste the value of the **connection string** noted in an earlier exercise. Also expand the FUNCTIONS_EXTENSION_VERSION attribute and change the value from ~2 (the Azure default now) to ~1. Click **Save** after adding the value.

    ![In the Application settings section, contososportsstorage and its value are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image231.png "App settings section")

    >**Note**: You can find the Connection String value by opening the storage account, and clicking the **Access Keys** tile. Be sue to use the connection string and NOT the key itself.
    >**Note**: Azure Function Apps now use FUNCTIONS_EXTENSION_VERSION with a *default* setting of ~2 (version 2). The Student lab solution requires v1 to function properly. 

11. Back in your function, open the **sample.dat** file, and select as well as copy (Ctrl+C) the test data.

    ![The Sample.dat file displays.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image232.png "Sample.dat file")

12. Select the **Run.csx** file, click on the **Test** tab, and replace the contents by pasting (CTRL-V) in the Test tab Request Body. Ensure that there are no parameters.

    ![Screenshot of the run.csx file, and the Test tab request body.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image233.png "Run.csx file, Test tab request body")

13. Select the **View Files** tab, select **Run.csx**, and click **Run**.

14. You should see messages in the Logs window stating the Webhook was triggered, and the PDF was generated / saving it the storage account. Also, you should see that actual message text in the Output Window.

    ![In the run.csx file, under Logs, messages stating the Webhook was triggered and the PDF was generated are circled. In the Test tab request body, under Output, the message text is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image234.png "Run.csx file, Test tab request body")

15. To see that the PDF indeed landed in the receipts container in blob storage, download **Microsoft Storage Explorer** at [http://storageexplorer.com](http://storageexplorer.com/). Use Microsoft Storage Explorer to verify the PDF landed on the Blob Container for receipts. You may need to refresh and/or select another folder, and arrive back to the receipts folder to see the PDF.

    ![In Storage Explorer, on the left, the following path is expanded: Storage Accounts\\contososportsstorage01\\Blub containers. Under Blob Containers, receipts is circled. On the right, on the receipts tab, ContosoSportsLeague-Store-Receipts-38.pdf is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image235.png "Storage Explorer")

### Task 2: Create an Azure Logic App to Process Orders

Without writing any code, you can automate business processes more easily and quickly when you create and run workflows with Azure Logic Apps. Logic Apps provide a way to simplify and implement scalable integrations and workflows in the cloud. It provides a visual designer to model and automate your process as a series of steps known as a workflow. There are [many connectors](https://docs.microsoft.com/en-us/azure/connectors/apis-list) across the cloud and on-premises to quickly integrate across services and protocols.

The advantages of using Logic Apps include the following:

-   Saving time by designing complex processes using easy to understand design tools

-   Implementing patterns and workflows seamlessly, that would otherwise be difficult to implement in code

-   Getting started quickly from templates

-   Customizing your logic app with your own custom APIs, code, and actions

-   Connect and synchronize disparate systems across on-premises and the cloud

-   Build off of BizTalk server, API Management, Azure Functions, and Azure Service Bus with first-class integration support

1.  Next, we will create a Logic App that will trigger when an item is added to the **receiptgenerator** queue. In the Azure Management Portal, click the **+Create a resource** button, search for **Logic App**, click the returned Logic App result, and click **Create**.

    ![In the Azure Portal, under Marketplace, Everything is selected. Under Everything, Logic App is in the search field. Under Name, Logic App is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image236.png "Azure Portal")

2.  Fill out the name as **ContosoLogicApplication** along with your subscription, and use the existing resource group **contososports**. Choose the **same region** as your Web App and storage account. Click **Create**.

    ![In the Create logic app blade, ContosoLogicApplication is in the Name field. Under Resource group, the Use existing radio button is selected, and contososports is the name.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image237.png "Create logic app blade")

3.  Open up the logic app after it is deployed by clicking **All Services**, searching for and selecting **Logic App** and selecting the Logic App you just created.

    ![In the Azure Portal, logic is in the search field, and under that, Logic apps is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image238.png "Azure Portal")

4.  Click on the **Logic App Designer** link.

    ![In the Logic app blade, under Development tools, Logic App Designer is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image239.png "Logic app blade")

5.  In the Logic Apps Designer, under **Templates**, select **Blank Logic App**.

    ![In the Logic Apps Designer, the Blank Logic App tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image240.png "Logic Apps Designer")

6.  Select **Azure Queues**. You may have to search for it.

    ![In the Services section, the Azure Queues tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image241.png "Services section")

7.  Select **Azure Queues -- When there are messages in a queue**.

    ![In the Search all triggers section, Azure Queues - When there are messages in a queue is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image242.png "Search all triggers section")

8.  Specify **ContosoStorage** as the connection name, select the Contoso storage account from the list, and click **Create**.

    ![In When there are messages in a queue, the Connection Name is ContosoStorage, and under Storage Account, contosostorage123321 is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image243.png "When there are messages in a queue ")

9.  Select the **receiptgenerator** queue from the drop-down, click **New Step**, and **Add an Action**.

    ![Under When there are messages in a queue, the Queue name is set to receiptgenerator. At the bottom, the New Step and Add an action buttons are selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image244.png "Queue name")

10. Select **Azure Functions**.

    ![In the Choose an action section, under Services ,the Azure Functions tile is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image245.png "Choose an action")

11. Click the **Azure Function App** you just created.

    ![Under Azure Functions, on the Actions tab, a single Action, the Azure function contosofunction2101, is listed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image246.png "Azure Functions")

12. Click the Azure function **ContosoMakePDF**.

    ![Under Azure Functions, on the Actions tab, a single Action, the Azure function contosofunction2101, is listed.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image247.png "Azure Functions")

13. Type this in the Request Body:

    ```json
    {"Order": pick MessageText from list on right }
    ```

    Make sure the syntax is json format. Sometimes the ":" will go to the right side of MessageText by mistake. Keep it on the left. It should look like this:

    ![Under ContosoMakePDF, the previous JSON code is typed in the Request Body, and to the right of this, in Insert parameters from previous steps, Message text is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image248.png "ContosoMakePDF")

14. Click **Save** to save the Logic App.

15. There is one modification we need to make in the code. Click on the **CodeView** button.

    ![In the Logic App, the CodeView button is selected from the top menu.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image250.png "Logic App")

16. Find the line of code in the body for the Order item that reads the MessageText value from the queue, and add the base64 function around it to ensure it encoded before passing it off to the Azure function. It should look like the following:

    ```json
    "Order": "@{base64(triggerBody()?['MessageText'])}"
    ```

    ![In the Order item code, the following line of code is circled: \"Order\": \"@{base64(triggerBody()?\[\'MessageText\'\])}\"](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image251.png "Order item code")

    Click **Save** again.

17. Run the logic app. It should process the orders you have submitted previously to test PDF generation. Using Azure Storage Explorer or Visual Studio Cloud Explorer you can navigate to the storage account and open the receipts container to see the created PDFs.

    ![In Azure Storage Explorer, on the left, the following tree view is expanded: Storage Accounts\\contososportsstorage01r\\Blob Containers. Under Blob Containers, receipts is selected. On the right, the ContosoSportsLeague-Store-Receipt-72.pdf is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image252.png "Azure Storage Explorer")

18. Double click it to see the Purchase receipt.

19. Now, click the **Designer** button in the Logic Apps Designer screen. add two more steps to the flow for updating the database and removing the message from the queue after it has been processed. Switch back to the designer, click **+ New step**.

    ![In Designer, the New Step link is circled. Under New step, the Add an action tile is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image254.png "Designer")

20. Select **SQL Server**.

    ![In the Services section, under Services, SQL Server is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image255.png "Services section")

21. Select **SQL Server - Update row**.

    ![In the SQL Server section, on the Actions tab, SQL Server - Update row is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image256.png "SQL Server section")

22. Name the connection ContosoSportsDB, and select the primary ContosoSportsDB database for your solution. Under the user name and password used to create it, click **Create**.

    ![TheUpdate row section displays the previously defined settings.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image257.png "Update row")

23. From the drop-down select the name of the table, **Orders**.

    ![In the Update row section, under Table name, Orders is selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image258.png "Update row section")

24. Press **Save** and ignore the error. Click the **Code View** button.

25. Replace these lines:

    ![Screenshot of code to be replaced.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image259.png "Code view")

    With these:

    ```json
    "OrderDate": "@{body('ContosoMakePDF')['OrderDate']}",
    "FirstName": "@{body('ContosoMakePDF')['FirstName']}",
    "LastName": "@{body('ContosoMakePDF')['LastName']}",
    "Address": "@{body('ContosoMakePDF')['Address']}",
    "City": "@{body('ContosoMakePDF')['City']}",
    "State": "@{body('ContosoMakePDF')['State']}",
    "PostalCode": "@{body('ContosoMakePDF')['PostalCode']}",
    "Country": "@{body('ContosoMakePDF')['Country']}",
    "Phone": "@{body('ContosoMakePDF')['Phone']}",
    "SMSOptIn": "@{body('ContosoMakePDF')['SMSOptIn']}",
    "SMSStatus": "@{body('ContosoMakePDF')['SMSStatus']}",
    "Email": "@{body('ContosoMakePDF')['Email']}",
    "ReceiptUrl": "@{body('ContosoMakePDF')['ReceiptUrl']}",
    "Total": "@{body('ContosoMakePDF')['Total']}",
    "PaymentTransactionId": "@{body('ContosoMakePDF')['PaymentTransactionId']}",
    "HasBeenShipped": "@{body('ContosoMakePDF')['HasBeenShipped']}"
    ```

26. And modify the path variable to include the index key or OrderId to be as follows:

    ```json
    "path": "/datasets/default/tables/@{encodeURIComponent(encodeURIComponent('[dbo].[Orders]'))}/items/@{encodeURIComponent(encodeURIComponent(body('ContosoMakePDF')['OrderId']))}"
    ```

    The code should now look as follows for the update\_row method:

    ![Screenshot of replacement code.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image260.png "Code")

27. **Save** and return to the designer.

28. Your updated designer view should look like this:

    ![The Update row section displays the purchase fields.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image261.png "Update row section")

29. Finally, let us add one more step to remove the message from the queue. Press **+New Step**. Type in Queue in the search box, and select Azure Queues -- Delete message.

    ![In the Choose an action section, queue is typed in the search field. Under Services, Azure Queues is selected. On the Actions tab, Azure Queues - Delete message is selected. ](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image262.png "Choose an action section")

30. Select the **receiptgenerator** queue from the list.

31. Select **Message Id** **\>** **Pop Receipt** from the list, and click **Save**.

    ![In the Update row section, on the left in the Delete message fields, Message ID and Pop receipt are selected. On the right, under When there are messages in a queue, Message ID and Pop receipt are selected.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image263.png "Update row section")

32. Click Run on the Logic App Designer, and then run the Contoso sports Web App and check out an Item.

33. Run the admin website app, and select the last Details link in the list.
    ![Screenshot of the Details link.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image264.png "Details link")

34. You should now see a Download receipt link because the database has been updated.

    ![In the Order Details window, the Download receipt link is circled.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image265.png "Order Details window")

35. Click on the Download receipt link to see the receipt.

36. Return to the Logic app and you should see all green check marks for each step. If not, click the yellow status icon to find out details.

    ![In the Logic app, all steps have green checkmarks.](images/Hands-onlabstep-by-step-Moderncloudappsimages/media/image267.png "Logic app")

## After the hands-on lab

Duration: 10 minutes

### Task 1: Delete resources

1.  Since the HOL is now complete, go ahead and delete all of the Resource Groups that were created for this HOL. You will no longer need those resources and it will be beneficial to clean up your Azure Subscription.

You should follow all steps provided *after* attending the hands-on lab.

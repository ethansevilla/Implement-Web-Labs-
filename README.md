# How to Implement Web Apps Using Microsoft Azure


## Introduction
In this tutorial, you will learn how to implement web apps using Microsoft Azure. You will create and configure an Azure Web App to display a Hello World application in an external GitHub repository, deploy code, configure settings, and learn how to scale and monitor the web app.



## Prerequisites
Before you begin, ensure you have the following:
- A Microsoft Azure account
- Basic knowledge of web development
- GitHub Repository 
- Azure CLI installed on your machine



### Task 1: Create a Azure Web App
1. In the Azure portal, navigate to "Create a resource" > "App Services" > "Web App".
2. Fill in the required fields:
    - **Name:** Your web app name
    - **Publish:** Code
    - **Runtime stack:** Select the runtime stack you want to use (e.g., .NET, Node.js, Python)
    - **Operating System:** Choose the operating system
    - **Region:** Select the same region as your app service plan
    - **App Service plan:** Select the app service plan 
3. Click on "Review + create" and then "Create".

    <img src="https://github.com/user-attachments/assets/8adc3cb3-a682-4df8-a4b3-16afc1bb220d"> 
   <img src="https://github.com/user-attachments/assets/96c8536f-c2a7-4ea4-8659-21cb861f5bc5">  
   <img src="https://github.com/user-attachments/assets/6471c4f3-5f4e-4a24-b7b2-28fd762e3879"

## Task 2: Deploy Code to the Web App


1. In the Azure portal, navigate to your web app's resource page.
   <p>
      <img src="https://github.com/user-attachments/assets/c6eb0301-e1ba-4e1b-b287-080b7d6236c2"
   </p>
2. click the Default Domain link to display the default web page in a new browser tab.
   <p>
     <img src="https://github.com/user-attachments/assets/6b1a65b6-2c75-4b55-a4ec-fabdbffd8381"
   </p> 
3. Go back to Azure Portal, in the Deployment section of the Web App page, click Deployment slots
   <p>
     <img src="https://github.com/user-attachments/assets/3c9824ae-c15f-4049-b3e3-e81d19fdd3ce"
   </p>


4. Click Add Slot and add the new slot with the following setting of the name: staging, and (Do not clone) settings
   <p>
     <img src= "https://github.com/user-attachments/assets/a591b940-0369-40fb-8a42-24fc13f95cbb" 
   
  </p> 
  <p>
     <img src="https://github.com/user-attachments/assets/da0d2476-a63e-41b8-9d3f-e806014fd334"
  </p>


## Task 3: Configure Web App Deployment Settings

##In this task, we will configure the Web App Deployment settings for continuous deployment.

1. Go to Deployment Center, and go to Settings
2. Go to "Source*" drop-out list and select External Git.
3. In the External Git settings, in the repository field, enter this external Github link: https://github.com/Azure-Samples/php-docs-hello-world
   This GitHub repository link is sample that holds and demonstrates a tiny Hello World PHP app for App Service
4. In Branch* field, enter master
5. select Save
   <p>
       <img src="https://github.com/user-attachments/assets/48e90701-f403-42c2-968d-522e1bd40959"
   </p> 
6. In the staging slot, select Overview and select the Default Domain link, and open URL. The staging slot should display Hello World 
   <p>
     <img src= "https://github.com/user-attachments/assets/ce342cfe-fa32-4cce-b02a-af9fc95c9533"
   </p> 


## Task 4: Swap Deployment Slots 

### In this task, we will swap the staging slot with the production slot. This action will let us use the code that was tested in the staging slot and move it to production. 
1. In the Deployment slots blade, select Swap
   <p>
     <img src="https://github.com/user-attachments/assets/c65ca04d-48a2-41b6-a718-80654d392ce8"
   </p>
2. Review the default settings in the Swap blade, and click Start Swap
   <p>
     <img src="https://github.com/user-attachments/assets/ff580593-adb8-4a77-a92f-7e60d5a682e1"
   </p>
3. Go back to the Overview blade of the Web App and click the Default domain link
   <p>
     <img src="https://github.com/user-attachments/assets/9891b7c7-cc51-47f9-9101-9842f1360b4a"
   </p>
4.  The production web page should display the Hello World page
   <p>
     <img src="https://github.com/user-attachments/assets/043da934-63f2-4f14-933a-a98d3091bdd1"
   </p>



### Task 5: Configure Autoscaling of Azure Web App

### In this task, we will configure the Azure Web App with autoscaling, which allows you to maintain optimal performance during high traffic. 
1. In the Settings section of Web App, select Scale out(App Service Plan).
    <p>
      <img src="https://github.com/user-attachments/assets/0bbe6a36-c409-4ab2-b058-ee108ab0938b"
    </p> 
2. In the Scaling section, select Automatic as the Scale out method and the Maximum burst field, select 2 and select save
   <p>
     <img src="https://github.com/user-attachments/assets/637242e6-6324-4ed8-9b1e-5ef271d46b74"
   </p> 
3. Go to Diagnose and solve problems on the left pane.
   <p>
     <img src="https://github.com/user-attachments/assets/3e220fd4-ecdb-44f4-83c9-0cc46ff610ed"

   </p> 
4. Go to the Load Test your App box, select Create Load Test and Select + Create and give a unique name. Select Review + Create and then Create.
5. Wait for the load test to be created and select Go to resource
6. In the Overview,  go to Add HTTP requests and select Create
   <p>
     <img src="https://github.com/user-attachments/assets/cc4932e9-581f-47e3-b3e4-4b83fcfdb0b3"
   </p>
7. On the Test Plan tab, click Add request and in the URL field, paste in your Default domain URL. And select Review + create and Create.
   <p>
     <img src="https://github.com/user-attachments/assets/9890afc3-528f-4f71-887d-5a1e33b07193"
   </p>  
   <p>
     <img src="https://github.com/user-attachments/assets/c80ab6d9-94ac-478e-8ab9-ae0bc9d0eae9"
   </p>
8. See and review the test results. Select Stop to complete test run
   <p>
     <img src="https://github.com/user-attachments/assets/0c487e47-3879-4059-abf2-0d1ececb4653"
   </p> 

### Task 6: Clean Up Resources 
1. Go to Azure portal, select and delete Resource Groups by entering the name
2. For Alternative cleanup, use the Azure PowerShell method and enter Remove-AzResourceGroup -Name resourceGroupName
   <p>
     <img src="https://github.com/user-attachments/assets/5e50b6c7-edd3-4203-9d5e-ce7eb1a27b2b"
   </p>
## Conclusion
Congratulations! You have successfully implemented a web app using Microsoft Azure. You have learned how to create and configure an Azure Web App, deploy code to it, configure settings, and scale and monitor the web app.

## Additional Resources
- [Azure Web Apps Documentation](https://docs.microsoft.com/en-us/azure/app-service/)
- [Azure CLI Documentation](https://docs.microsoft.com/en-us/cli/azure/)
- [Azure DevOps Documentation](https://docs.microsoft.com/en-us/azure/devops/?view=azure-devops)

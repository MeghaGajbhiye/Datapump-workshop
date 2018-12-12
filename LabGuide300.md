Updated: December 10, 2018

## Introduction

This lab guide will walk you through the process of creating a Compute Linux Instance.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

## Objectives

- Create a compute linux instance.

## Required Artifacts

- An oracle cloud account with Autonomous Data Warehouse Cloud Service.
- A public and private ssh keys.

### **STEP 1**: Create a **Compute Oracle Linux instance**.

- From the Cloud UI dashboard click on the **Compute** service.
    
    ![](images/datapump/compute1.png) 
   
- Select a compartment by clicking on **Pick a compartment**.
    
    ![](images/datapump/compute2.png)

- Click on **Create Instance**.
    
    ![](images/datapump/compute3.png)
    
- Give an **instance name** and select the **availability domain**. Keep the **Operating System** as **default** which is **Oracle Linux**.
    
    ![](images/datapump/compute4.png)

- Keep instance type as **Virtual Machine** and let the **instance shape** be **default**.  
    
    ![](images/datapump/compute5.png)

- I am not configuring any boot volume for the demo. Go ahead and upload an **ssh public key** by clicking on **Choose Files**. The format of the file should be **.pub**.
    
    ![](images/datapump/compute6.png)

- Leave everything as default and click on **Create** 
    
    ![](images/datapump/compute7.png)

- Once the instance is created, click on the instance name and note down the **public IP address.**

    ![](images/datapump/compute15.png)


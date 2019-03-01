Updated: December 10, 2018

## Introduction

This lab guide will walk you through the process of creating Autonomous Data Warehouse cloud service. We will then connect it to SQL Developer and will import a table from local machine.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

## Objectives

- Create an Autonomous Data Warehouse Cloud Service.
- Connect ADWC to SQL Developer and create a credential.
- Import a table from local machine.

## Required Artifacts

- An oracle cloud account with Autonomous Data Warehouse Cloud Service.
- SQL Developer.

### **STEP 1**: Create Autonomous Data Warehouse Cloud Service (ADWC).


- Login into your cloud account. Click on **Menu** and click on **Autonomous Data Warehouse.**

    ![](images/datapump/compute8.png)

- Click on **Create Autonomous Data Warehouse**.

    ![](images/datapump/compute9.png)

- On Details screen, select the **Compartment**, enter **Display Name and Database Name**. Keep the **CPU Core Count and Storage** as **1**. Finally enter the **Password** and **Confirm Password**.

    - **Note** : Make sure your password doesn't have **"@"**. It might create a problem later.
    
    ![](images/datapump/compute10.png)

- Select a **License Type** and click on **Create Autonomous Data Warehouse**.
    
    ![](images/datapump/compute11.png)

- Once your ADWC instance is avaiable, click on the ADWC instance that you have just created. Then Click on **DB Connection**. Download **Client Credentials Wallet** by clicking on **Download**.
    
    ![](images/datapump/compute13.png)

- Enter the **Password** and click on **Download**.

    ![](images/datapump/compute14.png)
    
  Note: Remember this password. This can be different than the password you have entered while creating ADWC instance.

- For quick access, create a directory **DemoADWC** and copy paste this zip wallet file there. 

### **STEP 2**: Connect ADWC with SQL Developer and create a credential.

- Connect ADWC with SQL Developer.
    
    - Open SQL Developer.
    
    - Click on **Connections** 
    
      ![](images/datapump/compute31.png)
    
    - Set the following parameters:
    
      **Connection Name** : `Enter any Connection Name`
      
      **Username** : `admin`
      
      **Password** : `Password that was entered during ADWC instance creation.`
      
      **Connection Type** : `Cloud PDB`
      
      ![](images/datapump/compute32.png)

      **Configuration File** : `Click on Browse and select the wallet that you have downloaded in Step 1`
      
      **Keystore Password** : `Password entered while downloading wallet`
      
      **Service**  : `Service name starts with your ADWC Database Name followed by high/medium/low. Select high service for this demo.`
      
    - Click on **Test**. If it shows **Status as Success**, your ADWC is connected to SQL Developer.
 
        ![](images/datapump/compute33.png)
        
    - Go to Oracle Compute instance. Click on **Menu**, **Identity**, **Users**.
    
        ![](images/datapump/compute34.png)
        
    - Click on **gse-admin_ww@oracle.com** user.
    
        ![](images/datapump/compute35.png)
    
    - Click on **Auth Tokens**. 
    
        ![](images/datapump/compute36.png)  
     
    - Click on **Generate Token**  
     
        ![](images/datapump/compute37.png)
        
    - Give a **Description** and click on **Generate Token**
    
        ![](images/datapump/compute38.png)
    
        Note:  Make sure to save the token in a text file for future reference. 
      
    - Go back to SQLDeveloper and copy paste the following script:
    
      Change the following parameters before copy pasting the script: 
      
      - **username**: `gse-admin_ww@oracle.com`
    
      - **password**: `Generated token`
      
      **Script**: 
      
        BEGIN      
            DBMS_CLOUD.CREATE_CREDENTIAL(
            credential_name => 'DEF_CRED_NAME',
            username => 'gse-admin_ww@oracle.com',
            password => 'Generated Token'
            );
            END;

### **STEP 3**: Create a table in ADWC. 

- Download following file. [Channels](images/datapump/channels.csv) 

- Right click on **Tables** and click on **Import Data**. 

    ![](images/datapump/compute39.png)

- Leave the **Source** as **Local File**. Open the file just downloaded. 

    ![](images/datapump/compute40.png)    
    
- Click on *next* and give *Table Name* as **channels**. Click on **next**, **next** and **finish**.

    ![](images/datapump/compute41.png)  
    
- A pop up appears to show data is imported. Click on **OK**.

    ![](images/datapump/compute42.png)  

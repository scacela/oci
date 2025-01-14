# Set Up Digital Twin Running Environment


## Introduction
In this session, we will configure OCI tenancy with required IAM resources (compartment, user/group, compartment), create OCI services like OKE, OCI Streaming, Object Storage, and OCI Notification service.



### Services will be provisioned in this Lab:
- **Identity and Access Management (IAM)**:
    - **Compartment**: Logical container for resources, used to manage access to resources as a function of Identity and Access Management (IAM). 
    - **Policy**: An arrangement of statements used to manage access to resources as a function of Identity and Access Management (IAM). 
    - **Dynamic Group**: An arrangement of matching rules used to manage permissions to enable specific resources to access other specified resources.
- **Oracle Data Science Platform**: Serverless platform that lets developers create, run, and scale applications without managing any infrastructure. 
- **Oracle Kubernetes Engine (OKE)**: Oracle-managed container orchestration service that can reduce the time and cost to build modern cloud native applications. 
- **Oracle Object Storage**: Securely store any type of data in its native format, with built-in redundancy. 
- **Virtual Cloud Network (VCN)**: Customizable and private cloud network.


*Estimated Time*: 30 minutes



### Objectives
1. Create the OCI services needed to run digital twin model and anomaly detection solution
2. Understand the OCI services

### Prerequisites
1. Fully-privileged access to an OCI Tenancy (account).
2. Sufficient availability of resources in your OCI Tenancy. You can check resource availability [here](https://docs.oracle.com/en-us/iaas/Content/General/Concepts/servicelimits.htm#Viewing).



## Task 1 Create Resource Manager Stack

Resource Manager automates deployment and operations for all Oracle Cloud Infrastructure resources. Using the infrastructure-as-code (IaC) model, the service is based on Terraform, an open source industry standard that lets DevOps engineers develop and deploy their infrastructure anywhere

1. Log into your Oracle Cloud Infrastructure (OCI) tenancy. 

2. Click the `Deploy to Oracle Cloud` button below, this will open the Create stack page into a new browser tab.

[![Deploy to Oracle Cloud](https://oci-resourcemanager-plugin.plugins.oci.oraclecloud.com/latest/deploy-to-oracle-cloud.svg)](https://cloud.oracle.com/resourcemanager/stacks/create?region=home&zipUrl=https://github.com/scacela/oci-anomaly-detection-pipeline/archive/refs/tags/v1.0.0.zip)

3. In the `Stack Information` section, select the checkbox to confirm that you accept the [Oracle Terms of Use](https://cloudmarketplace.oracle.com/marketplace/content?contentId=50511634&render=inline).

![create stack 1](./images/create_stack1.png)

The **OCI Anomaly Detection Pipeline** will pop up under `Stack Information`. Click **Next** to proceed to the `Configure Variables` section.

![create stack 2](./images/create_stack2.png)

4. In `Configuration variables` section, select `Region` and `Parent Compartment` to choose where you want the infrastructure stack to be deployed. 

![create stack config variable](./images/create_stack3.png)

For each resource that you wish to deploy, verify that the corresponding checkbox is selected in the `Select Resources` tile. Optionally, you can customize the attributes of each selected resource once an additional tile that presents configuration options for its respective resource appears below.

![create stack config var](./images/create_stack4.png)

When you are finished editing your variables in the `Configure Variables` section, click **Next** to proceed to the `Review` section.

5. Select the checkbox for **Run Apply**, and click **Create**. OCI Resource Manager then will start run the job.

![create stack review](./images/create_stack_review.png)

You can monitor the deployment by monitoring the `Logs` window.

![create stack log](./images/resource_manager_log.png)

The job will take approximately 25 minutes to run.

## Task 2 Review Stack Job Resources

1. Once the Job state turns to SUCCEEDED, you can view all the resources provisioned by the stack by click **Job resources**. 

![job succeed](./images/job_succeed.png)

![job resource view](./images/job_resource_show.png)



## Task 3 Verify OCI Object Storage

Oracle Cloud Infrastructure Object Storage service is an Internet-scale, high-performance storage platform that offers reliable and cost-efficient data durability. You can check and verify the Object Storage Bucket that created by the Resource Manager job.

1. Click the Navigation Menu in the upper left, navigate to **Storage**, and select **Buckets**.
![os navigation](./images/bucket_navigation.png)

2. Select the compartments
![os console](./images/os_console.png)

3. Open the bucket **ad_bucket**
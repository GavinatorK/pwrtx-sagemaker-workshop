# pwrtx-sagemaker-workshop
Sagemaker workshop on NASA dataset

## Workshop 

### 1. Introduction
Quickly talk about the NASA dataset and run through visualizations used in the paper to set context on what data we have, what constitutes a failure and the data distributions etc.

### 2. Dataset Formulation
Based on what is called out in the paper, we will formulate the dataset with minimal features

### 3. SageMaker Training 
Using dataset from step 3 , we will do 
1. a quick EDA, 
2. do a train validation split 
3. pick a sagemaker algorithm and train a model 
4. Download training report and understand feature importances

### 4. SageMaker Inference

we will use test data to run through SageMaker inference and compare the results to actual values and look at some metrics in the process.


## Log In

![Event Engine Dashboard Login Screenshot](img/ee-dashboard-login.jpg)

We will be using AWS Event Engine for the labs in order to prevent you from incurring any expense.

To access the AWS Event Engine Team Dashboard, [open this link in a new tab](https://dashboard.eventengine.run/).

Once the Event has begun, find your name below and enter the 12 digit hash (next to your name) in the Team Dashboard.

From within the Team Dashboard, click on "AWS Console" and then "Open AWS Console". This will open the console in a new tab for you to begin your labs.


!!! warning "IMPORTANT"
    Each attendee will have their own, unique AWS account to perform the labs. Make sure you find your name in the list and only use ** your** hash.  If you don't see your name in the table, please let us know.


| Name              | AWS Event Engine Hash |
| ----------------- | ---------------------- |
| Christopher | 1143-0bd99a3fd4-8a |
| Mobeen      | f2af-042d136e64-d3 |
| Jay         | 315e-029675bef4-05 |
| ayman       | ea34-021b386ff4-79 |
| Ozgur       | f656-0083782e74-7f |
| Raj         | f75c-0763283ca4-37 |
| Extra-1     | b091-0c8280c9b4-10 |


!!! info
    These accounts will be available for you to use until close of business on **04/21/2021**

## Verify Region

For this class, we will be doing all of our work out of the **us-east-1 (N. Virgina)** region. To verify you're using the correct region, the region dropdown at the top right of the screen should read _N. Virginia_.

![Console us-east-1](img/region-selection.png)

## Browser

We recommend you use the latest version of Chrome or Firefox to complete this workshop.


# Getting Started

One way to interact with the AWS platform is by using the [AWS Management Console](https://aws.amazon.com/console/). This intuitive, web-based console allows you to administer all of your AWS resources in a single interface.

## Login and Select N. Virginia Region

To get started, you'll need to log into the AWS console, see [Getting Started](../login.md) for help.

Once there, be sure that you are operating in the **us-east-1** region by selecting **N. Virginia** from the chooser in the upper right hand corner of your AWS Console.

![Select N. Virginia Region](img/region-selection.png)

---

We'll create a SageMaker notebook instance, which we will use to run the other workshop modules as docker is not supported in SageMaker Studio.


#### High-Level Instructions

Use the console or AWS CLI to create an Amazon S3 bucket. Keep in mind that your bucket's name must be globally unique across all regions and customers. We recommend using a name like `smworkshop-firstname-lastname`. If you get an error that your bucket name already exists, try adding additional numbers or characters until you find an unused name.

??? optional-class "Step-by-step instructions to create an S3 bucket (expand for details)"
	1. In the AWS Management Console, choose **Services** then select **S3** under Storage.
	2. Choose **+Create Bucket**
	3. Provide a globally unique name for your bucket such as `smworkshop-firstname-lastname`
	4. Select the Region you've chosen to use for this workshop from the dropdown
	5. Choose **Create** in the lower left of the dialog without selecting a bucket to copy settings from.


<!--
### 2. Use CloudFormation to Set Up a SageMaker Role

1. Click on AWS CloudFormation from the list of all services. This will bring you to the AWS CloudFormation console homepage.

2. Click on **Create new stack**

3. Choose **Specify an Amazon S3 template URL**, paste the following URL and hit **Next**: ```https://ml-materials.s3.amazonaws.com/WorkshopResources/SagemakerRoleCF.template```

4. Name your stack ```AmazonSageMaker-ExecutionRole``` and choose **Next**

5. Leave options as they are and choose **Next**

6. Check the box next to **I acknowledge that AWS CloudFormation might create IAM resources.** and choose **Create**

7. Refresh the page after a few seconds to make sure that the **Status** reads ```CREATE_COMPLETE```

8. Click on the **Outputs** tab and make note of the ARN value that looks like ```arn:aws:iam::XXXX::role/AmazonSageMaker-ExecutionRole-SageMakerLab-XXXX```. You will need this value in the next step.
-->

### 2. Launching the Notebook Instance

1\. In the upper-right corner of the AWS Management Console, confirm you are in the desired AWS region (N. Virginia).

2\. Click on Amazon SageMaker from the list of all services.  This will bring you to the Amazon SageMaker console homepage.

![Services in Console](/img/Picture1.png)

3\. To create a new notebook instance, go to **Notebook instances**, and click the **Create notebook instance** button at the top of the browser window.

![Notebook Instances](/img/Picture2.png)

4\. Type [First Name]-[Last Name]-workshop into the **Notebook instance name** text box, and select ml.m4.xlarge for the **Notebook instance type**.


5\. Click **Create notebook instance**.  This may take several minutes to complete.

![Create Notebook Instance](/img/notebook-instance.png)

6\. For IAM role, choose **Create a new role**. On the **Create an IAM role** screen, select **Any S3 bucket** and click **Create role**.

![Create IAM Role](/img/CreateRole.jpg)



### 3. Accessing the Notebook Instance

1\. Wait for the server status to change to **InService**. This may take a few minutes.

![Access Notebook](/img/jupyterlab-open.png)

2\. Click **Open Jupyterlab**. You will now see the Jupyterlab homepage for your notebook instance. Note that the notebook list will most likely be empty.

!!! Done

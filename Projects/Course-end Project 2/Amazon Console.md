# **Architecting a website using the Serverless Technology.**

### **Course-end Project 2**

**Description:** Use the serverless technology to build up a feedback website.

**Tools required:** AWS Services - S3, DynamoDB, Cognito, IAM 

**Expected Deliverables:**

- Use Auto Scaling to manage the EC2 instances
- Use EC2 instance and capture the metrics in the CloudW

# **Sol:**

I will do it using just 5 major steps: -

1. Create Amazon Cognito User pool and Identity pool (Federated identities).
2. Configure IAM role.
3. Create Amazon DynamoDB Table.
4. Create Amazon S3 Bucket.
5. Upload static Feedback website to the S3 Bucket.

## **Step 1**

**Create Amazon Cognito User pool and Identity pool (Federated identities)**

- Create New Amazon Cognito user pool ![1.png](./images/1.png)

- Select `User name` for sign-in option and click next. ![2.png](./images/2.png)

- Here, selection No MFA and leaving rest of options as default and click next. ![3.png](./images/3.png)

- Leaving everything as default in Step 3 (Configure sign-up experience)

- In the Step 4 (Configure message delivery), Select Send email with Cognito and next. ![4.png](./images/4.png)

- Naming the User pool as `Feedback` and in the `Initial app client > Client secret` select `Don't generate a client secret` and naming app client as `FeedbackAppClient`. ![5.png](./images/5.png)


- Create the user pool. After creating the user pool you'll get the `User pool ID`.  <mark>- Checkpoint 1</mark>
![6.png](./images/6.png)


- In the user pool, go to the App integration, scroll down and you'll get the `Client ID`. <mark>- Checkpoint 2</mark>

</br>

- Now, go to the `Federated identities`.
![7.png](./images/7.png)

- Create new identity pool naming `FeedbackIdentityPool` and use the `User Pool ID
` and `App client id` got in checkpoint 1 and 2.

![8.png](./images/8.png)

- A new role will be created by default named `Cognito_FeedbackIdentityPoolAuth_Role`. click Allow.
![9.png](./images/9.png)

- Here, you'll get your `IdentityPoolId`. <mark>- Checkpoint 3</mark>
![10.png](./images/10.png)


## **Step 2**

**Configure IAM role**



- Go to IAM Roles and search for the role created by default before named `Cognito_FeedbackIdentityPoolAuth_Role `.
![11.png](./images/11.png)

- Add 2 permission (Attach policy) to the role.
  1. `AmazonS3FullAccess`
  2. `AmazonDynamoDBFullAccess`
![12.png](./images/12.png)
- Selecting the launch template created before and click next

## **Step 3**

**Create Amazon DynamoDB Table**

- Go to DynamoDB nad create table.

![13.png](./images/13.png)

- Naming the table as `Feedback` and in Partition key I'm using email as a primary key.

![14.png](./images/14.png)

- Leaving rest of options as default.

## **Step 4**

**Create Amazon S3 Bucket**

- Now, go to the Amazon S3 and **Create bucket**
- Naming as `feedbacksky9262`.
![15.png](./images/15.png)

- In Object Ownership, Select `ACLs enabled`.
![16.png](./images/16.png)

- In Block Public Access settings for this bucket, Unblock two options. Set the permissions as below.
![17.png](./images/17.png)

- Leaving the rest of options as default and create the bucket.

- Now, Open the bucket.
![18.png](./images/18.png)

- Go to Permissions, Scroll down and edit `Cross-origin resource sharing (CORS)`.
![19.png](./images/19.png)

- Paste the below JSON and click “Save”. This will allow cross origin access.

```Json
[
    {
        "AllowedHeaders": [
            "*"
        ],
        "AllowedMethods": [
            "GET",
            "PUT",
            "POST",
            "DELETE"
        ],
        "AllowedOrigins": [
            "*"
        ],
        "ExposeHeaders": []
    }
]
```

- Now, Go to Properties, Scroll down to bottom and edit `Static website hosting`. 
![20.png](./images/20.png)
- Enable the Static website hosting and in Index document type `index.html`.
> Note:- index.html will be our homepage.

![21.png](./images/21.png)

- You'll get the Bucket website endpoint.
![22.png](./images/22.png)


## **Step 5**

**Upload static Feedback website to the S3 bucket**


- Go to this [Github Repo (AWSCognitoFeedbackStaticWeb)](https://github.com/sky9262/AWSCognitoFeedbackStaticWeb) and get the code for the feedback web app. 
> This is an static html page with AWS Javascript SDK included in “script” folder.

<details><summary>Brief explaination of the code</summary>

 * Created 3 pages. 
   * __Home page ([index.html](https://github.com/sky9262/AWSCognitoFeedbackStaticWeb/blob/main/index.html))__: Feedback form
   * __Login page ([login.html](https://github.com/sky9262/AWSCognitoFeedbackStaticWeb/blob/main/login.html))__: Login the user with email id and password.
   * __Signup page ([signup.html](https://github.com/sky9262/AWSCognitoFeedbackStaticWeb/blob/main/signup.html))__: Signup new user.
 * Used `Javascript SDK` to Signup and Login and after the login, getting user creds to submit the form to DynamoDB table.
 * The website's background image will be randome image everytime you visit it.
</details>

- Now, Download the repo and edit the files.

> **Important step**: 
>- Change AWS IDs in the `index.html`, `login.html` and `signup.html` file with the values got in <mark> checkpoint 1, 2 and 3 </mark> and you can also customize the website according to you.
![code.png](./images/code.png)

- Upload the files to the S3 bucket
![23.png](./images/23.png)

- After uploading the files, select all files click on Action button and Make public using ACL.
![24.png](./images/24.png)

#### Now you can access the website and submit a feedback with Serverless Technology.

![25.png](./images/25.png)

**All Done.**


![otsukaresamadesu](./images/82341587.png)

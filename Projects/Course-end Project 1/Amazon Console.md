# **Managing tightly coupled architecture using Amazon SQS**

### **Course-end Project 1**

**Description:** Use AWS SQS to manage a tightly couple architecture.

**Tools required:** AWS Services: SQS, EC2, IAM, and RDS



# **Sol:**

I will do it using just 4 major steps:-

1. Create and Configure Amazon RDS.
2. Create Amazon SQS Queue.
3. Create AIM Role.
4. Create two EC2 Instance.

## **Step 1**

**Create and Configure Amazon RDS**

- Create New Amazon RDS ![1.png](./images/1.png)

- Select `MySQL` . ![2.png](./images/2.png)

- Select `Free tier`. ![3.png](./images/3.png)

- Enter DataBase Instance name, Master username and Master password. ![4.png](./images/4.png)

- Enable Public Access. ![5.png](./images/5.png)


- Select `Password and IAM database authentication`
![6.png](./images/6.png)



- In Additional configuration, enter Initial database name.
![7.png](./images/7.png)

- Now, Create the DataBase.

- Wait for the status `Available` ![8.png](./images/8.png)

- While it's creating the RDS, create a new security group to allow 3306 port from everywhere.
![9.png](./images/9.png)
- Add Inbound rule.
![10.png](./images/10.png)

- Create the security group.

- Now, go to the RDS, modify it and change the vpc security group to the new one created.
![10.1.png](./images/10.1.png)

- Do continue and Apply immediately.

- Step 1 completed.


## **Step 2**

**Create Amazon SQS Queue**



- Go to Amazon SQS and create queue.
![11.png](./images/11.png)

- Enter queue name
![12.png](./images/12.png)
- Leave rest of the options default and create the queue.

- Step 2 completed.


## **Step 3**

**Create AIM Role**

- Now, Open the Amazon AIM and go to Role.

![13.png](./images/13.png)

- Create new Role with use case of EC2.

![14.png](./images/14.png)

- Here, I'm creating only one Role and giving it to both service's permission `AmazonSQSFullAccess` and `AmazonRDSFullAccess`.
> Note: It's good to create separate roles and give only the permissions required (not full).

![14.1.png](./images/14.1.png)

- Enter the Role name and create.

![14.2.png](./images/14.2.png)

- Step 3 completed.

## **Step 4**

**Create two EC2 Instance**

- Now, let's create two ec2. one for the webserver and one for a python application that will look to the sqs queue and if there is any message it'll send to RDS table and delete the message from the sqs queue.


- Create a WebServer EC2.
![15.png](./images/15.png)

- Allow HTTP and HTTPS traffic from the internet.
![16.png](./images/16.png)

- In Advanced details, select the IAM instance profile created in previous step.
![17.png](./images/17.png)

- In User data, add the script below to automatically install webserver and start.
```bash
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
sudo curl https://raw.githubusercontent.com/sky9262/AWS-Developer-Associate/main/Projects/Course-end%20Project%201/Code/WebPage.html >> /var/www/html/index.html
```
> Note:- You need to change the following config:
![code1.png](./images/code1.png)

![18.png](./images/18.png)

- Create one more instance for the python application using the same way created the previous one but change the user-data.
```bash
#!/bin/bash
pip3 install PyMySQL
pip3 install boto3
curl https://raw.githubusercontent.com/sky9262/AWS-Developer-Associate/main/Projects/Course-end%20Project%201/Code/SQS2RDS.py >> SQS2RDS.py
python3 SQS2RDS.py
```
> Note:- You need to change the following config:
![code2.png](./images/code2.png)

![19.png](./images/19.png)


#### Now you can access the website and submit a contact message. It'll send to SQS and the python application take the message and add to the RDS table.

#### If the DataBase is offline the message will still send and when the DataBase will be online all the Messages will be send to RDS table.


**All Done.**


![otsukaresamadesu](./images/82341587.png)

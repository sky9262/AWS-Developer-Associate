# **Managing tightly coupled architecture using Amazon SQS.**

### **Course-end Project 1**

**Description:** Use AWS SQS to manage a tightly couple architecture.

**Tools required:** SQS, EC2, IAM, and RDS

In the traditional way of building applications, the applications directly talk to each other. if an application is down, it impacts the other linked applications, and some data might be compromised. This is called tightly coupled architecture.

 

Applications cannot communicate directly with each other. This can be done through AWS SQS, which makes applications highly available. In the below diagram, the Customer Web Applications interacts with the Backend Applications via SQS Queue. For some reason, if the backend applications are down, the Customer Web Application can continue working with the messages being buffered in the SQS Queue. Once the backend application is up, it can start polling the messages from the SQS Queue and update the database. This way, none of the messages are lost, and applications are loosely coupled and not aware of the status of each other.

#### Solved in two ways:

AWS Console            |  CloudFormation
:-------------------------:|:-------------------------:
[<img src="./images/b1.png">](./Amazon%20Console.md)  |  



## AWS Resources
- SQS
- EC2
- IAM
- RDS

 

## References
- AWS SQS documentation: https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html

- AWS EC2 documentation: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html

- AWS Identity and Access Management documentation: https://docs.aws.amazon.com/iam/index.html

- AWS RDS documentation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html



## WorkFlow

![Template Diagram](./images/template1-designer.png)



## Authors

- [@sky9262](https://www.github.com/sky9262)


## 🔗 Connect with me
[![blog](https://img.shields.io/badge/blog-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://sky9262.tistory.com/)

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sky9262/)

[![github](https://img.shields.io/badge/Instagram-ffffff?style=for-the-badge&logo=instagram&logoColor=dd2a7b)](https://www.instagram.com/sky926296/)

[![github](https://img.shields.io/badge/github-000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sky9262/)
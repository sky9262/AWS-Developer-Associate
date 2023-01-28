# AnimeWebCloudFormation with VPC
Instructions:
- Create a VPC and two subnets public and private. 
- Deploy to WebServer and use Elastic Load Balancer to distribute traffic 
## Mentor

**Ritesh Behal**

## AWS Resources
* VPC
  * ElasticLoadBalancingV2::LoadBalancer
    * TargetGroup
    * Listener
    * SecurityGroup
  * Route
  * RouteTable
  * SubnetRouteTableAssociation
  * Public Subnet
    * EC2
      * Volume
    * EC2
    * SecurityGroup
    * KeyPair
  * Private Subnet

* InternetGateway
* VPCGatewayAttachment
## References
- [Webserver GitHub Repository](https://github.com/falselunatic/Anime)
- AWS CloudFormation documentation: https://aws.amazon.com/cloudformation/

- AWS CloudFormation templates documentation: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-reference.html


## Diagram

![Template Diagram](./images/template1-designer.png)


## Authors

- [@sky9262](https://www.github.com/sky9262)


## 🔗 Connect with me
[![blog](https://img.shields.io/badge/blog-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://sky9262.tistory.com/)

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sky9262/)

[![github](https://img.shields.io/badge/Instagram-ffffff?style=for-the-badge&logo=instagram&logoColor=dd2a7b)](https://www.instagram.com/sky926296/)

[![github](https://img.shields.io/badge/github-000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sky9262/)
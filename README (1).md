## Testing the standalone OpenSearch Dashboard in ECS & in local hosted docker container with multiple users | FGAC enabled domains

1. Creation of a new OpenSearch domain - OS_1.3
```
domain arn : arn:aws:es:ap-south-1:765423874566:domain/success-test-1
Domain endpoint : https://vpc-success-test-2-ce6hkjt5ghggqczkbka4xsxc6a.ap-south-1.es.amazonaws.com
OSD endpoint : https://vpc-success-test-2-ce6hkjt5ghggqczkbka4xsxc6a.ap-south-1.es.amazonaws.com/_dashboards
```
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/main/READMEIMG/1.png)

2. Login to the OpenSearch Dashboard with master user and password

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/2.png)

3. Creation of internal users and mapping users to the roles

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/3.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/4.png)

4. Creation of Dashboards on all user account on the private tenant

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/5.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/6.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/7.png)

5. Creation of ECS Cluster with task and service and connecting the OSD to OpenSearch Cluster
```
ECS Endpoint : 13.127.112.161
```

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/8.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/9.png)

6. Access all the users and their dashboards through ECS Fargate endpoint

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/10.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/11.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/12.png)

7. Spin up a docker OSD in an EC2 Instance and connect to the OpenSearch cluster
```
EC2 Endpoint : 65.2.130.32
```

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/13.png)

8. Accessing users and their dashboards through EC2 linux endpoint

![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/14.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/15.png)
![](https://gitlab.aws.dev/mkbn/standalone-osd-to-the-rescue/-/raw/306f672b83b192c0356b4440ca4aadda09ec9f60/READMEIMG/16.png)


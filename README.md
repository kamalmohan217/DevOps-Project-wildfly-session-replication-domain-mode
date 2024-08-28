# DevOps-Project-wildfly-session-replication-domain-mode
![image](https://github.com/user-attachments/assets/8de01d24-5e6d-4400-a184-ae1cd486fae0)

Using terraform script present in this repository I have created the infrastructure of EC2 Instances, S3 bucket, NLB and RDS. Ansible has been used as a configuration management tool. Before running the terraform script make sure Ansible is installed on your Terraform-Server. In this project I have used Wildfly-11 JBoss Application Server and MySQL 5.7 RDS. For Wildfly domain discovery S3 bucket has been used and MySQL database as a central point for cluster configuration.

After successfully creation of the infrastructure we will test MySQL database connection with slave-1 and slave-2 as shown in the screenshot below.

![image](https://github.com/user-attachments/assets/ad6f633b-b5b6-49fa-b0c9-60f215f10384)
![image](https://github.com/user-attachments/assets/305591d5-9551-474e-b940-63a4f2dd146e)

After we will ensure everything is fine go fo the deployment of war file as shown in the screenshot below.

![image](https://github.com/user-attachments/assets/e0e214fd-6cc1-4136-a81e-4733799666c9)
![image](https://github.com/user-attachments/assets/763f2038-a537-4453-8d7a-10e8176ef037)
![image](https://github.com/user-attachments/assets/6ca01e79-7951-4310-82be-a22106ca4e4a)
![image](https://github.com/user-attachments/assets/63bf8e43-71c9-4d0c-bfe3-cd0ebf135924)
![image](https://github.com/user-attachments/assets/7de950d4-a526-4904-98dd-ee3ca239cc76)
![image](https://github.com/user-attachments/assets/e2bef2e3-d0a6-45f5-a3e4-5a1b79d52d80)

After successfull deployment of war file to wildfly domain mode cluster do the entry of NLB DNS name into the Route53 hosted zone and create the record set as shown in the screenshot below.

![image](https://github.com/user-attachments/assets/8b3e7809-3dc6-40cb-8118-0880848eb578)

Access the Application's URL and open the web developer's tool and check the session Id. In web developer's tool if JSESSIONID ends with slave name as slave-1 then next time for the testing purpose stop slave-1 and refresh the page you will find JESSIONID value with same session id but different slave name as slave-2 and page count will be increased.

![image](https://github.com/user-attachments/assets/1ab3c993-a0e0-44d5-9da1-e4d96d0cef42)
![image](https://github.com/user-attachments/assets/8c590ab4-1335-4862-acfb-d610ef7c275d)

Finally check the entry of the database jgroups and table as shown in the screenshot below.

![image](https://github.com/user-attachments/assets/f8a5decf-3272-4708-b6aa-954fbe368447)

<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
References:-       https://octopus.com/blog/wildfly-s3-domain-discovery
                   https://octopus.com/blog/wildfly-jdbc-ping
```

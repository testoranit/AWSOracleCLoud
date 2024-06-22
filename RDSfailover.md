
install apache2
install mysql-client
toot


add-apt-repository -y ppa:ondrej/php
apt install php5.6 php5.6-mysqli -y
cp index.php to /var/www/html/
create rds db

take rds endpoint and confiure details in index.php
create table in data in my sql db.
insert records.

create ami of the ec2
create LC
creats ASG
create new lbroute 53
insert records
do failover


https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/multi-az-db-clusters-concepts.html#multi-az-db-clusters-concepts-failover

*************
RDS db instance class

The DBInstanceClass parameter specifies the compute and memory capacity of the Amazon RDS instance. It determines the hardware specifications of the RDS instance, including the amount of CPU, memory, and network throughput available. AWS provides a variety of instance classes tailored for different use cases and workloads.

Instance classes are categorized into several families, each optimized for different purposes, such as general-purpose, memory-optimized, or burstable performance. Below are some commonly used instance classes:

General Purpose (e.g., db.t3, db.m5)

db.t3.micro, db.t3.small, db.t3.medium, etc.: These are burstable performance instances suitable for workloads that have moderate CPU requirements and can benefit from burstable performance.
db.m5.large, db.m5.xlarge, db.m5.2xlarge, etc.: These instances offer a balance of compute, memory, and network resources and are suitable for a wide range of database workloads.
Memory Optimized (e.g., db.r5)

db.r5.large, db.r5.xlarge, db.r5.2xlarge, etc.: These instances are optimized for memory-intensive applications and offer higher memory-to-CPU ratios.
Burstable Performance (e.g., db.t2, db.t3)

db.t2.micro, db.t2.small, db.t2.medium, etc.: These are also burstable performance instances similar to the t3 series, suitable for workloads that don't require sustained high CPU performance.
Compute Optimized (e.g., db.c5)

db.c5.large, db.c5.xlarge, db.c5.2xlarge, etc.: These instances are optimized for compute-intensive applications

****RDS
RPO:- how much data loss u can withstand.
RTO:- time tken to recover the db.

When you scale up a Multi-AZ DB instance in Amazon RDS, the process is designed to be as seamless as possible. Here's how it works:

Upgrade Standby: The upgrade first occurs on the standby instance.
Failover: After the standby instance is upgraded, a failover happens, making the upgraded standby instance the new primary.
Upgrade New Standby: The old primary instance, now the standby, is then upgraded.
Application Endpoint
One of the significant advantages of Amazon RDS is that it abstracts the failover process and manages it automatically. This means:

RDS Endpoint: Your application connects to a single endpoint provided by RDS. This endpoint remains the same before, during, and after the failover.
No Endpoint Change Required: Since the RDS service handles the failover, your application's connection endpoint does not change. The endpoint will automatically point to the new primary instance after the failover.
After Scaling Up
New Primary: After the failover, the previously standby instance becomes the new primary instance.
New Standby: The old primary, now the standby, is upgraded to the new instance class.

***storage

Summary of Downtime Expectations
Scaling Storage Size: No downtime.
Changing Storage Type: Potential downtime, especially noticeable for single-AZ deployments.
Multi-AZ Deployments: Downtime is minimized but not entirely eliminated; there is typically a brief period during failover.


Patching also happens similar to changing db instance class.
after patching monitor the db performance.
check app is working fine with the new patch.



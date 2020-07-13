# Notes for the AWS Cloud Practitioner Exam 2020

## 1. Introduction
**AWS Cloud**: on demand delivery of IT through the internet
**Global infrastructure** -> Region, Availability Zones, Edge Locations (end points for AWS - cache contents)

AWS Interfaces (references the AWS API):
- AWS Management Console - graphical
- CLI - programming language agnostic
- SDKs - in existing apps (Infrastructure as code)

**IAM** - Identity Access Management

3 types of cloud deployment:
- Public
- Hybrid
- Private (on prem)

Cloud computing models:
- IaaS (EC2)
- PaaS (Elastic Beanstalk)
- Saas

Cloud: low cost, low risk
1. Reduce risk - agile
2. Scalability - resize resources
3. Agility - speed, experimentation, innovation
4. Elasticity - scale up or down - autoscaling, Elastic Load Balancing
5. Reliability - AWS regions - availability zones with data centers, Fault tolerance - system still runs if something fails
6. Security - continual monitoring, staffed 24/7, multi factor authorization, multi region

## 2. AWS Core Services
**EC2** - Elastic Compute Cloud
Instances - pay as you go, broad selection of hardware/software (server, virtual machine), global hosting 

Instance types:
- On Demand - no contract - more $
- Reserved - contract
- Spot - bid the price you want to pay, apps with flexible start and stop times
- Dedicated Hosts - physical EC2, can be on demand or reserved

Deploy to one specific region and availability zone

AMI - Amazon Machine Image - the OS and software

**EBS** - Elastic Block Store - additional storage for EC2
- HDD and SDD
- Snapshots - recreate a new volume
- Encryption
- Elasticity - HDD <--> SDD, inc/dec volume size
- On the same availability zone and region as the EC2 instance

**S3** - Simple Storage Service
- Managed cloud storage service
- Store virtually number of objects
- Access anytime from anywhere
- Rich security controls
- Must be unique names
  
Create bucket, key in object

IAM policies (allow or deny users)
S3 bucket policies (allow or deny bucket)
Per object access - access control list

***Use cases***
- Store app assets
- Static webhosting
- Backup and disaster recovery
- Staging for big data

***Access Tiers***
- Regular (standard)
- IA (infrequently accessed)
- Glacier (archival)
- Intelligent Tiering - 2 tiers (frequent and infrequent)

**AWS Global Infrastructure**
- Regions - 2 or more availability zones, separate regions
- Availability Zones (AZ) - collection of data centers, physically and logically separate, protected from failures
- Edge Locations -  CDN (Amazon CloudFront)

**Virtual Private Cloud (VPC)**
- Networking AWS Service
- Lives in a region
- Subnets (span to AZs)
- Route tables
- Internet Gateway
- NAT Gateway
- NACL - Network Access Control List

## 3. Integrated Services
Application Load Balancer
- Classic load balancer
- **Elastic load balancer** - configure routing to applications (listeners, target, target group)
Use containers to host microservices 
Features:
- Support protocols
- CloudWatch metrics
- Access logs
- Health checks
- Path and host-based routing
- IPv6 support
- Dynamic Ports

**Autoscaling** - ensure you have the correct number of EC2 instances, adjust capacity as needed
Scalability and automation
  1 Launch configuration (what) --> 2 Autoscaling group (where) --> 3 Autoscaling policy (when)

  Dynamic autoscaling: Elastic Load Balancing --> CloudWatch --> Autoscaling

**Route 53** (DNS service) - translate a URL to an IP address
- Hosted zone
- Record Set - subdomain creation
- DNS resolution strategies
  Simple Routing, Geo-location, Failover
  Weighted round robin, latency-based, multivalue answer

**Relational Database Service** (RDS)
- DB instance class and storage
- private subnet (AZ)
- Web applications, e-commerce, mobile and online games

**Lambda** - compute service
- Event-driven serverless compute
- pay when code is run
- Use cases: Automatic backup, event, IOT, serverless websites

**Elastic Beanstalk**
- PaaS
- Allows quick deployment of apps
- Reduce management complexity
  Just need to have the application code then everything is done for you
  Choose instance type, db, autoscaling
  Provides: code, app service, http service, OS, language interpreter, host

**Simple Notification Service** (SNS)
- pub/sub messaging and mobile communication service

**CloudWatch** - monitoring service in real time
- CPU, disk I/O, set alarms, automatically react to changes
Metrics
- Alarms - watches a single metric, performs one or more actions
- Events - describe changes in AWS resources
- Logs - in real time - cloud trail logged events
- Dashboard

**CloudFront** (CDN) - edge locations

**Cloud Formation** - simplify repeated tasks
- Create, update, delete stacks (environment)

## 4. Architecture
Well-architected framework

**5 Design/Pillar principles**
1. Security: IAM, detective controls, infrastructure protection, data protection, incident response
2. Reliability: Recover from issues/failures
3. Performance efficiency: select, review, monitor, trade-offs
4. Cost optimization: cost-effective resources, match supply and demand, increase expenditure awareness, optimize overtime
5. Operational excellence: manage/automate change

Fault tolerance - ability to remain operational in case of failure

Simple queue service: messaging system
Simple storage service (S3): data storage
RDS relational database service 

High availability

Elastic load balancers - distribute incoming traffic

IP address
Route 53 - DNS service (translate domain names to IP addresses)
Autoscaling - adjust/modify resources with changes in demand
CloudWatch - statistic gathering system, used with autoscaling 

## 5. Security
**AWS Cloud HSM** - hardware based encryption

**Shared Responsibility Model**
You:
- User data
- Application
- Guest OS
- EC2

AWS:
- Hypervisor
- Network - VPC
- Physical

**Identity and Access Management** (Authentication/Authorization)
  Policy Docs (permissions)
  --> Role (temporary)
  --> User (permanent)
  --> Group

**Amazon Inspector(**) - security assessment service, produces report, identifies security vulnerabilities

**AWS Shield**:
- Managed DDoS (Distributed Denial of Service - multiple source, make your app unavailable to users) protection service

  Standard - free
  Advanced - 24/7 access to DDoS response team (DRT)

## 6. Pricing and Support
Reserve instances:
- AURI - All up front (largest discount)
- PURI - Less up front (more discount)
- NURI - no up front

Consolidated billing for multiple accounts
- Pay for: compute, storage, outbound data transfer
- No charge: Inbound data transfer or AWS services on same region

On demand, reserved, spot (bid)

EC2 - charge only for capacity used (clock-second/hour billing)

S3 - standard storage, standard infrequent access (number and size, type, get requests) - no charge for autoscaling

EBS - General purpose SSD - included in price, others cost money (ie snapshots)

RDS - clock-hour billing, db characteristics, db purchase type - no charge for backup storage

CloudFront - price based on request, data transfer out, varies by region

**Trusted Advisor** - checks cost optimization, performance, security, fault tolerance

Support
- Proactive guidance - technical account manager (TAM)
- Best practices - trusted advisor
- Account assistance - AWS support concierge - billing and account

Support plans:
- Basic
- Developer
- Business
- Enterprise

**AWS Cost Explorer** - custom reports analyze usage and costs
**Total cost of ownership** (TCO) - shows how much it costs to move to AWS instead of on-prem
**AWS organizations** - automate account creation, groups of accounts, policies 

## Useful Links:
https://digitalcloud.training/certification-training/aws-certified-cloud-practitioner/
https://github.com/yafeunteun/aws-cloud-practitioner-certification-notes 
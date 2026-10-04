# AWS Fluency Roadmap - GenAI / ML Engineer

## Goal

Become fluent in AWS as a **GenAI / ML Engineer**, with the ability to:

* Deploy production applications on AWS
* Design scalable cloud architectures
* Build and deploy GenAI/RAG systems
* Understand networking and security
* Work with containers and serverless services
* Debug production issues
* Monitor and optimize applications
* Explain AWS architecture confidently in interviews

> **Target:** Don't memorize AWS services. Learn to solve production problems using AWS.

---

# 8-Week AWS Learning Plan

## Week 1 - AWS Foundations + IAM

### Services

* IAM
* AWS Organizations - basic understanding
* AWS STS
* AWS CLI
* AWS Console

### Learn

#### IAM

* Users
* Groups
* Roles
* Policies
* Identity-based policies
* Resource-based policies
* Least privilege
* Role assumption
* Access keys
* Temporary credentials
* IAM + applications
* IAM roles for EC2/ECS/Lambda

#### AWS CLI

* Configure CLI
* Profiles
* Basic AWS commands
* Working with S3 through CLI

### Hands-on

* Create an IAM role
* Create a least-privilege policy
* Assume a role
* Configure AWS CLI
* Upload/download files using CLI
* Deploy a simple resource using AWS CLI

### Goal

Be able to answer:

> How does an application securely access AWS services without storing AWS access keys in the source code?

---

# Week 2 - S3 + EC2

## S3

### Learn

* Buckets
* Objects
* Prefixes
* Storage classes
* Versioning
* Lifecycle policies
* Encryption
* Bucket policies
* Access control
* Presigned URLs
* Multipart uploads
* S3 events
* Static website hosting - basic understanding

### EC2

### Learn

* AMIs
* Instance types
* CPU / memory
* EBS
* Security groups
* Key pairs
* SSH
* User data
* Elastic IP
* Auto Scaling - basic understanding
* Instance lifecycle

### Hands-on

Deploy a FastAPI application on EC2.

```text
Internet
   ↓
EC2
   ↓
FastAPI
```

Store application files/data in S3.

### Goal

Be able to deploy and operate a basic application on EC2.

---

# Week 3 - VPC + Networking

This is a **high-priority topic**.

## Learn

### VPC

* CIDR
* Subnets
* Public subnet
* Private subnet
* Route tables
* Internet Gateway
* NAT Gateway
* Security Groups
* Network ACLs
* DNS
* Elastic IP
* VPC endpoints
* Availability Zones
* Regions

### Understand

```text
                    AWS Region
                        │
                       VPC
                        │
          ┌─────────────┴─────────────┐
          │                           │
     Public Subnet               Private Subnet
          │                           │
    Load Balancer                 Application
          │                           │
    Internet Gateway             Database
                                      │
                                 NAT Gateway
                                      │
                                  Internet
```

### Hands-on

Create:

* VPC
* Public subnet
* Private subnet
* Route tables
* Internet Gateway
* NAT Gateway
* Security Groups

Deploy an application into a private subnet.

### Goal

Be able to explain:

> Why can't an EC2 instance in a private subnet directly receive traffic from the internet?

And:

> How does a private application access the internet?

---

# Week 4 - Docker + ECR + ECS/Fargate

## Docker

You should already know Docker, but strengthen:

* Images
* Containers
* Dockerfile
* Volumes
* Networks
* Environment variables
* Multi-stage builds

## ECR

Learn:

* Repositories
* Image tags
* Push/pull images
* Image lifecycle

## ECS

Learn:

* Cluster
* Task
* Task Definition
* Service
* Container
* Fargate
* CPU/memory
* Environment variables
* Secrets
* Health checks
* Service discovery
* Autoscaling
* Rolling deployments

## Application Load Balancer

Learn:

* Listener
* Target group
* Health checks
* HTTP/HTTPS
* Routing

### Hands-on

Deploy:

```text
GitHub
   ↓
Docker
   ↓
ECR
   ↓
ECS/Fargate
   ↓
ALB
   ↓
FastAPI
```

### Goal

Be able to deploy a production-style containerized FastAPI application.

---

# Week 5 - Databases + Messaging

## RDS

Learn:

* PostgreSQL
* MySQL - basic understanding
* DB instances
* Subnet groups
* Security groups
* Backups
* Read replicas
* Multi-AZ
* Encryption

## DynamoDB

Learn:

* Tables
* Items
* Partition keys
* Sort keys
* GSI
* LSI
* Query vs Scan
* Capacity
* TTL

## ElastiCache

Learn:

* Redis
* Caching
* Session storage
* Rate limiting
* Frequently accessed data

## SQS

Learn:

* Queue
* Producer
* Consumer
* Visibility timeout
* Dead-letter queue
* Long polling
* Standard vs FIFO

## SNS

Learn:

* Topics
* Publishers
* Subscribers
* Fan-out

### Hands-on

Build:

```text
FastAPI
   ↓
SQS
   ↓
Worker
   ↓
PostgreSQL
```

Add a Dead Letter Queue.

### Goal

Understand asynchronous and distributed application architecture.

---

# Week 6 - Lambda + EventBridge + Step Functions + CloudWatch

## Lambda

Learn:

* Functions
* Runtime
* Event
* Execution role
* Timeout
* Memory
* Layers
* Environment variables
* Concurrency
* Cold starts
* Provisioned concurrency

## EventBridge

Learn:

* Events
* Event bus
* Rules
* Event patterns
* Targets
* Scheduled events

## Step Functions

Learn:

* State machines
* Tasks
* Choice
* Parallel
* Retry
* Catch
* Workflow orchestration

## CloudWatch

Learn:

* Logs
* Metrics
* Alarms
* Dashboards
* Log groups
* Log Insights

### Hands-on

Build:

```text
S3 Upload
    ↓
EventBridge
    ↓
SQS
    ↓
Lambda / ECS Worker
    ↓
Processing
    ↓
CloudWatch
```

### Goal

Understand event-driven and asynchronous AWS architecture.

---

# Week 7 - Amazon Bedrock + GenAI

## Amazon Bedrock

This is a **high-priority topic for GenAI roles**.

### Learn

* Foundation models
* Model IDs
* Model invocation
* Converse API
* Streaming
* Prompting
* Tool use
* Function calling
* Guardrails
* Model evaluation
* Agents
* Knowledge Bases
* Prompt management
* Provisioned throughput
* Cost considerations

### Build

```text
User
  ↓
API
  ↓
Bedrock
  ↓
LLM
  ↓
Response
```

Then extend:

```text
User
  ↓
API
  ↓
Agent
  ├── Bedrock
  ├── Database
  ├── External API
  └── Tools
```

### Goal

Be able to build a production-oriented LLM application using Bedrock.

---

# Week 8 - AWS RAG + Production Architecture

## RAG

Learn:

* S3 document ingestion
* Chunking
* Embeddings
* Vector search
* Metadata filtering
* Hybrid search
* Reranking
* Retrieval evaluation
* Context quality
* Hallucination reduction

## AWS Options

Understand:

### Option 1

**Bedrock Knowledge Bases**

### Option 2

**Amazon OpenSearch / OpenSearch Serverless**

### Option 3

**Aurora PostgreSQL + pgvector**

### Option 4

Deploy your own vector database on AWS.

---

# Capstone Project

## Production Resume / Candidate Matching RAG System

Build a production-style version of a system you already understand.

### Architecture

```text
                         Users
                           │
                           ↓
                    CloudFront / WAF
                           │
                           ↓
                    API Gateway / ALB
                           │
                           ↓
                     ECS / Fargate
                           │
          ┌────────────────┼────────────────┐
          │                │                │
          ↓                ↓                ↓
         S3               SQS            Bedrock
     Resumes/JDs          Queue          LLM/Agent
          │                │                │
          ↓                ↓                │
     EventBridge       Workers             │
                           │                │
                           ↓                │
                    Document Processing     │
                           │                │
                           ↓                │
                    Vector Database         │
                           │                │
                           └───────┬────────┘
                                   ↓
                              Reranking
                                   │
                                   ↓
                              Match Score
                                   │
                                   ↓
                                API
```

---

# Security Layer

Learn and implement:

* IAM
* IAM Roles
* Least privilege
* KMS
* Secrets Manager
* Parameter Store
* Security Groups
* Private subnets
* VPC endpoints
* Encryption at rest
* Encryption in transit
* CloudTrail
* WAF

Your application should **never** contain hardcoded:

```text
AWS_ACCESS_KEY
AWS_SECRET_ACCESS_KEY
DATABASE_PASSWORD
API_KEYS
```

---

# Monitoring Layer

Implement:

```text
Application
    ↓
CloudWatch Logs
    ↓
CloudWatch Metrics
    ↓
CloudWatch Alarms
    ↓
SNS
    ↓
Notification
```

Monitor:

* CPU
* Memory
* Request count
* Latency
* Error rate
* Container restarts
* Queue depth
* Lambda errors
* Database connections
* LLM latency
* LLM token usage
* AWS costs

---

# CI/CD

Learn:

* GitHub Actions
* ECR
* ECS deployment
* Environment management
* Automated testing
* Docker builds
* Rolling deployments

Target:

```text
Git Push
   ↓
GitHub Actions
   ↓
Tests
   ↓
Docker Build
   ↓
ECR
   ↓
ECS Deployment
   ↓
Health Check
   ↓
Production
```

---

# AWS Services Priority

## 🔴 Must Master

* IAM
* VPC
* S3
* EC2
* ECS
* Fargate
* ECR
* ALB
* Lambda
* SQS
* CloudWatch
* RDS
* Bedrock
* OpenSearch
* Secrets Manager
* KMS

## 🟠 Strong Understanding

* API Gateway
* EventBridge
* SNS
* Step Functions
* DynamoDB
* ElastiCache
* CloudFront
* WAF
* CloudTrail
* Route 53
* VPC Endpoints

## 🟡 Basic Understanding Initially

* EKS
* Aurora
* Glue
* Athena
* EMR
* Kinesis
* Redshift
* SageMaker
* Batch
* CodePipeline
* CodeBuild

Don't try to master every AWS service.

---

# Architecture Problems to Practice

For each problem, design the AWS architecture before looking at the solution.

## Problem 1

Deploy a FastAPI application.

Think:

```text
EC2 vs ECS vs Lambda?
```

---

## Problem 2

Store millions of PDFs.

Think:

```text
S3
```

Why not EBS?

---

## Problem 3

Process uploaded PDFs asynchronously.

Think:

```text
S3
 ↓
EventBridge
 ↓
SQS
 ↓
Worker
```

---

## Problem 4

Run a FastAPI application privately.

Think:

```text
ALB
 ↓
Private ECS
```

---

## Problem 5

Build a GenAI chatbot.

Think:

```text
API
 ↓
Bedrock
```

---

## Problem 6

Build a RAG application.

Think:

```text
S3
 ↓
Embedding
 ↓
Vector DB
 ↓
Retrieval
 ↓
Bedrock
```

---

## Problem 7

Process 1 million documents.

Think:

```text
S3
 ↓
SQS
 ↓
Workers
 ↓
Autoscaling
```

---

## Problem 8

Secure database credentials.

Think:

```text
Secrets Manager
```

---

## Problem 9

Application needs access to S3 without credentials.

Think:

```text
IAM Role
```

---

## Problem 10

Application is receiving too much traffic.

Think:

```text
ALB
 ↓
ECS
 ↓
Autoscaling
```

---

# Interview-Level Questions

You should eventually be able to answer these without looking them up.

### IAM

* User vs Role?
* Role vs Policy?
* Identity-based vs Resource-based policy?
* How does EC2 access S3 securely?

### S3

* Why S3 instead of EBS?
* What is S3 versioning?
* What is a presigned URL?
* How do you secure an S3 bucket?

### EC2

* EC2 vs ECS?
* What is an AMI?
* What is EBS?
* Security Group vs NACL?

### VPC

* Public vs private subnet?
* Internet Gateway vs NAT Gateway?
* Security Group vs NACL?
* How does a private subnet access the internet?
* What is a VPC endpoint?

### ECS

* Task vs Service?
* ECS vs Fargate?
* How does ECS autoscale?
* How does ALB route traffic to ECS?

### Lambda

* What causes cold starts?
* Lambda vs ECS?
* Lambda concurrency?
* When should you NOT use Lambda?

### SQS

* Why use SQS?
* Visibility timeout?
* Dead Letter Queue?
* Standard vs FIFO?

### Databases

* RDS vs DynamoDB?
* SQL vs NoSQL?
* When would you use Redis?

### Bedrock

* Why Bedrock?
* Bedrock vs hosting your own model?
* Knowledge Bases?
* Bedrock Agents?
* Guardrails?
* How would you control LLM costs?

### Architecture

* How would you design a highly available GenAI application?
* How would you handle 10K concurrent users?
* How would you process 1M documents?
* How would you secure the architecture?
* How would you monitor it?
* How would you reduce AWS costs?

---

# Learning Method

For every AWS service:

## 1. Understand the problem

What problem does this service solve?

## 2. Understand the architecture

Where does it fit?

## 3. Build something

Don't just watch tutorials.

## 4. Break it

Intentionally cause:

* Permission errors
* Network errors
* Timeouts
* Invalid credentials
* Container failures
* Database connection failures

## 5. Debug it

Use:

* CloudWatch
* AWS Console
* CLI
* Logs
* Metrics
* IAM policy analysis

## 6. Explain it

Explain the service without documentation.

---

# Weekly Routine

Target:

**2–3 hours/day, 6 days/week**

### Day 1

Learn concepts.

### Day 2

AWS documentation + architecture.

### Day 3

Hands-on implementation.

### Day 4

Build something without tutorial.

### Day 5

Break + debug it.

### Day 6

Architecture + interview questions.

### Day 7

Rest / revision.

---

# Final Target

At the end of this roadmap, I should be able to receive a requirement like:

> "Build a production GenAI application on AWS that supports RAG, asynchronous document processing, authentication, autoscaling, monitoring, security and high availability."

And independently design:

```text
                    CloudFront
                        │
                       WAF
                        │
                 API Gateway / ALB
                        │
                  ECS / Fargate
                        │
       ┌────────────────┼────────────────┐
       │                │                │
      S3               SQS            Bedrock
       │                │                │
 EventBridge        Workers         Knowledge Base
       │                │                │
       └────────────┬───┘                │
                    ↓                    │
              Vector Search ────────────┘
                    │
                    ↓
               Reranking
                    │
                    ↓
                FastAPI
                    │
                    ↓
               Application

        ┌─────────────────────────┐
        │ Security & Operations   │
        │                         │
        │ IAM                     │
        │ KMS                     │
        │ Secrets Manager         │
        │ CloudWatch              │
        │ CloudTrail              │
        │ VPC                     │
        │ Autoscaling             │
        └─────────────────────────┘
```

## Definition of AWS Fluency

I am **AWS fluent** when I can:

* [ ] Choose the right AWS service for a problem
* [ ] Deploy applications without following a tutorial
* [ ] Design VPC/network architecture
* [ ] Configure IAM securely
* [ ] Deploy Docker applications using ECS/Fargate
* [ ] Build event-driven systems
* [ ] Work with S3, RDS, DynamoDB and SQS
* [ ] Build GenAI applications with Bedrock
* [ ] Build production RAG on AWS
* [ ] Monitor and debug production systems
* [ ] Secure secrets and credentials
* [ ] Explain scalability and high availability
* [ ] Estimate major cost drivers
* [ ] Design AWS architectures in interviews
* [ ] Troubleshoot AWS failures independently

> **Main principle:** Build first. Break things. Debug them. Then learn the theory behind what you built.





# Concrete Weekly Deliverables

The rule for this roadmap:

> **Every week must produce something working.**
>
> No week is complete just because you watched courses or read documentation.

---

# Week 1 Deliverables - IAM + AWS CLI

## Build

Create an AWS account/project structure and configure secure access.

### Deliverable 1 - IAM Setup

Create:

* [ ] IAM role for application access
* [ ] Least-privilege policy for S3
* [ ] IAM role that can be assumed
* [ ] Separate development permissions from production permissions

### Deliverable 2 - AWS CLI

Be able to run:

```bash
aws sts get-caller-identity
aws s3 ls
aws s3 mb s3://<bucket>
aws s3 cp <file> s3://<bucket>/
aws s3 cp s3://<bucket>/<file> .
```

### Deliverable 3 - Security Notes

Create:

```text
docs/week-01-iam.md
```

Document:

* IAM User vs Role
* IAM Policy
* Role assumption
* Least privilege
* Why access keys should not be hardcoded
* How EC2/ECS/Lambda can access AWS services

### Definition of Done

* [ ] I can configure AWS CLI without guessing
* [ ] I understand IAM roles
* [ ] I can write a basic IAM policy
* [ ] I can explain temporary credentials
* [ ] I can explain how an application accesses S3 securely

---

# Week 2 Deliverables - S3 + EC2

## Build

Deploy a FastAPI application on EC2.

### Deliverable 1 - FastAPI Application

Create:

```text
aws-fluency/
├── app/
│   └── main.py
├── Dockerfile
├── requirements.txt
└── README.md
```

Endpoints:

```text
GET /health
GET /hello
```

### Deliverable 2 - EC2 Deployment

Deploy the application to EC2.

You should be able to:

```text
Internet
   ↓
EC2
   ↓
FastAPI
```

### Deliverable 3 - S3 Integration

Implement:

```text
POST /upload
GET /files
```

Files should be stored in S3.

### Deliverable 4 - Presigned URL

Create an endpoint that generates a temporary download URL.

### Deliverable 5 - Documentation

Create:

```text
docs/week-02-s3-ec2.md
```

Document:

* EC2 architecture
* S3 architecture
* Security Group configuration
* IAM role
* S3 bucket policy
* Why S3 is better than storing files on EC2

### Definition of Done

* [ ] FastAPI runs on EC2
* [ ] API can upload to S3
* [ ] API can retrieve files from S3
* [ ] Presigned URLs work
* [ ] No AWS credentials are hardcoded

---

# Week 3 Deliverables - VPC + Networking

## Build

Create a proper VPC architecture.

```text
                    VPC
                     │
        ┌────────────┴────────────┐
        │                         │
 Public Subnet              Private Subnet
        │                         │
       ALB                    Application
        │                         │
 Internet Gateway            NAT Gateway
```

### Deliverable 1 - VPC

Create:

* [ ] VPC
* [ ] Public subnet
* [ ] Private subnet
* [ ] Internet Gateway
* [ ] NAT Gateway
* [ ] Route tables
* [ ] Security Groups

### Deliverable 2 - Architecture Diagram

Create:

```text
docs/week-03-vpc.png
```

Show:

```text
Internet
   ↓
Internet Gateway
   ↓
Public Subnet
   ↓
Load Balancer
   ↓
Private Subnet
   ↓
Application
```

### Deliverable 3 - Network Debugging

Intentionally break:

* Security Group
* Route table
* Internet access

Then fix them.

Document the debugging process:

```text
docs/week-03-network-debugging.md
```

### Definition of Done

You should be able to explain:

* [ ] Public vs private subnet
* [ ] Internet Gateway
* [ ] NAT Gateway
* [ ] Route table
* [ ] Security Group
* [ ] NACL
* [ ] Why a private subnet cannot directly receive internet traffic

---

# Week 4 Deliverables - Docker + ECR + ECS/Fargate

## Build

Move your FastAPI application from EC2 to ECS/Fargate.

### Deliverable 1 - Docker

Create a production Dockerfile.

Requirements:

* [ ] Small base image
* [ ] Non-root user
* [ ] Environment variables
* [ ] Health check
* [ ] Multi-stage build if useful

### Deliverable 2 - ECR

Create an ECR repository.

Push:

```text
fastapi-app:latest
```

### Deliverable 3 - ECS

Create:

* [ ] ECS cluster
* [ ] Task definition
* [ ] ECS service
* [ ] Fargate task
* [ ] CloudWatch logging

### Deliverable 4 - ALB

Configure:

```text
Internet
   ↓
ALB
   ↓
ECS/Fargate
   ↓
FastAPI
```

Implement:

```text
GET /health
```

as the ALB health check.

### Deliverable 5 - Autoscaling

Configure basic ECS autoscaling.

### Definition of Done

* [ ] Docker image builds
* [ ] Image is pushed to ECR
* [ ] ECS runs the container
* [ ] ALB routes traffic
* [ ] Health checks work
* [ ] Logs appear in CloudWatch
* [ ] Application can scale

---

# Week 5 Deliverables - RDS + DynamoDB + SQS

## Build

Create an asynchronous backend.

```text
FastAPI
   ↓
SQS
   ↓
Worker
   ↓
PostgreSQL
```

### Deliverable 1 - RDS

Create PostgreSQL RDS.

Implement:

```text
/users
/jobs
```

### Deliverable 2 - SQS

Create:

```text
processing-queue
processing-dlq
```

Implement:

```text
POST /jobs
```

The API should send a message to SQS.

### Deliverable 3 - Worker

Create a worker that:

1. Reads SQS message
2. Processes it
3. Writes result to PostgreSQL
4. Deletes SQS message

### Deliverable 4 - Failure Handling

Intentionally make the worker fail.

Verify that messages eventually reach the DLQ.

### Deliverable 5 - DynamoDB

Create a small DynamoDB example.

Use it for something appropriate such as:

```text
request_id → request status
```

### Definition of Done

* [ ] API sends messages to SQS
* [ ] Worker consumes messages
* [ ] Worker writes to PostgreSQL
* [ ] Failed messages reach DLQ
* [ ] I understand RDS vs DynamoDB
* [ ] I understand when Redis would be useful

---

# Week 6 Deliverables - Lambda + EventBridge + Step Functions + CloudWatch

## Build

Create an event-driven document-processing workflow.

```text
S3
 ↓
EventBridge
 ↓
SQS
 ↓
Lambda / Worker
 ↓
Result
```

### Deliverable 1 - Lambda

Create a Lambda function that:

```text
Input Event
    ↓
Validate
    ↓
Process
    ↓
Return Result
```

### Deliverable 2 - EventBridge

Configure:

```text
S3 Event
   ↓
EventBridge Rule
   ↓
Target
```

### Deliverable 3 - Step Functions

Create a workflow:

```text
START
  ↓
Validate
  ↓
Process
  ↓
Check
  ↓
Success / Failure
```

Implement:

* [ ] Retry
* [ ] Catch
* [ ] Conditional branching

### Deliverable 4 - CloudWatch

Create a dashboard containing:

* [ ] Request count
* [ ] Error count
* [ ] Lambda errors
* [ ] SQS queue depth
* [ ] Application latency

### Deliverable 5 - Alarm

Create at least one useful alarm.

Example:

```text
SQS messages > threshold
        ↓
CloudWatch Alarm
        ↓
SNS notification
```

### Definition of Done

* [ ] Event triggers workflow
* [ ] Lambda works
* [ ] Step Functions workflow works
* [ ] Retry/catch works
* [ ] Logs are searchable
* [ ] CloudWatch alarm works

---

# Week 7 Deliverables - Bedrock + GenAI

## Build

Create a production-oriented GenAI API.

```text
User
 ↓
FastAPI
 ↓
Bedrock
 ↓
LLM
 ↓
Response
```

### Deliverable 1 - Bedrock API

Implement:

```text
POST /chat
```

Input:

```json
{
  "message": "Explain AWS IAM"
}
```

Output:

```json
{
  "response": "..."
}
```

### Deliverable 2 - Streaming

Implement streaming responses.

### Deliverable 3 - Tool Calling

Create at least one tool.

Example:

```text
LLM
 ↓
calculate_cost()
```

or:

```text
LLM
 ↓
get_job_status()
```

### Deliverable 4 - Guardrails

Implement appropriate safety/validation controls.

### Deliverable 5 - Observability

Track:

* [ ] Request latency
* [ ] Model latency
* [ ] Token usage
* [ ] Errors
* [ ] Approximate cost per request

### Deliverable 6 - Architecture

Create:

```text
docs/week-07-bedrock.md
```

Explain:

* Why Bedrock?
* Model selection
* Cost considerations
* Latency considerations
* Streaming
* Tool calling
* Security

### Definition of Done

* [ ] LLM API works
* [ ] Streaming works
* [ ] Tool calling works
* [ ] Usage is monitored
* [ ] You can explain Bedrock architecture

---

# Week 8 Deliverables - RAG + Production Architecture

## Build

Create an AWS RAG system.

```text
Documents
   ↓
S3
   ↓
Ingestion
   ↓
Chunking
   ↓
Embeddings
   ↓
Vector Search
   ↓
Retrieval
   ↓
Bedrock
   ↓
Answer
```

### Deliverable 1 - Document Upload

Support:

```text
PDF
TXT
DOCX
```

Upload documents to S3.

### Deliverable 2 - Ingestion Pipeline

Implement:

```text
S3
 ↓
Event
 ↓
Processing
 ↓
Chunking
 ↓
Embedding
 ↓
Vector Store
```

### Deliverable 3 - RAG API

Implement:

```text
POST /ask
```

Example:

```json
{
  "question": "What are the candidate's AWS skills?"
}
```

### Deliverable 4 - Metadata Filtering

Support metadata such as:

```text
document_id
candidate_id
document_type
created_at
```

### Deliverable 5 - Retrieval Evaluation

Create at least 10 test questions.

Measure:

* Retrieval relevance
* Correct context
* Answer quality
* Hallucinations

Store results in:

```text
evaluation/rag-results.csv
```

### Deliverable 6 - Production Architecture

Create:

```text
docs/final-architecture.png
```

Architecture should include:

```text
CloudFront / WAF
        ↓
API Gateway / ALB
        ↓
ECS/Fargate
        ↓
S3
        ↓
EventBridge
        ↓
SQS
        ↓
Workers
        ↓
Vector Database
        ↓
Bedrock
        ↓
Response
```

Also include:

* IAM
* KMS
* Secrets Manager
* CloudWatch
* Autoscaling
* VPC
* Private subnets

### Definition of Done

* [ ] Documents upload to S3
* [ ] Documents are automatically processed
* [ ] Embeddings are generated
* [ ] Vector search works
* [ ] RAG answers questions
* [ ] Metadata filtering works
* [ ] Evaluation exists
* [ ] Production architecture is documented

---

# Final Capstone Deliverables

After Week 8, your GitHub repository should look approximately like:

```text
aws-genai-platform/
│
├── app/
│   ├── api/
│   ├── services/
│   ├── models/
│   └── main.py
│
├── workers/
│   └── document_processor/
│
├── infrastructure/
│   └── terraform/
│
├── tests/
│
├── evaluation/
│   └── rag-results.csv
│
├── docs/
│   ├── week-01-iam.md
│   ├── week-02-s3-ec2.md
│   ├── week-03-vpc.png
│   ├── week-03-network-debugging.md
│   ├── week-07-bedrock.md
│   └── final-architecture.png
│
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── README.md
```

---

# Final Demo

At the end of Week 8, record a **5–10 minute demo**.

Your demo should show:

1. Upload a document
2. Document appears in S3
3. Event triggers processing
4. Worker processes document
5. Embeddings are generated
6. Vector database is updated
7. User asks a question
8. Bedrock generates the answer
9. CloudWatch shows application activity
10. Show the AWS architecture

---

# Final Interview Deliverable

Create:

```text
docs/interview-architecture.md
```

Answer these:

### Architecture

* Why ECS instead of Lambda?
* Why S3 instead of EBS?
* Why SQS?
* Why private subnets?
* Why ALB?
* Why Bedrock?
* Why this vector database?
* Where are the bottlenecks?
* What happens if a worker crashes?
* What happens if Bedrock is unavailable?
* How does the system scale?
* How would you reduce costs?
* How would you secure the system?
* How would you monitor it?
* How would you make it highly available?

---

# Weekly Evidence Rule

At the end of **every week**, produce these 4 things:

```text
1. Working code
2. Architecture diagram
3. Documentation
4. 5–10 interview questions answered
```

Your Git history should tell the story:

```text
Week 1 → IAM
Week 2 → EC2 + S3
Week 3 → VPC
Week 4 → ECS
Week 5 → SQS + RDS
Week 6 → Event-driven architecture
Week 7 → Bedrock
Week 8 → Production RAG
```

---

# Weekly Scorecard

Score yourself from **0–2**:

| Skill        | 0                | 1                   | 2                          |
| ------------ | ---------------- | ------------------- | -------------------------- |
| Concepts     | Don't understand | Understand basics   | Can explain deeply         |
| Hands-on     | Couldn't build   | Built with tutorial | Built independently        |
| Debugging    | Can't debug      | Can follow docs     | Can diagnose independently |
| Architecture | Can't design     | Can copy patterns   | Can design independently   |
| Security     | Don't know       | Basic understanding | Can implement securely     |
| Cost         | Don't know       | Basic awareness     | Can optimize               |
| Interview    | Can't answer     | Partial answer      | Confident answer           |

### Weekly target

**Minimum: 10/14**

### Final target

**80%+ across all categories**

---

# Most Important Rule

Don't measure progress by:

> "How many AWS services have I learned?"

Measure progress by:

> "How many production problems can I solve without a tutorial?"

The end goal is not to know 50 AWS services.

The end goal is to look at a requirement and confidently say:

```text
"This is the architecture I would use.
Here's why.
Here's how I would secure it.
Here's how I would scale it.
Here's how I would monitor it.
Here's what could fail.
And here's what it will approximately cost."
```

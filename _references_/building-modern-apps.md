# Building Modern Apps

All Apps use IntelliJ IDEA, Gradle w/ Kotlin, Unit tests using JUnit 5 (w/ Hamcret and AssertJ) and Mockito. Also, they are packaged as Docker images

## Starter Apps
- Single Page App (SPA)
- Containerized Microservice or Serverless App that...
  + Performs a Computational logic and returns JSON payload
  + Acts as a REST client and gets data from httpbin (or other public) APIs
  + Integrates with *DynamoDB* (or, *MongoDB*)
  + Integrates with *Aurora/Postgres* (or, *PostgreSQL*)
  + Integrates with *ElastiCache* (or, *Redis*)
  + Integrates with *SNS* and/or *SQS* (or, *Kafka*)
  + Integrates with *S3*
  + Integrates with *SNS* and/or *SQS*

## Stox Shop! 
- Capabilities:
  + Allow users to create a basket of stocks. 
    - Support Symbol Look, which should make a live call and show latest information about the company
    - Support Add, Edit and Delete
    - Fields to provide: Name, Email, Stock Symbol, Number of Shares Purchased, Cost/Share, Total Cost, Date of Purchase
    - List View shows: Stock Symbol, Company Name, Number of Shares Purchased, Cost/Share, Total Cost, Date of Purchase, Total Value Now, % Gain/Loss, Status
  + Adding and/or Editing is handled using synchronous API call
  + Deleting will trigger Worker via SQS. Worker will use SNS (or SES) to send email asking for confirmation
  + User's selection of stocks as well as Audit trail is stored in Aurora Serverless (MySQL) and/or DynamoDB
  + List view is cached in ElastiCache, with Refresh functionality
- Microservices: Web App (Fargate or EKS), Web API (Fargate or EKS, API Gateway), Worker (Lambda, API Gateway)
- DynamoDB, ElastiCache (Redis)
- SQS, SNS/SES

## Learn from Peers: Cloud Native Microservices Sample Apps
- [GCP Microservices Demo App](https://github.com/GoogleCloudPlatform/microservices-demo)
- [Weaveworks Sock Shop](https://microservices-demo.github.io/)
- [Twitter Voting App](https://github.com/dockersamples/example-voting-app)
- [Scaling Microservices with Message Queues, Spring Boot and Kubernetes](https://medium.com/hackernoon/scaling-microservices-with-message-queues-spring-boot-and-kubernetes-9ba4b0e48bdf)
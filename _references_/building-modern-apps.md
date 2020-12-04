# Building Modern Apps

## Axioms
- Use an IDE (IntelliJ IDEA)
- Use a Build tool (Gradle w/ Kotlin)
- Write Unit tests! (JUnit 5 w/ Hamcret Matchers, and Mockito)
- Package it as OCI compliant image
- Use Git as SCM along with an actual CI/CD Pipeline
- All Apps MUST read the secrets necessary to integrate with the backends at startup time by talking to Vault (or similar AWS services)

## Starter Apps
- Single Page App (SPA)
- Create a server-side delivered Web App
  + With AuthC
- Create RESTful API
  + Responds with JSON Payload
  + With CORS enabled
- Create an App that interacts with RESTful API
  + JSON Payload
  + With AuthC
  + GET, POST, PUT, DELETE
- Create an App that interacts with PostgreSQL (or *Aurora/Postgres*)
- Create an App that interacts with MongoDB (or *DynamoDB*)
- Create an App that interacts with Redis (or *ElastiCache*)
- Create an App that publishes messages to Kafka (or *SNS* and/or *SQS*)
  + Create an App that that publishes messages to RabbitMQ
- Create an App that reads messages from Kafka (or *SNS* and/or *SQS*)
  + Create an App that reads messages from RabbitMQ
- Create an App that uploads file to S3 compliant backend like Minio (or *S3*)
- Create Serverless App
  + AWS Lambda 
  + Google Cloud Run

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
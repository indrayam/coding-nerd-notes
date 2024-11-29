# Building Modern Apps (in 2020s)

## Tools of the Trade

- Use an IDE (IntelliJ IDEA)
- Use a Build tool (Gradle w/ Groovy DSL)
- Write Unit tests! (JUnit 5 w/ Hamcret Matchers, and Mockito)
- Package it as OCI compliant image
- Use Git as SCM along with an actual CI/CD Pipeline
- All Apps **MUST** read the secrets necessary to integrate with the backends at startup time by talking to Vault (or similar AWS services)

## S4! Sharma Stox Shop Simulator

- Capabilities:
  - Allow users to create a basket of stocks.
    - AuthC that captures Name
    - Support Symbol Look
    - Support Add, Edit and Delete
    - Fields to provide: Stock Symbol, Number of Shares Purchased, Cost/Share, Total Cost, Date of Purchase
    - List View shows: Stock Symbol, Company Name, Number of Shares Purchased, Cost/Share, Total Cost, Date of Purchase, Total Value Now, % Gain/Loss, Status
  - Symbol Lookup is powered by a synchronous API call
  - Add/Edit/Delete is handled asynchronously by pushing messages to a Queue
    - An eWorker process it in the background
  - List view is cached. Offers Refresh functionality
- 3. Microservices:
  - 1. Single Page Web App (3-4 Transition Screens)
  - 2. Facade API
    - Symbol Lookup Service (External API call)
    - List Stocks Selected Service (Redis call, followed by MongoDB if necessary)
    - Async Events (Lambda) Proxy Service (RabbitMQ call)
    - List Trasaction History Service (MongoDB call)
  - 3. Event Worker/Lambda
    - Process Add Events
    - Process Edit Events
    - Process Delete Events
- Data Model:
  - User Stox: One document per user
  - User Stox Trades: One document per stock trade per user

## S3! Sharma Software Store

- Software: 
  - seaz-web-app, seaz-software-web-api, seaz-software-eworker
- Software Functionality:
  - Build a SpringBoot-based Angular App
  - Angular App makes an API call and shows a list of software stored in MongoDB (subset of the data)
  - Upon clicking the Software Name, I go to the Software Details screen. Every time you see that, you make an API call (POST) to store the number of times the Software was accessed
  - The API stores the message on RabbitMQ (or Kafka)
  - An eWorker processes the “number of times the software was accessed" and updates MongoDB
  - Refreshing the Software Details Screen shows the updated count of the number of times the Software Details was accessed
- App Platforms:
  - Kafka
  - MongoDB
  - Redis
- Infrastructure:
  - DNS on Cloudflare
  - SSL cert from Let’s Encrypt
  - HAProxy front-end
  - 1 Master, 5 Node Kubernetes Cluster with Contour Ingress Controller
  - Kafka on a VM
  - MongoDB on a VM
  - Redis on a VM

## Learn from Peers: Cloud Native Microservices Sample Apps

- [Scaling Microservices with Message Queues, Spring Boot and Kubernetes](https://medium.com/hackernoon/scaling-microservices-with-message-queues-spring-boot-and-kubernetes-9ba4b0e48bdf)
- [GCP Microservices Demo App](https://github.com/GoogleCloudPlatform/microservices-demo)
- [Twitter Voting App](https://github.com/dockersamples/example-voting-app)
- [Weaveworks Sock Shop](https://microservices-demo.github.io/) DEPRECATED


# Hands-On Skills

## Axioms
- Use an IDE (IntelliJ IDEA)
- Use a Build tool (Gradle w/ Kotlin)
- Write Unit tests! (JUnit 5 w/ Hamcret Matchers, and Mockito)
- Package it as OCI compliant image
- Use Git as SCM along with an actual CI/CD Pipeline
- All Apps **MUST** read the secrets necessary to integrate with the backends at startup time by talking to Vault (or similar AWS services)

## Basics
- Single Page App (SPA)
- Create an App that implements Rock, Paper and Scissors game where user's input is received from the Console
- Create an App that implements a Class Hierarchy: Employee, Manager, Executive
- Create an App that implements a List of Employees and perform all kinds of operations on it
- Create an App that Reads and Writes from/to a CSV file
- Create an App that Reads and Writes from/to a JSON file
- Create an App that traverses a folder structure and prints file and folder name with additional file/folder attributes
- Create an App that uses Locale, Number Formatting and Currency Formatting to print money in acceptable format in US, UK, Germany and India 
- Create an App that uses Dates to find current date in different timezones, difference between two dates, a future date and a past date

## Building Apps
- Create a server-side delivered Web App
  + With AuthC
- Create RESTful API
  + Responds with JSON Payload
  + With CORS enabled
- Create an App that interacts with RESTful API
  + JSON Payload
  + With AuthC
  + GET, POST, PUT, DELETE
- Create an App that interacts with PostgreSQL
- Create an App that interacts with MongoDB
- Create an App that interacts with Redis
- Create an App that publishes messages to Kafka
  + Create an App that that publishes messages to RabbitMQ
- Create an App that reads messages from Kafka
  + Create an App that reads messages from RabbitMQ
- Create an App that uploads file to S3 compliant backend like Minio (or *S3*)
- Create Serverless App
  + AWS Lambda 
  + Google Cloud Run

## Reference Sites
- [Learn Kotlin by Example](https://play.kotlinlang.org/byExample/overview)
- [Coding Bat - Java](https://codingbat.com/java)

## Open Source Nuggets

#### Popular Java Utility SDKs
- [Apache Commons for Validators](https://commons.apache.org/components.html)
- [Google Guava](https://github.com/google/guava)
- [Google Gson](https://github.com/google/gson/blob/master/UserGuide.md)
- Jackson: [Core](https://github.com/FasterXML/jackson-core), [Annotations](https://github.com/FasterXML/jackson-annotations), [Databind](https://github.com/FasterXML/jackson-databind)
- [JAXB](https://javaee.github.io/jaxb-v2/doc/user-guide/release-documentation.html)
- Lombok: [Stable](https://projectlombok.org/features/all), [API Doc](https://projectlombok.org/api/)
- [SL4J](http://www.slf4j.org/manual.html), [Log4j 2](https://logging.apache.org/log4j/2.x/javadoc.html)
- JUnit 5 ([User Guide](https://junit.org/junit5/docs/current/user-guide/), [API Doc](https://junit.org/junit5/docs/current/api/org.junit.jupiter.api/org/junit/jupiter/api/package-summary.html)), Hamcrest Matchers ([Tutorial](http://hamcrest.org/JavaHamcrest/tutorial), [API Doc](http://hamcrest.org/JavaHamcrest/javadoc/2.2/)), [AssertJ Assertions](https://assertj.github.io/doc/)
- [Mockito](https://javadoc.io/doc/org.mockito/mockito-core/latest/org/mockito/Mockito.html)
- [more...](https://towardsdatascience.com/25-lesser-known-java-libraries-you-should-try-ff8abd354a94)

#### Popular Kotlin Utility SDKs
- MockK
- Ktor

#### Public RESTful APIs
- [Space Station and Astronauts API](http://open-notify.org/)
- [EC2 Shop API](https://ec2.shop/)
- CoinMarket API
  + [Pro](https://pro.coinmarketcap.com/account/)
  + [Sandbox](https://sandbox.coinmarketcap.com/account/)
- [AlphaVantage API](https://www.alphavantage.co/documentation/)
- [JSONbox.io](https://jsonbox.io/)
- [Httpbin.org](https://httpbin.org/)
- [Internet Chuck Norris Jokes Database](http://www.icndb.com/api/)


#### Popular GitHub Repos
- [Awesome Java](https://github.com/akullpp/awesome-java)
- [Java Design Patterns](https://github.com/iluwatar/java-design-patterns)
- [Interviews](https://github.com/kdn251/interviews)
- [The Algorithms - Java](https://github.com/TheAlgorithms/Java)
- [Realworld](https://github.com/gothinkster/realworld)
- [GitHub: Modern Java Tutorial with Simple Examples](https://github.com/winterbe/java8-tutorial)
  + [Java 8 Tutorial](https://winterbe.com/posts/2014/03/16/java-8-tutorial/)
  + [Java 8 Streams Tutorial](https://winterbe.com/posts/2014/07/31/java8-stream-tutorial-examples/)
  + [Java 11 Tutorial](https://winterbe.com/posts/2018/09/24/java-11-tutorial/)
- [Cracking the Coding Interview - Java](https://github.com/careercup/CtCI-6th-Edition) 
# Event Driven Architecture Patterns

## 1. Outbox Pattern
### Problem
- An Event happened in your Boundary/System and you want to notify an another Boundary/System.
- Steps
  -  Save the event to DB.
  -  Publish the event to Message Broker/Queue.
- What happens if publishing to Message Broker/Queue.

### Solution
- The Outbox Pattern solves this problem by writing the messages to be published to the database(Imagine Outbox) with your state changes within the same transaction. 
- A seperate job/publisher will pull the messages and send them to your Message Broker/Queue.

- Source : https://codeopinion.com/my-top-patterns-for-event-driven-architecture

![Image](Outbox-Pattern-Fig.jpg)

## 2. Event Choreography & Orchestration (SAGA)
### Problem
- Consistency dor Distributed Transaction

### Solution

Event Choreography is driven entirely by events being consumed and published by various boundaries within a system. There is no centralized coordination or logic. A long-running process workflow is created by one boundary publishing an event, another consuming it and performing some action, then publishing its own event. Depending on the workflow there could be many services involved but they are entirely decoupled and have no knowledge about how the entire workflow works.


## 3. Queries in a Microservice Environment - CQRS (Command Query Responsibility segregation)
### Problem
- Querying data across multiple services.
- In Monolith it would be a simple join in a single DB.

### Solution
- The API Composition pattern
- The Command Query Responsibility Segregation pattern.

#### The API Composition Pattern
- Create a service to compose all the individual results of queries from each service and combine them.
  - Where should the service Reside ? FE  BE , which service in BE ?  -  
- Use a reactive programming model to call these service sin parallel than calling them sequentially
#### The benefits and drawbacks of the API composition pattern
- __Drawbacks__
  -  Increased overhead   
  - Risk of reduced availability
  - Lack of transactional data consistency
- 
#### The CQRS Pattern
### Problem
- API Composition is partial Solution as it can't implement queries efficiently.
- The Database might not efficiently support that specific query
- joining large datasets across different services are difficult , RDBs do them efficientlty.
- 

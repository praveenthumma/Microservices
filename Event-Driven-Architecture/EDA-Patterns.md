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

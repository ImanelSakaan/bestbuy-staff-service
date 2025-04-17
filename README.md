# bestbuy-staff-service

# 1. Explanation of the staff-service microservice and its functionality
Microservices are a modern architectural approach in software development  
where an application is built as a collection of small, self-contained services,  
each responsible for a specific function or business capability.

- **Microservices** are a collection of services that are:
  - **Independently Deployable**
  - **Use API Communication**
  - **Loosely Coupled**
 
## Microservices Architecture
![image](https://github.com/user-attachments/assets/a1fd8ff4-914f-4218-95ac-5c5c63d7699a)

- **Microservices** are a collection of services that are:
  - **Independently Deployable**
  - **Use API Communication**
  - **Loosely Coupled**
  - **Organized Around Business Capabilities**
  - **Owned by a Small Team**
  - **Product Focused**

## Characteristics of Microservices

# 2. How to use the microservice, including endpoints for the CRUD operations.
- Each service can be deployed separately without having to deploy the entire system.  
  If a new feature or update is made to a specific service, only that service needs to be updated, leaving the rest of the application unaffected.

- Each service has its own **database** to avoid central bottlenecks.

- This independence **reduces downtime**, allows for **more frequent updates**, and **simplifies the deployment process**.

### Examples of Deployable or Executable Units

Formats or packaging mechanisms that allow you to deploy (or run) a service on its own:

- **Executable JAR file**: A Java Archive that can be executed directly by the Java Runtime Environment.
- **Operating system executable**: A file that the operating system recognizes as a program it can run, like an `.exe` file in Windows.
- **Docker container image**: An encapsulated environment that can run applications isolated from the host system.


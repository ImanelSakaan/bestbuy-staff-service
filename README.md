
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

## CRUD Operations

**CRUD** stands for **Create, Read, Update, and Delete** — the four basic functions used in persistent storage systems like databases.

### 1. Create
- Adds new data or records to a database.
- **Example:** Submitting a new product form to store it in the inventory database.

### 2. Read
- Retrieves or displays existing data from a database.
- **Example:** Viewing the list of all orders placed by customers.

### 3. Update
- Modifies existing data in the database.
- **Example:** Editing a product’s price or name in the admin dashboard.

### 4. Delete
- Removes data from the database.
- **Example:** Deleting an outdated product from the catalog.

### CRUD in RESTful APIs

| Operation | SQL Command | HTTP Method     |
|-----------|-------------|-----------------|
| Create    | `INSERT`    | `POST`          |
| Read      | `SELECT`    | `GET`           |
| Update    | `UPDATE`    | `PUT` / `PATCH` |
| Delete    | `DELETE`    | `DELETE`        |

## Architecture

The application has the following services: 

| Service | Description | Github Repo |
| --- | --- | --- |
| `store-front` | Web app for customers to place orders (Vue.js) | [store-front-L8](https://github.com/ImanelSakaan/store-front-L8) |
| `store-admin` | Web app used by store employees to view orders in queue and manage products (Vue.js) | [store-admin-L8](https://github.com/ImanelSakaan/store-admin-L8) |
| `order-service` | This service is used for placing orders (Javascript) | [order-service-L8](https://github.com/ImanelSakaan/order-service-L8) |
| `product-service` | This service is used to perform CRUD operations on products (Rust) | [product-service-L8](https://github.com/ImanelSakaan/product-service-L8) |
| `makeline-service` | This service handles processing orders from the queue and completing them (Golang) | [makeline-service-L8](https://github.com/ImanelSakaan/makeline-service-L8) |
| `ai-service` | Optional service for adding generative text and graphics creation (Python) | [ai-service-L8](https://github.com/ImanelSakaan/ai-service-L8) |
| `rabbitmq` | RabbitMQ for an order queue | [rabbitmq](https://github.com/docker-library/rabbitmq) |
| `mongodb` | MongoDB instance for persisted data | [mongodb](https://github.com/docker-library/mongo) |
| `virtual-customer` | Simulates order creation on a scheduled basis (Rust) | [virtual-customer-L8](https://github.com/ImanelSakaan/virtual-customer-L8) |
| `virtual-worker` | Simulates order completion on a scheduled basis (Rust) | [virtual-worker-L8](https://github.com/ImanelSakaan/virtual-worker-L8) |

# Step 2: Deploy Store-Front on Azure Static Web Apps
4.1. Create an Azure Static Web App
In the Azure Portal, navigate to "Static Web Apps" and create a new static web app.
Source: Choose GitHub as the deployment source.
Repository: Select the repository containing your store-front code.
Build Presets: Choose "Vue.js" if prompted.

# step 3 Containerizing the Best buy Store Microservices
### Step 3.1. Dockerize the order-service
      cd order-service-L8
      In the order-service directory, create a Dockerfile with the following content: and copy the code on it
      Build the Docker image:
      docker build -t order-service:latest .
      Run a Docker container from order-service:latest image and expose it on port 3000:
      docker run --rm -d -p 3000:3000 order-service:latest
<img width="637" alt="image" src="https://github.com/user-attachments/assets/44608e3c-0e36-495d-8337-c8b16dc4525b" />

### Step 3.2. Dockerize the product-service
cd product-service-L8
In the order-service directory, create a Dockerfile with the following content: and copy the code on it
docker build -t product-service:latest .
docker run --rm -d -p 3030:3030 product-service:latest
![image](https://github.com/user-attachments/assets/9233c0b5-02e7-4731-82c7-1076900169ff)

<img width="505" alt="image" src="https://github.com/user-attachments/assets/03bd5e1f-6a7e-4731-844e-11bdab13c032" />


### Step 3.3. Deploy to AKS:
bash
Copy
Edit
kubectl apply -f deployment.yaml
kubectl get services
<img width="546" alt="image" src="https://github.com/user-attachments/assets/bf5c6152-f251-4c42-b5b9-36a8a84811c4" />



<img width="546" alt="image" src="https://github.com/user-attachments/assets/5166d5f2-c42d-452c-b736-89d1e11548d2" />

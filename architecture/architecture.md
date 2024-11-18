# Content Management & Publication System

## Architecture


![diagram](https://github.com/user-attachments/assets/cb65cd76-7df3-49f9-9649-b1894d628a12)


### Components
1. **Frontend**:
   - Built using **Angular**.
   - Includes a mock **Authentication Service** to manage user roles locally (no backend communication).

2. **Backend**:
   - **API Gateway Service**: Routes client requests to the appropriate microservices and integrates with Eureka for service discovery.
   - **Service Discovery (Eureka)**: Dynamically registers and discovers backend microservices.
   - **Configuration Service**: Provides centralized configuration for all backend services.
   - **Microservices**:
     - **PostService**: Handles creating, editing, and listing posts.
     - **ReviewService**: Manages post approvals, rejections, and notifications.
     - **CommentService**: Handles user comments, including adding, editing, and deleting them.
   - **Database**: Each service uses **PostgreSQL** for data storage.


## Communication

1. **Synchronous Communication**:
   - Implemented using **OpenFeign** for direct API calls between services.

2. **Asynchronous Communication**:
   - Managed via **RabbitMQ** for event-driven messaging.


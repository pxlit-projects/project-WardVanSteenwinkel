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

## Synchronous Communication
**OpenFeign**: Utilized for real-time operations requiring immediate responses between microservices.

- **PostService**:
  - Fetch details about a specific post (title, content, author, creation date).  
- **ReviewService**:
  - Check the approval or rejection status of posts before displaying them.  
- **CommentService**:
  - Retrieve comments related to a post in real-time for users to view.  

---

### Asynchronous Communication
**RabbitMQ**: Used for event-driven communication between services to decouple operations and handle non-immediate tasks.

- **PostService to ReviewService**:
  - Send an event when a post is submitted for review.  
- **ReviewService to PostService**:
  - Notify that a post has been approved or rejected, with optional comments explaining the decision.  
- **CommentService**:
  - Broadcast when a new comment is added to a post, allowing other services to asynchronously handle updates.  



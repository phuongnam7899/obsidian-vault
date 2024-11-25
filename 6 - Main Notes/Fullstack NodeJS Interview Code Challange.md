2024-11-25 20:46

Tags: [[ReactJS]] [[JS]]

---

### **Advanced Frontend Tasks**

1. **Dynamic Microfrontend Integration**  
    **Scenario:**  
    A microfrontend team has created a React component library for reusable UI widgets. You're tasked to dynamically load a widget (a button with custom text) into an existing React application and ensure seamless communication between the host app and the microfrontend.
    
    - Implement the dynamic import using **Webpack Module Federation** or another bundler-based microfrontend technique.
    - Handle communication between the host and the microfrontend (e.g., passing and receiving events or props).
    
    **Focus:**
    
    - Dynamic imports.
    - Microfrontend architecture and inter-app communication.

- Create an app to expose the components/event bus
- Create app to:
	- remote the app that expose the components/event bus
	- Dynamic import
	- Use the event bus to communicate between micro-frontends

---

2. **Complex State Management**  
    **Scenario:**  
    Build a task tracker application where tasks can be added, updated, and filtered based on priority and status. Use **React Context API** or **Redux** with TypeScript.
    
    - Support optimistic UI updates when interacting with a mocked backend API.
    - Include undo functionality for accidental updates.
    
    **Focus:**
    
    - Scalable state management.
    - Asynchronous state handling with proper TypeScript integration.

- Create taskSlice with redux toolkit that define add, edit, undo reducers
- Create store with redducers config included the taskSlice reducer
- Provide the store to the app

---

### **Advanced Backend Tasks**

3. **GraphQL with Complex Nested Queries**  
    **Scenario:**  
    Create a GraphQL API to handle a complex schema for an insurance policy system:
    
    - Policies have nested relationships with customers, claims, and documents.
    - Implement a resolver to handle a query that fetches all active policies along with their claims and customer details.
    - Optimize the resolver to minimize over-fetching by batching and caching queries (e.g., with **Dataloader**).
    
    **Focus:**
    
    - GraphQL schema design.
    - Efficient query resolution.

---

4. **Distributed Task Queue**  
    **Scenario:**  
    Implement a task queue using **Redis** and Node.js for handling insurance claims processing.
    
    - Producer: Accepts claim data via a REST API and pushes tasks to the queue.
    - Consumer: Processes the tasks and updates the claim status in MongoDB.
    - Add a retry mechanism for failed tasks.
    
    **Focus:**
    
    - Distributed systems.
    - Fault tolerance.

---

### **Fullstack Tasks**

5. **Real-time Updates**  
    **Scenario:**  
    Build a real-time notification system for an insurance dashboard using **WebSockets**:
    
    - Backend: A NestJS service that broadcasts claim updates to connected clients.
    - Frontend: A React app that subscribes to these updates and displays them dynamically.
    
    **Focus:**
    
    - WebSocket implementation.
    - Synchronizing real-time data between server and client.

---

6. **End-to-End Application with Microservices**  
    **Scenario:**  
    Design a simplified insurance policy management system using microservices:
    
    - Service A: Handles user authentication (OAuth2 with JWT).
    - Service B: Manages policy data and CRUD operations.
    - Service C: Processes claims asynchronously using a message queue (RabbitMQ/Kafka).
    - Containerize all services using Docker, and orchestrate them using Kubernetes.
    
    **Focus:**
    
    - Microservices design.
    - Authentication and inter-service communication.

---

### **System Design Challenge**

7. **Scalable API Design**  
    **Scenario:**  
    Design a RESTful API system for the insurance platform:
    
    - Support high throughput for querying policy and claims data.
    - Implement rate limiting for clients to prevent abuse.
    - Discuss your choice of database (e.g., SQL vs. NoSQL) and justify it.
    - Provide a high-level design for caching frequently accessed data to reduce database load (e.g., Redis).
    
    **Focus:**
    
    - Scalability and caching.
    - API design best practices.

---

8. **Authentication and Authorization in a Distributed System**  
    **Scenario:**  
    Design an authentication and authorization system for a multi-tenant insurance application using Keycloak or another identity provider.
    
    - Users from different organizations should only access their respective data.
    - Demonstrate token validation and role-based access control (RBAC) in the API.
    - Explain how you would handle token renewal and session management.
    
    **Focus:**
    
    - Security.
    - Distributed authentication mechanisms.

---

### **Additional Advanced Concepts**

9. **Performance Optimization**  
    **Scenario:**  
    Optimize the performance of a React app that renders a list of 10,000 insurance policies.
    
    - Implement virtualization (e.g., `react-window` or `react-virtualized`).
    - Measure and optimize the rendering performance using React DevTools.
    
    **Focus:**
    
    - Performance debugging and optimization techniques.

---

10. **Observability and Monitoring**  
    **Scenario:**  
    Implement logging, metrics collection, and error tracking for a microservices-based application.
    
    - Use tools like Prometheus for metrics and ELK stack for logging.
    - Set up alerts for SLA breaches (e.g., response time > 500ms).
    
    **Focus:**
    
    - Production monitoring.
    - Observability best practices.

---
# References
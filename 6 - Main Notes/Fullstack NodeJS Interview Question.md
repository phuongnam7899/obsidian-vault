2024-11-23 13:32

Tags: [[Interview]] [[ReactJS]] [[JS]] [[Typescript]] [[Devops]]

---

### **General and Behavioral Questions**

1. Can you walk us through your experience in developing full-stack applications?
2. How do you prioritize tasks when working on cross-functional teams?
3. Describe a challenging project you worked on that required collaboration across multiple teams.
4. How do you ensure the code you write is efficient, maintainable, and scalable?
5. What steps do you take to stay updated with the latest trends in web development?

---

### **React.js Questions**

1. What are the key differences between class components and functional components in React?
	1. Old vs new
	2. Hooks
	3. life cycle vs props-state
2. Explain the concept of React Hooks. Can you name and describe the use of some commonly used hooks?
	1. Hook = function that can use react feature
3. How do you manage state in a large React application?
	1. useState for local
	2. useContext for bigger
	4. Redux - global state manage (RTK)
	5. React query forr server state
4. What strategies do you use to optimize performance in React applications?
	1. Using hooks like (useMemo, useCallback)
	2. Lazyload and Suspense
	3. Import optimize
	4. Infinite loading
	5. image
	6. ssr
	7. caching
5. Can you explain how React handles reconciliation?
	1. Compare previous virtual dom with new one if props changed
	2. Commit 
6. Have you worked with microfrontends using React? How did you manage inter-microfrontend communication?
	1. Pub-sub (window.dispatchEvent() and addEventListener)
	2. Shared state woth global store
	3. Event bus (RxJS or EventEmitter)

---

### **Node.js Questions**

1. How does the event loop work in Node.js?
	1. Call stack - Web APIs (Node API) - Task queue (MIcro/Macro)
	2. Event loop: continuously check call stack -> when empty, run microtassk -> macro task
2. Explain how you would handle asynchronous operations in Node.js.
	1. Then
	2. Async await
3. Can you walk us through how you would design an API using Express.js or NestJS?
	1. Understand requirements
	2. Define model
	3. Add routes
	4. Add controller to handle logic
		1. Write test case
		2. Validate the data
		3. Authorize if need
		4. Error handling
4. How do you handle error management in a Node.js application?
	1. Using middleware to centralize the error
		1. throw error with `next(new Error('Something went wrong'));`
		2. handle in the middleware put in the last
	2. Custom error classes
	3. Log the error
	4. Apply retry if need
5. What are some best practices for structuring a Node.js backend application?
	1. Model: db model
	2. Controller: logic for route
	3. Route
	4. Service: business logic share accross controller
	5. Utils
	6. Config
	7. Middlewares
6. What are some best practices for structuring a Node.js backend application follow DDD
	1. shared: common business logic used by multiple module
		1. errors
		2. utils
		3. middleware
		4. validation
	2. infrastructure: technical concern like db, queue, cache,...
		1. database
		2. message-broker
		3. mailer
		4. api client: for external api
	3. modules: each module contain bounded context
		1. controller
		2. service
		3. model
		4. routes
		5. useCase
		6. event

---

### **TypeScript Questions**

1. What are the advantages of using TypeScript over JavaScript?
2. How do interfaces and types differ in TypeScript?
	1. interface is for object only, type is not
	2. interface could be implemented by other class, type cannot
	3. 
3. Can you explain TypeScript’s `any`, `unknown`, and `never` types?
4. How do you use generics in TypeScript? Provide an example.
5. How do you set up and enforce strict typing in a large project?

---

### **Microfrontend Architecture Questions**

1. What are the advantages and challenges of using microfrontends?
2. How do you ensure consistency in a microfrontend architecture?
3. Can you describe a scenario where you implemented communication between microfrontends?
4. What tools or frameworks have you used for microfrontend architecture?
5. How do you handle shared state or dependencies across multiple microfrontends?

---

### **Server-Side Frameworks**

1. What are the differences between Express.js and NestJS?
2. How would you implement middleware in Express.js or NestJS?
3. Explain how server-side rendering (SSR) is implemented in NestJS.
4. How do you design RESTful APIs to be both scalable and maintainable?
5. Have you implemented authentication mechanisms in a backend framework? If so, how?

---

### **Containerization and Orchestration**

1. What is the difference between Docker images and containers?
2. How do you use Docker to containerize an application?
3. Can you explain the role of Kubernetes in container orchestration?
4. How do you manage scalability and load balancing in a Kubernetes environment?
5. What are some common challenges in deploying containerized applications, and how do you address them?

---

### **Database Management**

1. How do you decide between using MongoDB and SQL databases?
2. Can you explain indexing in databases and its impact on performance?
3. How do you handle migrations in a database schema?
4. Have you implemented transactions in a database? How do they work in MongoDB or SQL?
	1. Start transaction
	2. Make change
	3. Commit/rollback if failed
	4. ACID: atomicity, consistency, isolation, durability
5. How do you optimize database queries in a high-traffic application?

---

### **GraphQL**

1. What are the main differences between REST and GraphQL?
2. How do you define a schema in GraphQL?
3. Explain how you would handle resolving nested queries in GraphQL.
4. What strategies do you use to optimize GraphQL data fetching?
5. Have you faced challenges while implementing GraphQL APIs? How did you overcome them?

---

### **Microservices Architecture**

1. What is the difference between microservices and monolithic architectures?
2. How do you handle inter-service communication in microservices?
3. What tools or patterns do you use to manage service discovery?
4. How do you ensure fault tolerance in a microservices-based system?
5. Can you describe a scenario where you implemented a message queue like RabbitMQ or Kafka?

---

### **Authentication and Authorization**

1. What is the difference between authentication and authorization?
	1. "who are you" vs "what you can do"
2. How do you implement JWT-based authentication?
3. Can you explain the OAuth2 flow?
	1. Client redirect to login url
	2. User login
	3. Redirect back to main page with authorization code (access/refresh token)
	4. Client use token to make request to resources
4. How do you handle token expiration and renewal in an application?
5. How would you design a secure login system for a web application?
	1. bcript to hash user password
	2. jwt to generate token when login
	3. token sent to server through http-only cookie / header
	4. middleware to check token
	5. token need to be expirable
	6. refresh token

---

### **Performance Optimization**

1. What caching strategies have you implemented to optimize application performance?
	1. In-memory
	2. CDN cache
	3. DB caching
	4. HTTP cache
	5. Browser cache (IndexedDB)
	6. Distributed cache (cache across multi instance)
2. How do you measure and improve the performance of a React or Node.js application?
3. What tools do you use to monitor performance in production?
	1. React devtoool
	2. Lighthouse
4. How would you handle large datasets in a client-server interaction?
	1. Pagination
	2. Lazy load (infinity scroll)
	3. Cached
5. What techniques do you use to reduce bundle size in React applications?
	1. Code Splitting (React.lazy, React.Suspense)
	2. Tree Shaking
	3. Optimize Dependencies
	4. Minification
	5. Image Optimization (compress, webp, lazy)
	6. CDN
	7. Bundle analyzer
	8. SSR

---

### **DevOps and Deployment**

1. What is a CI/CD pipeline, and why is it important?
2. How do you automate deployment using tools like Jenkins, GitHub Actions, or GitLab CI?
3. Have you worked with cloud platforms like AWS, Azure, or GCP? How do you manage deployments there?
4. How do you monitor applications in production environments?
5. What are some common issues you’ve encountered during deployment, and how did you resolve them?

---

### **Soft Skills and Problem-Solving**

1. Describe a time you had to debug a complex issue in production. How did you handle it?
2. How do you handle disagreements or conflicting ideas within a team?
3. What steps do you take to ensure clear communication with stakeholders?
4. Can you give an example of a feature you implemented that improved user experience?
5. How do you mentor junior developers or help them get up to speed on a project?

---
# References
- [[Fullstack NodeJS Interview Code Challange]]
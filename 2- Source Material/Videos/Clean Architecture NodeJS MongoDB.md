Source link: https://www.youtube.com/watch?v=CnailTcJV_U&t=16s

Status: #source-absorbing  

---

# Clean Architecture Basic
- `Entity Layer`: contain basic concepts of the business, for example:
	- For social media application: Post, Comment, User, Group,...
	- For E-Commerce application: Order, Product, Customer,...
- `Use Case Layer`: Contain interaction between entities:
	- For social media: user make a post, user comment to post,
	- For e-commerce: customer place an order, customer make payment,...
- `Interface Adapter`: to isolate the use-case with the tool we used in Framework and Drivers Layer
- `Framework and Drivers`: 
	- ExpressJS, NestJS,...
	- DB: Mongo, Postgres
- Flow of dependency is from outside->inside
# Code
>[!i] Repo link : https://github.com/dev-mastery/comments-api/blob/master/src/comment/comment.js

`/comment`
- `comment.js`: is the entity
		![[Pasted image 20250107094508.png]]
	- the file does not have import anything, because Entity is the most inner layer -> should not have dependencies
	- `buildMakeComment()` return a function that could be use to create new comment (the returned function should :
		- do the validate work also
		- return a ==frozen== object the contain many methods to get/upadate (to protect the object from invalid state)
	- instead, it has dependency injection
		![[Pasted image 20250107094353.png]]
		
> [!s] Benefits
> - Easier to test (can pass mock dependency)
> - Don't need dependency code to be ready (just define the interface like that first, implement the dependency later)
> - (Most important) Can change the implementation of dependency later without affect the entity

- `index.js`: bring in all thing needed to build the `makeComment` function
`/use-cases`: contain all valid interaction in the application
- All files should only depend on entity
- All use cases return a factory function that return a function to handle use case
- The database info should be injected to handle the database related logic
- Should validate logic related to the use case
- If related to another use cases -> inject into the function
![[Pasted image 20250107100959.png]]
- `index.js`: to build and export the function for each use case
`/data-access`: return functions to interact with database
- Contain specific database type related syntax
- the `makeDB()` is injected to be able to change the MongoDB instance in runtime (like in test, or link to other DB)
- `index.js`: setup connection
`/controllers`: is interface adapter, aim to be the connection point of framework and use cases
- should export a factory function to return the controller function
- Do not care about the implementation of use cases
- get the input from the framework/driver (https, grpc, desktop,...) then convert to the format that the use cases understandable
- `index.js` create the function from the factory ->  export it with used after injecting dependencies
`index.js`: represent the framework layer (created with expressjs in this case) -> import the controllers -> use them in the routes

---
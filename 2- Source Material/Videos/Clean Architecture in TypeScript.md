Source link: https://www.youtube.com/watch?v=f7Su4KoqSio

Status: #source-eating 

---

# Dependency Inversion Principle
![[Pasted image 20250107105022.png]]
- The service should not be dependent on the concrete repository, because when you change the repository -> the service will break
- Instead,  the Repository should depend on an interface, then Service use that interface 
# Interface Adapter
![[Pasted image 20250107105553.png]]
# The modern take
![[Pasted image 20250107105848.png]]
- Infrastructure: contains interface for Database, event bus, mail sender,...
- Presentation: web, mobile, desktop, web api, cli,...
- Application: usually to create use cases
- Domain: contains entities and enterprise-wide logic
# The main component
![[Pasted image 20250107110757.png]]
- main component know everything
- bootstrap the application by managing the injection
# Components principles
- Reuse/release equivalence
- Common closure
- Acyclic dependency
- Common reuse
# Vertical slide architecture
![[Pasted image 20250107111749.png]]
# Side thought
- Can use dependency injection framework or factories function
# Code flow
> https://github.com/donnyroufs/clean-architecture-in-typescript-yt/blob/main/src/presentation/ApiServer.ts
- Create a `main.ts`
- Create a folder for each layer
- `/domain`: contains entity define  (and validate)
```ts
import { randomUUID } from "crypto";

export class Logbook {
  public constructor(
    public readonly name: string,
    public readonly userId: string,
    public readonly id: string = randomUUID()
  ) { }
}
```
- `/application`:
	- Create a file for each use case
	- File should export a class that have 1 `execute()` method
	- Create an interface for `CreateLogBookDataTransferObject` -> use it for the `execute` argument
	- The `_logbookRepo` should be injected to class with interface `ILogbookRepository` (we will create implementation for it later)
	- Create interface for `execute()`'s output
```ts
import { Logbook } from "../domain/Logbook"
import { IUseCase } from "../shared/IUseCase"
import { ILogbookRepository } from "./ILogbookRepository"

interface ICreateLogbookDto {
  name: string
  userId: string
}

export interface ICreateLogbookResult {
  logbookId: string
}

export class CreateLogbookUseCase implements IUseCase<ICreateLogbookDto, ICreateLogbookResult> {
  public constructor(private readonly _logbookRepo: ILogbookRepository) {}

  public async execute(
    input: ICreateLogbookDto
  ): Promise<ICreateLogbookResult> {
    const logbook = new Logbook(input.name, input.userId)

    const result = await this._logbookRepo.save(logbook)

    if (!result) {
      throw new Error("Could not save logbook.")
    }

    return {
      logbookId: logbook.id,
    }
  }
}
```
 - `/presentation`: 
	 - `apiServer.ts`: create server using ExpressJS or other framework
		 - Controllers should be injected into server class
```ts
import express from 'express'
import { CreateLogbookController } from './CreateLogbookController'
import { GetLogbookController } from './GetLogbookController'

export class ApiServer {
  public static async run(port: number, controller: CreateLogbookController, getController: GetLogbookController): Promise<void> {
    const app = express()
    app.use(express.json())

    app.post('/logbooks', (req, res) => controller.handle(req, res))
    app.get('/logbooks', (req, res) => getController.handle(req, res))

    app.listen(port, () => {
      console.log('server is running')
    })
  }
}
```




---
2025-04-06 09:13

Tags: [[AWS EC2]]

---

- When there's some free resource of the amazon system, client can use it. But when it is needed again, client will be disconnected from it
- Cheaper than on-demand (-90%)
- Ideal for flexible start and end time work and can withstand interruption (batch job, data analysis, image process,...)

# How to request
![[Pasted image 20250406094816.png]]
- Define max spot price that you want to pay -> get the instance while current spot price < that value (price may varied base on time and AZ)
- Choose request type `one-time` or `persistance`: if persistance, the request will be auto created again if interrupted
- When the price go higher than your -> can choose to stop/terminate it in 2min

```mermaid
graph TB
    Start([Start]) --> RequestType{Request Type}
    
    %% One-time Flow
    RequestType -->|One-time| Price1{Price Check}
    Price1 -->|Price > Max| Pending1[Pending]
    Pending1 --> Price1
    Price1 -->|Price <= Max| Launch1[Launch Instance]
    Launch1 --> Running1[Running]
    Running1 --> Check1{Interruption?}
    Check1 -->|No| Running1
    Check1 -->|Yes| Warning1[2min Warning]
    Warning1 --> Terminate1[Terminate]
    Terminate1 --> End1([Request Ends])
    
    %% Persistent Flow
    RequestType -->|Persistent| Price2{Price Check}
    Price2 -->|Price > Max| Pending2[Pending]
    Pending2 --> Price2
    Price2 -->|Price <= Max| Launch2[Launch Instance]
    Launch2 --> Running2[Running]
    Running2 --> Check2{Interruption?}
    Check2 -->|No| Running2
    Check2 -->|Yes| Warning2[2min Warning]
    Warning2 --> Terminate2[Terminate]
    Terminate2 --> Price2
```

> [!w] Cancel the Spot Request NOT mean the instance is terminated


---
# References
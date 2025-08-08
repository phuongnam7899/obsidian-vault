2025-07-24 20:22

Tags: [[Devops]] 

---


| Feature         | VM                                                                                                                                                                                    | Container                                                                                       |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Concept         | Full-computer emulation                                                                                                                                                               | Software                                                                                        |
| Includes        | OS. apps and dependencies                                                                                                                                                             |                                                                                                 |
| Resource usage  | Use more, suitable for heavier overhead                                                                                                                                               |                                                                                                 |
| Start-up speed  | Slower                                                                                                                                                                                |                                                                                                 |
| Portability     | Less, may require config changes                                                                                                                                                      | Highly, run consistently in different machine                                                   |
| Use cases       | - Want control over OS<br>- Demand strong isolation between applications<br>- Legacy applic - Modern, cloud-native apps<br>- Microservices architecture<br>- Prioritizing portability |                                                                                                 |
| Security        | - Better because each VM has it own OS                                                                                                                                                |                                                                                                 |
| Deployment      | - Deploy individual VM using windows admin center or Hyper-V or VMware or Powershell or System Center VM manager                                                                      | - Multiple containers could be deployed using orchestration service such as Azure K8S           |
| Storage         | - Virtual hard disk for local storage<br>- SMB file share for shared storage                                                                                                          | - Using Azure disk for local storage<br>- Azure Files for storage that shared by multiple nodes |
| Fault Tolerance | - Can be failover to another server in a cluster                                                                                                                                      | - When a node failed, it is rapidly recreated by the orchestration service                      |
```mermaid
graph TD
    A[Physical Machine]
    A --> B[Host OS]
    
    %% VM Branch
    B --> C[Hypervisor]
    C --> VM1[VM 1]
    C --> VM2[VM 2]
    VM1 --> VM1_OS[Guest OS]
    VM1_OS --> VM1_Lib[Libraries/Bins]
    VM1_Lib --> VM1_App[App]
    VM2 --> VM2_OS[Guest OS]
    VM2_OS --> VM2_Lib[Libraries/Bins]
    VM2_Lib --> VM2_App[App]
    
    %% Container Branch
    B --> D[Container Engine]
    D --> Cont1[Container 1]
    D --> Cont2[Container 2]
    Cont1 --> Cont1_Lib[Libraries/Bins]
    Cont1_Lib --> Cont1_App[App]
    Cont2 --> Cont2_Lib[Libraries/Bins]
    Cont2_Lib --> Cont2_App[App]
```

---
# References
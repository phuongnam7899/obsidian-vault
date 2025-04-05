2025-04-05 09:34

Tags: [[AWS]] [[Security]] [[Networking]]

---

- Is fundamental of network security in AWS
- a ==virtual firewall for [[AWS EC2]] instance or group of instances== (control how traffic allowed in or out of EC2):
    - By default ==denies all in== traffic and ==allow all out== traffic
    - Perform stateful packet filtering: remember the previous decision that were made
    - SG rules can be referenced by IP or by other SGs
```mermaid
graph LR
    subgraph Internet["🌐 WWW"]
    end

    subgraph SG["🔒 S-Group"]
        EC2["💻 EC2 Instance"]
    end
    
	SG -->|"Outbound Traffic"| Internet
	Internet -->|"Inbound Traffic"| SG
    
```
- Security group regulate:
	- Access to ports
	- Authorized [[IP ranges]] - [[IPv4]] and [[IPv6]]
	- Control inbound/outbound network
- Rule include:
	- Type
	- Protocol
	- Port range
	- Source
	- Description
- Example:
```mermaid
graph LR
    EC2["EC2 Instance<br/>IP XX.XX.XX.XX"]
    
    subgraph SG1_In["🔒 Security Group 1<br/>Inbound<br/>Filter IP / Port with Rules"]
    end
    
    subgraph SG1_Out["🔒 Security Group 1<br/>Outbound<br/>Filter IP / Port with Rules"]
    end
    
    Auth["Your Computer - IP XX.XX.XX.XX<br/>(authorised port 22)"]
    NonAuth["Other Computer<br/>(not authorised port 22)"]
    WWW["WWW<br/>Any IP - Any Port"]
    
    Auth -->|"Port 22"| SG1_In
    NonAuth -->|"Port 22"| SG1_In
    SG1_In --- EC2
    
    EC2 --- SG1_Out
    SG1_Out -->|"Any Port"| WWW

    style Auth fill:#gray
    style NonAuth fill:#gray
    style WWW fill:#gray
    style EC2 fill:#4B96D7
    style SG1_In fill:#FFA500
    style SG1_Out fill:#FFA500
```
- Good to know:
	- SG can be attached to multiple instances
	- Locked down to a region / [[VPC]] combination
	- Live OUTSIDE the EC2 (if requests are block, EC2 won't eve know it)

---
# References
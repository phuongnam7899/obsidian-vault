2025-04-05 09:34

Tags: [[AWS]] [[Security]] [[Networking]]

---

- Is fundamental of network security in AWS
- a ==virtual firewall for [[AWS EC2]] instance or group of instances== (control how traffic allowed in or out of EC2):
    - By default ==denies all in== traffic and ==allow all out== traffic
    - Perform stateful packet filtering: remember the previous decision that were made
    - SG rules can be referenced by IP or by other SGs
![[Security group 2025-04-05 09.40.13.excalidraw]]

---
# References
2025-03-31 20:25

Tags: [[AWS]]

---

- Build a global footprint: route user to nearest available footprint
  ![[Cloud Practitioner Essentials 2025-01-13 08.05.33.excalidraw]]

## Select region

Determine region for services, data, applications based on:

- Legal: is it allowed to be placed there?
  - For example: GDPR (General Data Protection Regulation): data from EU is not allowed to move to outer of EU
- Nearest to customer: to reduce delay
- Available services within region: some new regions may not support all services (might need to use from other regions -> slower)
- Price

## Availability zones

![[Cloud Practitioner Essentials 2025-01-13 08.35.12.excalidraw]]

- Each region contains multiple logically isolated zones that contain data centers of that region -> when an availability zone has a problem -> use other one to ensure the availability
- AZ(s) are connected by super-low latency connection

## Global content delivery - AWS Point of Presence

- Amazon CloudFront: is a CDN service provided by Amazon, put (cache) the content to Edge Location - nearer location from user -> increase speed
- AWS Outpost: Extend AWS infrastructure and services to your on-premises data center

---

# References

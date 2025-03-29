{{date}} {{time}}

Tags: [[AWS]] [[Cloud]] [[Security]]

---

- AWS provides comprehensive security services for protecting infrastructure and data
- Security is a shared responsibility between AWS and the customer

## Shared Responsibility Model

- **Customer responsible for:**

  - Customer data
  - Platform, applications, identity and access management
  - Operating system, network and firewall configuration
  - Client-side encryption
  - Server-side encryption
  - Network traffic protection

- **AWS responsible for:**
  - Hardware and AWS global infrastructure
  - Regions, Availability Zones, Edge Locations
  - Software infrastructure (compute, storage, database, networking)

## AWS Identity and Access Management (IAM)

- Manages access to AWS services and resources
- Key features:
  - IAM users - each with unique credentials
  - IAM policies - define permissions and actions
  - IAM roles - temporary access for services
  - IAM groups - collections of users with shared permissions
  - Multi-factor authentication (MFA)
  - Organizational units (OUs) for organizing accounts

## Authentication Mechanisms

- Password policy with configurable requirements
- Multi-factor authentication (MFA) options
  - Virtual MFA devices (Google Authenticator, Authy)
  - Universal 2nd Factor (U2F) Security keys
  - Hardware key fobs

## AWS Security Tools

- IAM Credential Reports for auditing
- IAM Access Advisor to monitor service usage
- AWS Web Application Firewall (WAF)
- AWS Shield for DDoS protection
- AWS Key Management Service (KMS)
- Amazon GuardDuty for threat detection

---

# References

- [[AWS Core Service Categories]]
- [[Amazon VPC]]

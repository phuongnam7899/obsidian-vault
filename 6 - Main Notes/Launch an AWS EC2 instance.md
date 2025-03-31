2025-03-31 21:06

Tags: [[AWS EC2]]

---

- Go to EC2 service console
- Go to "Instances"
- Click "Launch Instance"
- Fill info:
	- Name
	- Tags (Optional)
	- OS images
	- Instance type (t2.micro)
	- Create key pair to secure the instance
		- Key pair name
		- Key pair type (RSA/ED25519)
		- Private file format:
			- Win 7 & 8: `.ppk`
			- Others (Linux, MacOS, Win > 10): `.pem`
		- Network setting


---
# References
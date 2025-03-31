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
		- Storage setting
		- [[EC2 user data]] script, example:
```sh
#!/bin/bash
# Use this for your user data (script from top to bottom)
# install httpd (Linux 2 version)
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```


---
# References
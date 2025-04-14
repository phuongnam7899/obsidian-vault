2025-04-06 07:43

Tags: [[Networking]] [[Devops]]

---

![[Pasted image 20250406075057.png]]

> [!i] If using Windows <10, can use [[Putty]] instead

# How to?
## Windows 10
- Open `powershell`
- cd to the folder that contain key pair `.pem`/`.ppk` file (generated in [[Launch an AWS EC2 instance]]) 
- Run `ssh -i ./file_name.pem ec2-user@{PUBLIC_IP_OF_EC2_INTANCE}`

> [i] If cannot connect
> - Enter file's properties -> Security -> Advanced
> - Make sure the `Allow - SYSTEM - Full control` is delete (Disable inherritane)
> - Make sure current user has permission
> ![[Pasted image 20250406080831.png]]

---
# References
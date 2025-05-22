2025-05-09 10:10

Tags: 

---

# General info
- Check OS info:
```sh
cat /etc/os-release
```
- Check CPU architechture (`x86_64` / `aarch64`)
```sh
uname -m
```
- Check listening ports:
```sh
netstat -tulnp | grep LISTEN
```
# File management
- Check storage usage of items in a folder
```sh
du -sh ./*
```
- Copy all files in a folder to another
```sh
cp -r cd ./from-folder ./to-folder
```
- Move file/folder:
```sh
mv from_folder to_folder
```
- Delete file/folder
```sh
rm -rf path_to_folder
```

> [!i] `-r` mean recursive

- Unzip `tar.gz` file:
```sh
tar -xvf ./path-to-file 
```
- Zip folder:
```sh
tar -czvf output-file.tar.gz /path/to/folder
```
- Create folder:
```sh
mkdir -p ./folder-path
```
- Upload to Azure:
```
az storage blob upload --account-name fleetprodseadiagstrg --container-name code --name amq6 --file ./psa-amq-6.tar.gz --overwrite
```
- Transfer file to other VM:
```sh
scp file-name.tar.gz username@192.168.28.4:/home/usernamesud/
```
# Access management
- Create user group:
```sh
sudo groupadd fleetadmgrp -g 6097
```
- Create user
```sh
sudo useradd fleetadm -g 6097 -u 6043

sudo passwd fleetadm
```
- Change owner of file/folder:
```sh
sudo chown -R user_name:user_group ./folder_path
```

# Process management
- Find PID running in a port:
```sh
sudo lsof -i :61613
```
- Kill process by PID:
```sh
sudo kill 123123
```

> [!i] One line to find PID and kill by port: `sudo kill -9 $(sudo lsof -t -i :61613)`


---
# References
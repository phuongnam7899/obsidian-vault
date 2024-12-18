2024-12-18 08:09

Tags: [[Docker]]

---

## List all container

```sh
docker ps
```

## Build image from Dockerfile
```sh
docker build -t tag-name .
```
- `-t`: tag - give the image a tag to run later
- `.`: the path to the `Dockerfile`

## List all images
```sh
docker images
```

## Run a container from image
```sh
docker run -d --name [container_name] -p 1234:2345 [image_name]
```
- `-d`: run container in detached mode
- `--name`: give container a name
- `-p`: map port (1234) on the host machine to port (2345) of contaier
## Stop a running container
```sh
docker stop [contianer_name_or_id]
```


---
# References
# Docker
* [도커의 이해](https://subicura.com/2017/01/19/docker-guide-for-beginners-1.html)
* 하드웨어 가상화 없는 격리된 환경에서 실행되는 프로세스





# Docker Command

### Docker version check
```cmd
docker -v
```
### Docker Image Download
```cmd
docker pull {image-name}:{tag}
```
### Docker Image View
```cmd
docker images
```
### Create Docker Container
```cmd
docker create {option} {image-name}:{tag}
```

### Docker Container Running
```cmd
docker run {option} IMAGE{:tag|@digest} {command} {arg...}
```


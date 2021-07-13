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

* -d:	데몬으로 실행(뒤에서 - 안 보이는 곳(백그라운드)에서 알아서 돌라고 하기)
* -it:	컨테이너로 들어갔을 때 bash로 CLI 입출력을 사용할 수 있도록 해 줍니다.
* --name: {이름}	컨테이너 이름 지정
* -p: {호스트의 포트 번호}:{컨테이너의 포트 번호}	호스트와 컨테이너의 포트를 연결합니다.
* --rm:	컨테이너가 종료되면{내부에서 돌아가는 작업이 끝나면} 컨테이너를 제거합니다.
* -v: {호스트의 디렉토리}:{컨테이너의 디렉토리}	호스트와 컨테이너의 디렉토리를 연결합니다.

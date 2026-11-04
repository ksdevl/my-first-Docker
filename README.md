# 개발 워크스테이션 구축 미션



## 1. 프로젝트 개요

### 1-1. 미션 목표

본 프로젝트는 개발 환경 구축에 필요한 기본적인 도구와 기술을 직접 설치하고 실습하여 개발 워크스테이션의 기본적인 구성 및 운영 방법을 익히는 것을 목표로 한다.

### 1-2. 주요 수행 내용

- Windows 환경에서 개발 도구 및 터미널 사용
- Linux 기본 명령어와 파일 권한 관리
- Docker 이미지 및 컨테이너 생성·실행·관리
- Dockerfile을 활용한 커스텀 웹 서버 구축
- 바인드 마운트와 Docker Volume을 활용한 데이터 관리
- Git을 활용한 버전 관리 및 GitHub 연동
- 실습 과정과 결과를 README로 문서화

### 1-3. 최종 목표

개발 워크스테이션의 기본 구성 요소를 이해하고, Docker 기반의 웹 서버를 직접 구축하며, GitHub를 통해 프로젝트를 관리하고 공유할 수 있는 기본 역량을 확보한다.


## 2. 개발환경

| 항목 | 환경 |
|---|---|
| OS | Windows |
| Docker | Installed |
| Git | Installed |
| 개발 경험 | Beginner |
| 터미널 | PowerShell |
| 편집기 | VSCode |

### 2-1. PowerShell 버전 확인

실행 명령어:
```powershell
$PSVersionTable
```

실행 결과
```
Name                           Value                                                               
----                           -----                                                               
PSVersion                      5.1.19041.6456                                                      
PSEdition                      Desktop                                                             
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}                                             
BuildVersion                   10.0.19041.6456                                                     
CLRVersion                     4.0.30319.42000                                                     
WSManStackVersion              3.0                                                                 
PSRemotingProtocolVersion      2.3                                                                 
SerializationVersion           1.1.0.1              
```

### 2-2. Window 운영체제 확인

실행 명령어:
```powershell
systeminfo
```

실행 결과
```
OS 이름:                 Microsoft Windows 10 Home
OS 버전:                 10.0.19045 N/A 빌드 19045
OS 제조업체:             Microsoft Corporation
OS 구성:                 독립 실행형 워크스테이션
OS 빌드 종류:            Multiprocessor Free
등록된 소유자:           K'
시스템 제조업체:         Dell Inc.
시스템 모델:             G3 3779
시스템 종류:             x64-based PC
프로세서:                프로세서 1개 설치됨
                         [01]: Intel64 Family 6 Model 158 Stepping 10 GenuineIntel ~2208Mhz
BIOS 버전:               Dell Inc. 1.5.1, 2018-11-01
시스템 로캘:             ko;한국어
입력 로캘:               ko;한국어
표준 시간대:             (UTC+09:00) 서울
총 실제 메모리:          8,049MB
사용 가능한 실제 메모리: 1,748MB
```

### 2-3. git 버전 확인

실행 명령어:
```powershell
git --version
```

실행 결과
```
git version 2.56.0.windows.4
```

### 2-4. Docker 버전 확인

실행 명령어:
```powershell
docker --version
```

실행 결과
```
Docker version 29.9.2, build a82e528
```

### 2-5. Docker 클라이언트 및 서버 확인

실행 명령어:
```powershell
docker info
```

실행 결과
```
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.97.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     C:\Users\K'\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Users\K'\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     C:\Users\K'\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Users\K'\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.21
    Path:     C:\Users\K'\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     C:\Users\K'\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.40.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 3.755GiB
 Name: docker-desktop
 ID: 6844b9c5-907f-4a56-bf6f-aefe9f3f34b9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
```

## 3. 폴더/파일 생성 및 이동 등

### 3-1. 폴더 생성 및 확인

실행 명령어:
```
mkdir app
mkdir docker
mkdir docker-data
mkdir practice
mkdir logs
mkdir screenshots
Get-ChildItem
```

실행 결과
```
Mode                 LastWriteTime         Length Name                                             
----                 -------------         ------ ----                                             
d-----      2026-11-02   오후 2:55                app                                              
d-----      2026-11-02   오후 2:55                docker                                           
d-----      2026-11-02   오후 2:55                docker-data                                      
d-----      2026-11-02   오후 3:33                logs                                             
d-----      2026-11-02   오후 2:55                practice                                         
d-----      2026-11-02   오후 2:55                screenshots                                      
-a----      2026-11-02   오후 3:30           6405 README.md 
```

### 3-2. test폴더 생성 및 이동

실행 명령어:
```
mkdir test-folder
cd test-folder
pwd
cd ..
```

실행 결과
```

    디렉터리: C:\Users\K'\my-first-docker


Mode                 LastWriteTime         Length Name                                             
----                 -------------         ------ ----                                             
d-----      2026-11-02   오후 3:46                test-folder                                      

Drive        : C
Provider     : Microsoft.PowerShell.Core\FileSystem
ProviderPath : C:\Users\K'\my-first-docker\test-folder
Path         : C:\Users\K'\my-first-docker\test-folder
```

### 3-3. 파일 생성 및 내용 입력

실행 명령어:
```
New-Item practice.txt -ItemType File
Set-Content practice.txt "Hello, Codyssey!"
Get-Content practice.txt
```

실행 결과
```

    디렉터리: C:\Users\K'\my-first-docker


Mode                 LastWriteTime         Length Name                                             
----                 -------------         ------ ----                                             
-a----      2026-11-02   오후 3:55              0 practice.txt                                     
Hello, Codyssey!
```

### 3-4. 파일 복사, 이름 변경, 삭제

실행 명령어:
```
Copy-Item practice.txt practice-copy.txt
Rename-Item practice-copy.txt renamed-file.txt
Get-ChildItem
Remove-Item renamed-file.txt
```

실행 결과
```
 디렉터리: C:\Users\K'\my-first-docker


Mode                 LastWriteTime         Length Name                                             
----                 -------------         ------ ----                                             
d-----      2026-11-02   오후 2:55                app                                              
d-----      2026-11-02   오후 2:55                docker                                           
d-----      2026-11-02   오후 2:55                docker-data                                      
d-----      2026-11-02   오후 3:33                logs                                             
d-----      2026-11-02   오후 2:55                practice                                         
d-----      2026-11-02   오후 2:55                screenshots                                      
d-----      2026-11-02   오후 3:46                test-folder                                      
-a----      2026-11-02   오후 3:55             18 practice.txt                                     
-a----      2026-11-02   오후 3:56           9750 README.md                                        
-a----      2026-11-02   오후 3:55             18 renamed-file.txt   
```

## 4. Linux 파일 권한 관련

### 4-1. WSL 설치 여부 확인

실행 명령어:
```
powershell
wsl --list --verbose
```

실행 결과
```
 NAME              STATE           VERSION
* docker-desktop    Stopped         2
  Ubuntu            Stopped         2
  ```

### 4-2. Ubuntu 실행

실행 명령어:
```
wsl -d Ubuntu
```

실행 결과
```
ooooo@ks-11:/mnt/c/Users/K'/my-first-docker$ 
```

### 4-3. 실습 폴더 및 파일 생성

실행 명령어:
```
mkdir -p ~/mission-practice
cd ~/mission-practice
touch test.txt
ls -l
```

실행 결과
```
-rw-r--r-- 1 ooooo ooooo 0 Nov  3 13:01 test.txt
```

### 4-4. 파일 권한 변경

실행 명령어:
```
chmod 600 test.txt
ls -l test.txt
```

실행 결과
```
-rw------- 1 ooooo ooooo 0 Nov  3 13:01 test.txt
```

### 4-5. 파일 권한 변경2

실행 명령어:
```
chmod 700 test.txt
ls -l test.txt
```

실행 결과
```
-rwx------ 1 ooooo ooooo 0 Nov  3 13:01 test.txt
```

### 4-6. Ubuntu 실행 종료

실행 명령어:
```
exit
```

실행 결과
```
logout
```

## 5. Docker 활용 실습

### 5-1. Docker 엔진 상태 확인

실행 명령어:
```
powershell
docker info
```

실행 결과
```
Client:
 Version:    29.9.2
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.97.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     C:\Users\K'\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Users\K'\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Users\K'\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     C:\Users\K'\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Users\K'\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.21
    Path:     C:\Users\K'\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     C:\Users\K'\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     C:\Users\K'\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: nvidia runc io.containerd.runc.v2
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.40.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 12
 Total Memory: 3.755GiB
 Name: docker-desktop
 ID: 6844b9c5-907f-4a56-bf6f-aefe9f3f34b9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
 ```

### 5-2. 첫 번째 컨테이너 실행

실행 명령어:
```
docker run hello-world
```

실행 결과
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
d5e71e642bf5: Download complete 
Digest: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ```

### 5-3. Ubuntu 컨테이너 실행

실행 명령어:
```
docker run -it --name mission-ubuntu ubuntu:latest bash
```

실행 결과
```
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
f3f25b84a7d7: Pull complete 
edafa32f5d9e: Pull complete 
21594acc2d8b: Download complete 
Digest: sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11f4d3c
Status: Downloaded newer image for ubuntu:latest
```

### 5-4. 컨테이너 상태 확인

실행 명령어:
```
docker ps
docker ps -a
docker images
```

실행 결과
```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
CONTAINER ID   IMAGE           COMMAND    CREATED         STATUS                      PORTS     NAMES
8325a9987829   ubuntu:latest   "bash"     3 minutes ago   Exited (0) 43 seconds ago             mission-ubuntu
d03ce15efe5d   hello-world     "/hello"   7 minutes ago   Exited (0) 7 minutes ago              upbeat_mestorf
                                                                   i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c567b231f656       25.9kB         9.49kB    U   
ubuntu:latest        6a06111c3b0a        163MB         45.9MB    U   
```

### 5-5. 컨테이너 로그 및 관리

실행 명령어:
```
ddocker logs mission-ubuntu
docker start mission-ubuntu
docker stop mission-ubuntu
docker rm mission-ubuntu
```

실행 결과
```
root@8325a9987829:/# exit
exit
mission-ubuntu
mission-ubuntu
mission-ubuntu
```

### 5-6. attach와 exec 차이 확인

실행 명령어:
```
docker run -dit --name mission-test ubuntu:latest bash
```

실행 결과
```
bf5e6415efc3ea19c1136d9e78e82bd2a35eafeefce9943cd91f53d1c30eee5b
```

실행 명령어:
```
docker exec mission-test bash
```

실행 명령어:
```
docker attach mission-test
```

실행 결과
```
root@bf5e6415efc3:/# 
```
```
컨테이너에서 빠져나올때는 Ctrl + P를 누른 뒤 Ctrl + Q를 눌러서 컨테이너를 종료하지 않고 연결만 종료할 수 있음.
```

실행 명령어:
```
docker stop mission-test
docker rm mission-test
```

실행 결과
```
mission-test
mission-test
```

### 5-7. 기타 Docker 관리 명령어

실행 명령어:
```
docker stats --no-stream
docker inspect hello-world
docker system df
```

실행 결과
```
[
    {
        "Id": "sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef",        "RepoTags": [
            "hello-world:latest"
        ],
        "RepoDigests": [
            "hello-world@sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef"
        ],
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2026-03-23T21:33:59.562202219Z",
        "Config": {
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/hello"
            ],
            "WorkingDir": "/"
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 20399,
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:897b3f2a7c1bc2f3d02432f7892fe31c6272c521ad4d70257df624504a3238b4"
            ]
        },
        "Metadata": {
            "LastTagTime": "2026-11-03T04:21:10.749236658Z"
        },
        "Descriptor": {
            "mediaType": "application/vnd.oci.image.index.v1+json",
            "digest": "sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef",
            "size": 11062
        },
        "Identity": {
            "Pull": [
                {
                    "Repository": "docker.io/library/hello-world"
                }
            ]
        }
    }
]
TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          2         1         162.7MB   162.7MB (99%)
Containers      2         0         8.192kB   8.192kB (100%)
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
```

## 6. Dockerfile 작성 및 커스텀 웹 서버 구축

### 6-1. HTML 파일 작성

실행 명령어:
```
New-Item app/index.html -ItemType File
```

실행 결과
```

    디렉터리: C:\Users\K'\my-first-docker\app


Mode                 LastWriteTime         Length Name                                 
----                 -------------         ------ ----                                 
-a----      2026-11-03   오후 3:36              0 index.html       
```

실행 명령어: app/index.html을 열고 다음 내용을 입력
```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>내 첫번째 custom web server.</p>
    <p>Mission을 위한 첫단계!</p>
</body>
</html>
```

### 6-2. Dockerfile 작성

실행 명령어:
```
New-Item docker/Dockerfile -ItemType File
```

실행 결과
```
 디렉터리: C:\Users\K'\my-first-docker\docker


Mode                 LastWriteTime         Length Name                                 
----                 -------------         ------ ----                                 
-a----      2026-11-03   오후 3:43              0 Dockerfile 
```

실행 명령어:
```
notepad Dockerfile
```

실행 결과
```
메모장이 실행되면서 Dockerfile을 작성할 수 있음. 
```

실행 명령어: Dockerfile 메모장에 작성
```
FROM nginx:latest

COPY app/index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

실행 결과
```
파일 저장 시 아래와 같이 저장.
파일 이름: Dockerfile
파일 형식: 모든 파일
인코딩: UTF-8
확장자: 없음
```

### 6-3. Docker image build

실행 명령어:
```
docker build -t my-webserver:v1 -f Dockerfile .
```

실행 결과
```
[+] Building 16.3s (7/7) FINISHED                                  docker:desktop-linux
 => [internal] load build definition from Dockerfile                               0.0s
 => => transferring dockerfile: 123B                                               0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                    2.7s
 => [internal] load .dockerignore                                                  0.1s
 => => transferring context: 2B                                                    0.0s
 => [internal] load build context                                                  0.3s
 => => transferring context: 330B                                                  0.0s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:5ab5b0b01097420873a3f3330f44  8.6s
 => => resolve docker.io/library/nginx:latest@sha256:5ab5b0b01097420873a3f3330f44  0.1s
 => => sha256:a670537bed7086aeb8b663aad5e09cd584e19c6598cd2b6d905 1.40kB / 1.40kB  0.2s
 => => sha256:d322f1bf41d8e99dc47f550cbf85e79ca18bc45db12fd1b7a8b 1.21kB / 1.21kB  0.4s
 => => sha256:c139fe92686de21a8c49d9cb40415d1dddd95fbbee4d696cebe37693 0B / 404B  12.5s
 => => sha256:6e2ab1f3ef4e0ea3bbe1d208dfa048969199e3dab99e93c051b7c2d 964B / 964B  0.6s
 => => sha256:9f604dae09b216f6c87919d0e59d5a4ddc4387ef071cf63c645628f 628B / 628B  0.5s
 => => sha256:a071113ac575190a0fee0c046bcf51632356f07419bdffaa5 34.05MB / 34.05MB  2.8s
 => => sha256:6fc242d221a673263eabd14a9ad9584d3177c96e5cb504c89 29.86MB / 29.86MB  4.7s
 => => extracting sha256:6fc242d221a673263eabd14a9ad9584d3177c96e5cb504c891497338  1.0s
 => => extracting sha256:a071113ac575190a0fee0c046bcf51632356f07419bdffaa55798f54  0.8s
 => => extracting sha256:9f604dae09b216f6c87919d0e59d5a4ddc4387ef071cf63c645628f9  0.1s
 => => extracting sha256:6e2ab1f3ef4e0ea3bbe1d208dfa048969199e3dab99e93c051b7c2d0  0.1s
 => => extracting sha256:c139fe92686de21a8c49d9cb40415d1dddd95fbbee4d696cebe37693  0.1s
 => => extracting sha256:d322f1bf41d8e99dc47f550cbf85e79ca18bc45db12fd1b7a8b34bf7  0.1s
 => => extracting sha256:a670537bed7086aeb8b663aad5e09cd584e19c6598cd2b6d905c5f2f  0.1s
 => [2/2] COPY app/index.html /usr/share/nginx/html/index.html                     1.4s
 => exporting to image                                                             3.0s
 => => exporting layers                                                            0.4s
 => => exporting manifest sha256:9f2d3f5e2e7bf8dd6e79fa7ba34f7629c0985b3e0e3951d4  0.1s
 => => exporting config sha256:3258d7fc842b9aa46f094fcf345e9597c24db45413041303ac  0.1s
 => => exporting attestation manifest sha256:fd84825df51d004f72e31dd9b92312e17370  0.1s
 => => exporting manifest list sha256:114810bad59463c275cf3992078df7e7a7ada03a160  0.1s
 => => naming to docker.io/library/my-webserver:v1                                 0.0s
 => => unpacking to docker.io/library/my-webserver:v1         
 ```

 ### 6-4. 웹 서버 컨테이너 실행

실행 명령어:
```
docker run -d -p 8080:80 --name my-webserver-container my-webserver:v1
```

실행 결과
```
주소창에 http://localhost:8080를 입력하면 새 웹페이지가 뜨면서 설정했던 텍스트가 출력됨.
Hello, Docker!
내 첫번째 custom web server.
Mission을 위한 첫단계!
```

### 6-5. 웹 서버 컨테이너 검증

실행 명령어:
```
curl.exe http://localhost:8080
```

실행 결과
```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>내 첫번째 custom web server.</p>
    <p>Mission을 위한 첫단계!</p>
</body>
</html>
```

## 7. 바인드 마운트 실습

### 7-1. 기존 컨테이너 중지 및 삭제

실행 명령어: 실행중인 경우 같은 포트를 사용할 수 없음.
```
docker stop mission-bind
docker rm mission-bind
```

실행 결과
```
mission-bind
```

### 7-2. 바인드 마운트로 컨테이너 실행

실행 명령어: 
```
docker run -d --name mission-bind -p 8080:80 --mount "type=bind,source=$($PWD.Path)\app,target=/usr/share/nginx/html,readonly" nginx:latest
```

실행 결과
```
source=$($PWD.Path)\app,target=/usr/share/nginx/html,readonly" nginx:latest
093155c2852451300fd269540307f774ecf5fff45893da5cb9e9a8e9df4b93ca
```

### 7-3. HTML 파일 수정

## 8. Docker 볼륨을 이용한 데이터 영속성 실습

### 8-1. 볼륨 생성

실행 명령어: 
```
docker volume create mission-data
```

실행 결과
```
mission-data
```

### 8-2. 볼륨에 데이터 저장

실행 명령어: 
```
docker run -it --name volume-test -v mission-data:/data alpine sh
```

실행 결과
```
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
7b229517ed22: Pull complete 
3ec36f3670df: Download complete 
3da1513d2124: Download complete 
Digest: sha256:be2656061b536c1883c4034790e21d0a09c5aaaf51968b89368a3c0371ea2c9a
Status: Downloaded newer image for alpine:latest
```

실행 명령어: 컨테이너 내부에서 실행
```
echo "Docker Volume Persistence Test" > /data/test.txt
cat /data/test.txt
exit
```

실행 결과
```
Docker Volume Persistence Test
```

### 8-3. 컨테이너 삭제

실행 명령어: 
```
docker rm volume-test
```

실행 결과
```
volume-test
```

### 8-4. 새로운 컨테이너에서 데이터 확인

실행 명령어: 
```
docker run --rm -v mission-data:/data alpine cat /data/test.txt
```

실행 결과
```
Docker Volume Persistence Test
```

## 9. Git 및 Github 연동

### 9-1. Git 사용자 정보 확인

실행 명령어: 
```
git config --global user.name "ksdevl"
git config --global user.email "cela2323@google.com"
```

### 9-2. Gitignore 작성

실행 명령어: 
```
New-Item .gitignore -ItemType File
```

실행 결과
```
 디렉터리: C:\Users\K'\my-first-docker


Mode                 LastWriteTime         Length Name                                     
----                 -------------         ------ ----                                     
-a----      2026-11-04   오전 3:12              0 .gitignore  
```

### 9-3. Git 저장소 초기화

실행 명령어: 
```
New-Item .gitignore -ItemType File
```

실행 결과: 기존 프로젝트 폴더가 저장소로 지정되어 있어서, 다시 저장소로 지정함.
```
warning: re-init: ignored --initial-branch=main
Reinitialized existing Git repository in C:/Users/K'/my-first-docker/.git/
```

실행 명령어: Git 상태 확인
```
git status
```

실행 결과
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
        new file:   logs/terminal.md
        new file:   practice.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        Dockerfile
        app/
        docker/
```

### 9-4. 파일 등록 및 첫번째 커밋

실행 명령어: 
```
git add .
git status
git commit -m "First workstation mission"
```

실행 결과
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   .gitignore
        new file:   Dockerfile
        new file:   README.md
        new file:   app/index.html
        new file:   docker/Dockerfile
        new file:   logs/terminal.md
        new file:   practice.txt

[main (root-commit) 8d1ce94] First workstation mission
 7 files changed, 1046 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Dockerfile
 create mode 100644 README.md
 create mode 100644 app/index.html
 create mode 100644 docker/Dockerfile
 create mode 100644 logs/terminal.md
 create mode 100644 practice.txt
 ```

### 9-5. Github 저장소 생성

### 9-6. Github에 업로드

실행 명령어: 
```
git remote add origin https://github.com/ksdevl/my-first-Docker.git
git push -u origin main
```

실행 결과: 
```
numerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 12 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (13/13), 8.72 KiB | 2.18 MiB/s, done.
Total 13 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/ksdevl/my-first-Docker.git
   51a4285..898e245  main -> main
branch 'main' set up to track 'origin/main'.
```

### 9-7. 수정사항 업로드

실행 명령어: 
```
git add .
git commit -m "Update mission documentation"
git push
```

## 10. 최종 Reame 및 증거자료 정리

### 10-1. 최종 폴더 구조

실행 결과
```
![폴더구조](images/폴더구조.png)
```




## Troubleshooting 

### 1. Github에 업로드

실행 명령어: 
```
git remote add origin https://github.com/ksdevl/my-first-Docker.git
git push -u origin main
```

실행 결과: 기존 readme 저장소가 있어서 발생
```
error: remote origin already exists.
To https://github.com/ksdevl/my-first-Docker
 ! [rejected]        main -> main (fetch first)
hint: have locally. This is usually caused by another repository pushing to
hint: the same ref. If you want to integrate the remote changes, use
hint: 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

실행 명령어: 저장소를 다시 세팅
```
git remote set-url origin https://github.com/ksdevl/my-first-Docker.git
```

실행 명령어: 수정되었는지 확인
```
git remote -v
```

실행 결과: 
```
origin  https://github.com/ksdevl/my-first-Docker.git (fetch)
origin  https://github.com/ksdevl/my-first-Docker.git (push)
```

실행 명령어: 원격 저장소의 변경사항을 가져오고, 별개로 시작한 저장소의 이력을 병합하도록 허용
```
git pull origin main --allow-unrelated-histories
```

실행 결과: 
```
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 880 bytes | 29.00 KiB/s, done.
From https://github.com/ksdevl/my-first-Docker
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
Auto-merging README.md
CONFLICT (add/add): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

실행 명령어: Readme를 로컬파일 기준으로 선택
```
git checkout --ours README.md
```

실행 결과: 
```
Updated 1 path from the index
```

실행 명령어: 충돌 해결 및 병합 커밋 생성
```
git add README.md
git commit -m "Resolve merge conflict using local README"
```

실행 결과: 
```
[main 898e245] Resolve merge conflict using local README
```

실행 명령어: Github에 업로드
```
git push -u origin main
```

실행 결과: 
```
numerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 12 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (13/13), 8.72 KiB | 2.18 MiB/s, done.
Total 13 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/ksdevl/my-first-Docker.git
   51a4285..898e245  main -> main
branch 'main' set up to track 'origin/main'.
```
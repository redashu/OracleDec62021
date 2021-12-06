##  Training Plan 

<img src="plan.png">

### apps to test and deploy 

<img src="apps.png">

## problems 

### app libs comptability 

<img src="app1.png">

### intro to hypervisors {virtaulization}

<img src="vm.png">

### vm problem 1 

<img src="vmprob1.png">

### vm problem 2 

<img src="vmprob2.png">

## WElcome to CRE (Container runtime Engines)

<img src="cre1.png">

### CRE 

<img src="cre2.png">

### CRE vs hypervisor 

<img src="crevshyper.png">

### Docker as CRE 

<img src="docker.png">

### Installing docker 

<img src="dinstall.png">

### Docker Desktop for MAC 

[INstalllink](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

### Docker Desktop for windows 10 / 11 

### checking after installation 

```
docker  -v 
Docker version 20.10.8, build 3967b7d
 fire@ashutoshhs-MacBook-Air  ~  docker  version 
Client:
 Cloud integration: 1.0.17
 Version:           20.10.8
 API version:       1.41
 Go version:        go1.16.6
 Git commit:        3967b7d
 Built:             Fri Jul 30 19:55:20 2021
 OS/Arch:           darwin/amd64
 Context:           default
 Experimental:      true

Server: Docker Engine - Community
 Engine:
  Version:          20.10.8
  API version:      1.41 (minimum version 1.12)
  Go version:       go1.16.6
  Git commit:       75249d8
  Built:            Fri Jul 30 19:52:31 2021
  OS/Arch:          linux/amd64

```

### Install in Linux Host : centos / rhel / OL 

```
 yum  install docker -y
Loaded plugins: extras_suggestions, langpacks, priorities, update-motd
Resolving Dependencies
--> Running transaction check
---> Package docker.x86_64 0:20.10.7-5.amzn2 will be installed
--> Processing Dependency: runc >= 1.0.0 for package: docker-20.10.7-5.amzn2.x86_64
--> Processing Dependency: libcgroup >= 0.40.rc1-5.15 for package: docker-20.10.7-5.a
mzn2.x86_64
--> Processing Dependency: containerd >= 1.3.2 for package: docker-20.10.7-5.amzn2.x8
6_64
--> Processing Dependency: pigz for package: docker-20.10.7-5.amzn2.x86_64
--> Running transaction check
---> Package containerd.x86_64 0:1.4.6-7.amzn2 will be installed
---> Package libcgroup.x86_64 0:0.41-21.amzn2 will be installed
---> Package pigz.x86_64 0:2.3.4-1.amzn2.0.1 will be installed
---> Package runc.x86_64 0:1.0.0-2.amzn2 will be installed
--> Finished Dependency Resolution

```


### Starting docker engine service 

```
 systemctl enable --now docker 
Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /u
sr/lib/systemd/system/docker.service.
[root@ip-172-31-93-168 ~]# systemctl status docker 
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; enabled; vendor preset: di
sabled)
   Active: active (running) since Mon 2021-12-06 06:11:53 UTC; 9s ago
     Docs: https://docs.docker.com
  Process: 3232 ExecStartPre=/usr/libexec/docker/docker-setup-runtimes.sh (code=exite
d, status=0/SUCCESS)
  Process: 3215 ExecStartPre=/bin/mkdir
  
 ```
  
 ### adding non root user in linux Host 
 
 ```
  5  useradd  test 
    6  usermod -aG docker test 
    7  echo "OracleDocker088"  |  passwd test --stind 
    
 ```
 
 ### Docker lab setup 
 
 <img src="lab.png">
 
### Docker ENgine / server 

<img src="dengine.png">

### Docker client and server 

<img src="server.png">

###  Container required docker images 

<img src="dimg.png">

### Imgae registry like Docker hub 

### Docker client operations 

### checking local server images 

```
 docker   images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
[test@ip-172-31-93-168 ~]$ 


```

### pulling image from docker hub to docker engine server 

```
$ docker   images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
[test@ip-172-31-93-168 ~]$ docker  pull  openjdk 
Using default tag: latest
latest: Pulling from library/openjdk
28587b6e6475: Pull complete 
b1655352c888: Pull complete 
1f9646f00e96: Pull complete 
Digest: sha256:0e5ae79482731eef1526afb4e3a42e62b38142681c5752a944ff4236da979648
Status: Downloaded newer image for openjdk:latest
docker.io/library/openjdk:latest
[test@ip-172-31-93-168 ~]$ 
[test@ip-172-31-93-168 ~]$ docker   images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
openjdk      latest    1b3756d6df61   2 weeks ago   471MB

```

### final docker images 

```
docker  images
REPOSITORY    TAG       IMAGE ID       CREATED       SIZE
mysql         latest    bbf6571db497   3 days ago    516MB
alpine        latest    c059bfaa849c   11 days ago   5.59MB
openjdk       latest    1b3756d6df61   2 weeks ago   471MB
oraclelinux   8.5       fa4253e97227   2 weeks ago   235MB

```

### pulling images from QYay 

```
$ docker pull quay.io/bitnami/tomcat  
Using default tag: latest
latest: Pulling from bitnami/tomcat
1d7019cad1df: Pull complete 
a30ebf93a11a: Pull complete 
20a11b4e2b3b: Pull complete 
8c1997a505fe: Pull complete 
65fdfb1b53db: Pull complete 

```

### pulling from non cloud oralce public registry 

```
 docker pull container-registry.oracle.com/java/openjdk:latest
latest: Pulling from java/openjdk
0b3f7bc5b3d7: Pull complete 
7ba4be1f9aef: Pull complete 
793b9263010a: Pull complete 
Digest: sha256:294490452d9030fdcb85a9ccd74e48bdacca8b028d022dc6700b56c82d746bed
Status: Downloaded newer image for container-registry.oracle.com/java/openjdk:latest

```

### on the docker server side images storage location 

<img src="dst.png">



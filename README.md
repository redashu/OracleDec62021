# Training Plan 

<img src="plan.png">

## Docker CE components 

<img src="dockerce.png">

### Docker clients 

<img src="cli.png">


### Portainer 

```
docker  run  -d --name webui -p 9000:9000 --restart always  --memory 500M --cpu-shares=30       -v  /var/run/docker.sock:/var/run/docker.sock  portainer/portainer 
Unable to find image 'portainer/portainer:latest' locally
latest: Pulling from portainer/portainer
94cfa856b2b1: Pull complete 
49d59ee0881a: Pull complete 
a2300fd28637: Pull complete 
Digest: sha256:fb45b43738646048a0a0cc74fcee2865b69efde857e710126084ee5de9be0f3f
Status: Downloaded newer image for portainer/portainer:latest
0b6b355dcaa8ea041d6aa3f8565e216f60541e8ab3631e55b5cd27bd2c7a6279
[test@ip-172-31-93-168 ashu_images]$ 
[test@ip-172-31-93-168 ashu_images]$ docker ps
CONTAINER ID   IMAGE                 COMMAND        CREATED         STATUS         PORTS                                       NAMES
0b6b355dcaa8   portainer/portainer   "/portainer"   5 seconds ago   Up 3 seconds   0.0.0.0:9000->9000/tcp, :::9000->9000/tcp   webui

```




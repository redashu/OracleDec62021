# Training Plan 

<img src="plan.png">

### k8s REvision 

<img src="rev.png">

### k8s master node components 

<img src="compo.png">

### Understanding POD 

<img src="pod.png">

### POd explanation 

```
kubectl  explain  pod
KIND:     Pod
VERSION:  v1

DESCRIPTION:
     Pod is a collection of containers that can run on a host. This resource is
     created by clients and scheduled onto hosts.

FIELDS:
   apiVersion	<string>
     APIVersion defines the versioned schema of this representation of an
     object. Servers should convert recognized schemas to the latest internal
     value, and may reject unrecognized values. More info:
     https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources

   kind	<string>
     Kind is a string value representing the REST resource 
     
     
```

### First POd Info 

```
apiVersion: v1 # apiversion running on master node related to POD request 
kind: Pod
metadata: # info about Kind {Pod}
 name: ashupodx1 # name of Kind {POd}
spec: # is about application info like container / storage / security -etc
 containers: # one or more containers 
 - name: ashuc1
   image: alpine123344 
   command: ['sh','-c','ping google.com'] 
   
   
```

### Delete all the POds 

```
kubectl delete pods --all    
pod "aishpod-1" deleted
pod "aishpodx1" deleted
pod "ashupod-1" deleted
pod "chetabpod-1" deleted
pod "harikapod-1" deleted
pod "juhipod-1" deleted

```

### creating first pod 

```
kubectl apply -f  newpod.yaml 
pod/ashupodx1 created
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl get  pods
NAME         READY   STATUS             RESTARTS   AGE
aishpodx1    1/1     Running            0          27s
ashupodx1    0/1     ImagePullBackOff   0          13s
sunilpodx1   0/1     ErrImagePull       0          35s

```

### Note: Image name or access is leading to both the problem -- ImagePullBackOff , ErrImagePull

### get the details about internal things 

```
kubectl describe pod ashupodx1 
Name:         ashupodx1
Namespace:    default
Priority:     0
Node:         minion1/172.31.64.197
Start Time:   Thu, 09 Dec 2021 10:37:00 +0530
Labels:       <none>
Annotations:  cni.projectcalico.org/containerID: 1f4a508816aa346963569100fbb4bb5be3ab48d1ef0ceb926b3e2c80832a35b4
              cni.projectcalico.org/podIP: 192.168.34.36/32
              cni.projectcalico.org/podIPs: 192.168.34.36/32
Status:       Pending
IP:           192.168.34.36
IPs:
  IP:  192.168.34.36
Containers:

```

### access container shell running inside POD 

```
kubectl exec -it  ashupodx1  -- sh
/ # cat  /etc/os-release 
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.15.0
PRETTY_NAME="Alpine Linux v3.15"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://bugs.alpinelinux.org/"
/ # ps -e
PID   USER     TIME  COMMAND
    1 root      0:00 ping google.com
    7 root      0:00 sh
   15 root      0:00 ps -e
/ # exit

```


# Training Plan 

<img src="plan.png">

## Revision 

<img src="rev.png">

## Intro to secret resources in k8s 

<img src="sec.png">

### creating secret in our namespace 

```
kubectl config get-contexts 
CURRENT   NAME                          CLUSTER      AUTHINFO           NAMESPACE
*         kubernetes-admin@kubernetes   kubernetes   kubernetes-admin   ashu-space
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get secret 
NAME                  TYPE                                  DATA   AGE
default-token-rgxvk   kubernetes.io/service-account-token   3      22h
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl create secret 
Create a secret using specified subcommand.

Available Commands:
  docker-registry Create a secret for use with a Docker registry
  generic         Create a secret from a local file, directory, or literal value
  tls             Create a TLS secret


```

### ocr secret in k8s 

```
kubectl create secret  docker-registry  ashuocr       --docker-server=phx.ocir.io   --docker-username="tg8judkl/techbyme@gmail.com" --docker-password="M3drv7P#ejvX"
```

### apply nw changes 

```
kubectl replace -f ocr.yaml --force 
pod "ashupodx1" deleted
pod/ashupodx1 replaced
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get  pod
NAME        READY   STATUS    RESTARTS   AGE
ashupodx1   1/1     Running   0          10s

```

## ReplicationController 


<img src="rc.png">

### RC YAML 

```
apiVersion: v1
kind: ReplicationController
metadata:
 name: ashurc-1 
spec:
 replicas: 1 # number of pod we want 
 template: # rc will be using template to create PODs 
  metadata:
   labels: # label of pod 
    x: helloashutoshh1
  spec:
   containers:
   - image: dockerashu/oraclenode:v1
     name: ashuc1 
     ports:
     - containerPort: 3000


```

### deploy 

```
kubectl apply -f  ashurc1.yaml 
replicationcontroller/ashurc-1 created
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get  rc
NAME       DESIRED   CURRENT   READY   AGE
ashurc-1   1         1         1       5s
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get  po              
NAME             READY   STATUS    RESTARTS   AGE
ashurc-1-l5jdg   1/1     Running   0          22s
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get  po --show-labels
NAME             READY   STATUS    RESTARTS   AGE   LABELS
ashurc-1-l5jdg   1/1     Running   0          34s   x=helloashutoshh1

```

### creating service using expose method 

```
kubectl get  rc
NAME       DESIRED   CURRENT   READY   AGE
ashurc-1   1         1         1       3m27s
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  expose  rc  ashurc-1  --type NodePort --port 3000   --name  ashusvc1  
service/ashusvc1 exposed
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl  get  po --show-labels
NAME             READY   STATUS    RESTARTS   AGE   LABELS
ashurc-1-r4qqw   1/1     Running   0          2m    x=helloashutoshh1
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl get  svc -o wide
NAME       TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE   SELECTOR
ashusvc1   NodePort   10.108.134.125   <none>        3000:30124/TCP   27s   x=helloashutoshh1

```
### manual scaling of the POd using RC 

```

kubectl  scale rc  ashurc-1  --replicas=3
replicationcontroller/ashurc-1 scaled
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl get  pod                         
NAME             READY   STATUS    RESTARTS   AGE
ashurc-1-4nsgg   1/1     Running   0          3s
ashurc-1-r4qqw   1/1     Running   0          5m23s
ashurc-1-x9crg   1/1     Running   0          3s
 fire@ashutoshhs-MacBook-Air  ~/Desktop/k8sapps  kubectl get  pod -o wide
NAME             READY   STATUS    RESTARTS   AGE     IP                NODE      NOMINATED NODE   READINESS GATES
ashurc-1-4nsgg   1/1     Running   0          18s     192.168.34.60     minion1   <none>           <none>
ashurc-1-r4qqw   1/1     Running   0          5m38s   192.168.179.218   minion2   <none>           <none>
ashurc-1-x9crg   1/1     Running   0          18s     192.168.179.225   minion2   <none> 

```


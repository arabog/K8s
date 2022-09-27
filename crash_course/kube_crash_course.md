# Kubernetes Crash Course for Absolute Beginners [NEW]
## A. Introuction to Kubernetes
Kubernetes is an open source container orchestration(or managemt) tool developed by Google. It helps to manage conternerized applications (made up of numerous containers) in diff deploymt environments .    

### What problems does Kubernetes solve?
Trend from Monolith to Microservices  
Increased usage of containers  
Demand for a proper way of managing those hundreds of containers  

### Features Orchestration tools offer
High availability or no downtime  
Scalability or high performance  
Disaster recovery - backup and restore  

## B. Kubernetes Architecture
It cluster is md up of atleast one Master Node(Virtual or phy machine) and connected to this are a couple of Worker nodes(mostly called NODES). Each NODE  has a kubelet(pry node agt) process running on it, wc mks it possible for d clusters to talk to each other and execute sm tasks on those nodes i.e running sm processes.  
Each worker nodes have diff num of containers working on dm. Applicatns r mainly running on worker nodes while Master nodes run several Kubernetes(K8s) processes necessary to run and manage clusters properly an example is an **API server** wc is also a container and an entrypt to K8s cluster. It is d process diff K8s clusters will talk to. UI, API, command line tool will all talk to API server.

Anoda th running on Master node is **Controller Manager** wc keeps track of what is happening in the cluster weda smth needs to be repaired, or a container died and needed to be restarted.  
**Scheduler** ensures Pods placemt. It decides on wc Node new Pod(container) shd be scheduled.  
**etcd** key-value storage. it's d kubernetes backing store. It holds d current state of d K8s clusters. It has all d configuratn data inside and the state of each node and container.    
**Virtual Network** spans all d nodes that are part of the cluster. It turns all d nodes in d cluster into one unified powerful machine.  

Worker nodes because dy contain d applicatns av higher workload and much bigger and more resources.  
Master nodes wc is the control plane nodes av a handful of master processes and it is much more important than worker nodes.  

## C. Main Kubernetes Components
**Pod**  
It is d smallest unit in K8s.  
An abstratn over container.  
Usually 1 application per Pod.  
Each pod gets its own IP address wc it uses to communicate.  
Pod can die at any time with d creatn of new IP address wc can affect communicatn and bcos of ds Service is used.  

**Service**  
Enable permanent IP address dt can be assign to each pod.  
Hence, for eg d app (e.g my-app) will have its own service while d db will have its own service.  
Lifecycle of Pod and Service are not connected i.e if d pod dies d service persisted.  
Service is also a loadbalancer.  

External Service  
Enable communicatn from external sources like internet bcos app shd be accessible via browser.  
Internal Service  
Helps to prevent external sources from talking to some components of the network e.g db.  

Hence, it is impt to specify d type of Service on cr8n. Internal Service is d default type.  
 
**Ingress**  
Receives d request from external sources and dn forward it to d Service.  

<!-- ========================================== -->
**ConfigMap**  
DB URL is usu in d built application! So if d URL shd change, u'll need to 
Re-build  
Push it to repo  
Pull it into ur Pod  
To prevent dse steps, K8s uses ConfigMap, wc stores d external configuratn of d applicatn such as DB URL, password, username etc. It is directly connected to d pod meaning d pod gets d changes being made.  

**Secret**  
used to store secret data in base 64 format. It is referenced in Deploymt/Pod.  
Use it as environmt variables or as a ppties file.  

K8s Secrets r, by default, stored unencrypted in d API server's undelying data store (etcd). Any1 with API access can retrieve or modify a Secret, and so can anyone with access to etcd. Also, any1 who is authorized to cr8 a Pod in a namespace can use dt access to read any Secret in dt namespace; ds includes indirect access such as d ablitily to cr8 a Deploymt.  

In order to safely use Secrets, take at least the ffg steps:  
1. Enable Encryption at Rest for Secrets.  
2. Enable or configure RBAC rules dt restrict reading data in Secrets(including via indirect means).  
3. Where appropriate, also use mechanism such as RBAC to limit which principal r allowed to cr8 new Secrets or replace existing ones.  

**Volume**  
Used to persist data in database even if d db is destroyed. It can be storage on local machine or remote, outside of d k8s cluster.  
Data Storage: can be done either locally or remotely. both r external to d K8s cluster bcos K8s doesn't manage data persistence!     


<!-- ========================================== -->
**Deployment**  
Now dt d application is running and can be access via browser, wt happens if d app dies?  



**StatefulSet**  



<!-- ========================================== -->

**DaemonSet**  


## D. Local Setup


## E. Demo Project


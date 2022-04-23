## Source && reference:
- https://kubernetes.io/docs/tutorials/kubernetes-basics/explore/explore-intro/
- https://github.com/thangtq710/Kubernetes
- 
## no idea about title:
- K8S is the most popular container orchestration, docker is container runtime.
- It has 2 major component: master node and worker node.
- The important thing in k8s cluster is ETCD: it is DB storage for k8s cluster
- The common basic concept we need to know when working with in k8s is: pod, deployment, service. They are basic resource we need to learn for begin 

## Pod:
A Pod is a group of one or more application containers (such as Docker) and includes shared storage (volumes), IP address and information about how to run them. Containers of pod can run in same server only.

![image](https://user-images.githubusercontent.com/3434274/142842540-e15529f8-a83c-4ce8-8019-080d7ca8f98c.png)

### Deployment:
- When deploy service, we can use deployment or daemonset, but most common is deployment. 

![image](https://user-images.githubusercontent.com/3434274/164888637-59d37cfc-5435-45c5-8eb3-9e344bad6025.png)

- When we declare deployment with replica set is 3. The component controller manager in master it will commands deploy 3 pods as replica is 3 and interact with worker via kubelet, after that kubelet will use to deploy pods, run pods in containers. For able to run it, it use container runtime, specific is Docker!. 

### Service: 
- Used to connect traffic betwen pods in k8s cluster or connect service/ application from outside to inside k8s cluster. 

![image](https://user-images.githubusercontent.com/3434274/164889073-2825c470-7fc7-41b3-bb51-d761efeb1db1.png)

- Default, when deploy some deployments it will create a service called Cluster IP ( it is default service in k8s, pods in there will interact with each other via service name of that cluster IP. Mainly use for internal interact!

![image](https://user-images.githubusercontent.com/3434274/164889028-114b124e-4b25-4758-837c-8e4f20540c06.png)

for picture above: It used to know as load balancer for pod, when traffic go in service 1 with label is nginx,then it will forward al traffic to pod that has label nginx. 

- Next is node port:
![image](https://user-images.githubusercontent.com/3434274/164889207-a272c20d-4e88-441f-b748-15e6eb78c58e.png)
It used to run when service from outside call / interact with pod inside k8s cluster. Specify of node port is we can call port 30001 in any node even that pod isn't running on that node. For achieved it, it will create a rule iptable, it will NAT and forward port 30001 to all node of that k8s cluster.


## Node:
![image](https://user-images.githubusercontent.com/3434274/142842596-a419ebe9-abfb-4749-b96c-e79ec470cf05.png)

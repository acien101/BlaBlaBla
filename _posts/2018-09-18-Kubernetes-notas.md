---
layout: post
published: true
title: Notas Kubernetes
---

Esto son algunas notas de lo que voy aprendiendo de Kubernetes



---

Hay una herramienta para testear kubernetes en local que te monta un máquina virtual. [minikube](https://github.com/kubernetes/minikube)


Kubeadm solves the problem of handling TLS encryption configuration, deploying the core Kubernetes components and ensuring that additional nodes can easily join the cluster. [Kubeadm](https://github.com/kubernetes/kubeadm)


Para crear redes de dockers que se puedan descubrir automáticamente:
[Weave Net](https://www.weave.works/docs/net/latest/overview/)
---

The cluster can be interacted with using the kubectl CLI

Details of the cluster and its health status can be discovered via
```
kubectl cluster-info
```

To view the nodes in the cluster using
```
kubectl get nodes
```

With a running Kubernetes cluster, containers can now be deployed.

Using kubectl run, it allows containers to be deployed onto the cluster -
```
kubectl run first-deployment --image=katacoda/docker-http-server --port=80
```

The status of the deployment can be discovered via the running Pods -
```
kubectl get pods
```

Once the container is running it can be exposed via different networking options, depending on requirements. One possible solution is NodePort, that provides a dynamic port to a container.
```
kubectl expose deployment first-deployment --port=80 --type=NodePort
```
The command below finds the allocated port and executes a HTTP request.
```
export PORT=$(kubectl get svc first-deployment -o go-template='{{range.spec.ports}}{{if .nodePort}}{{.nodePort}}{{"\n"}}{{end}}{{end}}')
echo "Accessing host01:$PORT"
curl host01:$PORT
```
The results is the container that processed the request.

The Kubernetes dashboard allows you to view your applications in a UI. In this deployment, the dashboard has been made available on port 30000.

---

#### Ussing Kubeadm

etcd is a consistent and highly-available key value store used as Kubernetes’ backing store for all cluster data.

The first stage of initialising the cluster is to launch the master node. The master is responsible for running the control plane components, etcd and the API server. Clients will communicate to the API to schedule workloads and manage the state of the cluster.

The command below will initialise the cluster with a known token to simplify the following steps.

```
kubeadm init --token=102952.1a7dd4cc8d1f4cc5 --kubernetes-version $(kubeadm version -o short)
```

In production, it's recommend to exclude the token causing kubeadm to generate one on your behalf.

Once the Master has initialised, additional nodes can join the cluster as long as they have the correct token. The tokens can be managed via kubeadm token, for example

```
kubeadm token list
```

**Recomiendo leer kubeadm join --help**

Ejemplo de kubeadm join

On the second node, run the command to join the cluster providing the IP address of the Master node.

```
kubeadm join --discovery-token-unsafe-skip-ca-verification --token=102952.1a7dd4cc8d1f4cc5 172.17.0.93:6443
```

**Para saber los nodos, nos vamos al cluster master**

```
kubectl get nodes
```

**At this point, the Nodes will not be ready.**

This is because the Container Network Interface has not been deployed. This will beUsing Kubectl, it's possible to deploy pods. Commands are always issued for the Master with each node only responsible for executing the workloads.

The command below create a Pod based on the Docker Image katacoda/docker-http-server. fixed within the next step.

The Container Network Interface (CNI) defines how the different nodes and their workloads should communicate. There are multiple network providers available, some are listed [here](https://kubernetes.io/docs/concepts/cluster-administration/addons/).

Using Kubectl, it's possible to deploy pods.

The command below create a Pod based on the Docker Image katacoda/docker-http-server.

```
kubectl run http --image=katacoda/docker-http-server:latest --replicas=1
```

Once running, you can see the Docker Container running on the (other) node.

```
docker ps | grep docker-http-server
```

---

### Start containers using Kubectl

This deployment is issued to the Kubernetes master which launches the Pods and containers required. Kubectl run_ is similar to docker run but at a cluster level.

The format of the command is kubectl run <name of deployment> <properties>

The following command will launch a deployment called http which will start a container based on the Docker Image katacoda/docker-http-server:latest.

```
kubectl run http --image=katacoda/docker-http-server:latest --replicas=1
```

You can then use kubectl to view the status of the deployments

```
kubectl get deployments
```

To find out what Kubernetes created you can describe the deployment process.

```
kubectl describe deployment http
```

The description includes how many replicas are available, labels specified and the events associated with the deployment. These events will highlight any problems and errors that might have occurred.

Use the following command to expose the container port 80 on the host 8000 binding to the external-ip of the host.

```
kubectl expose deployment http --external-ip="172.17.0.58" --port=8000 --target-port=80
```

You will then be able to ping the host and see the result from the HTTP service.

```
curl http://172.17.0.58:8000
```

With kubectl run it's possible to create the deployment and expose it as a single command.

```
kubectl run httpexposed --image=katacoda/docker-http-server:latest --replicas=1 --port=80 --hostport=8001
```

**BRAINDEAD**

With our deployment running we can now use kubectl to scale the number of replicas.

Scaling the deployment will request Kubernetes to launch additional Pods. These Pods will then automatically be load balanced using the exposed Service.

The command kubectl scale allows us to adjust the number of Pods running for a particular deployment or replication controller.

```
kubectl scale --replicas=3 deployment http
```

Listing all the pods, you should see three running for the http deployment kubectl get pods

Once each Pod starts it will be added to the load balancer service. By describing the service you can view the endpoint and the associated Pods which are included.

```
kubectl describe svc http
```

Making requests to the service will request in different nodes processing the request.

```
curl http://172.17.0.58:8000
```
![BrainDEAD](../images/kubernetes-screenshot.png)

---

#### Deploy containers using YAML

Example of a yaml:

```

apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: webapp1
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: webapp1
    spec:
      containers:
      - name: webapp1
        image: katacoda/docker-http-servesvcr:latest
        ports:
        - containerPort: 80

```

This is deployed to the cluster with the command

```
kubectl create -f deployment.yaml
```

As it's a Deployment object, a list of all the deployed objects can be obtained via

```
kubectl get deployment
```

Details of individual deployments can be outputted with

```
kubectl describe deployment webapp1
```

Get service deployed

```

kubectl get svc

```

Creating a Nodeport service

```
apiVersion: v1
kind: Service
metadata:
  name: webapp1-svc
  labels:
    app: webapp1
spec:
  type: NodePort
  ports:
  - port: 80
    nodePort: 30080
  selector:
    app: webapp1
```

Deploy as:

```
kubectl create -f service.yaml
```

Get details of the service
```
kubectl describe svc webapp1-svc
```

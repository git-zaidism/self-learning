# What is Kubernetes?

- Kubernetes is a free, open-source tool that helps manage and organize containers (small, self-contained software units).
- It automates tasks like deploying, scaling, and managing these containers.

## Key Points:

- Kubernetes is often shortened to k8s.
- It was created by Google and is now maintained by the Cloud Native Computing Foundation (CNCF).
- It’s built using the Go programming language.

Kubernetes also helps with:

- **Container management**: Deploying, scheduling, scaling, and balancing the load across containers.

## Why do we need Kubernetes?

In real-time applications, managing many containers (small, self-contained pieces of software) can become very complex. Kubernetes solves this problem by automating and simplifying tasks like:

1. **Deploying containers**: It makes it easier to launch your containers on any machine, anywhere.
2. **Scaling containers**: If your app becomes more popular and needs more resources, Kubernetes can automatically add more containers to handle the load.
3. **Managing failures**: If a container stops working, Kubernetes will automatically restart it or replace it with a new one, ensuring your app stays up and running.
4. **Load balancing**: Kubernetes ensures that traffic is spread evenly across containers, so no single container is overloaded.

## What problem does Kubernetes solve in real-time apps?

- **Handling large-scale apps**: It helps manage many containers, especially when your app grows and you need to manage thousands of them.
- **Efficiency and uptime**: It keeps your app running smoothly by automatically fixing issues, balancing traffic, and scaling resources as needed.
- **Reducing manual work**: Kubernetes removes the need for manual intervention to manage containers, saving time and reducing human error.

In simple terms, Kubernetes makes it easier to run and manage apps at scale, ensuring they stay reliable, efficient, and available.

---

# Key Kubernetes Components:

## 1. Pod:
- The smallest unit in Kubernetes. A pod can have one or more containers that share the same resources (like storage and network). Each POD has a unique IP.

## 2. Node:
- A physical or virtual machine that runs applications in Kubernetes or a single/collection of Pods into a single unit is called Node. It contains the Kubelet (manages containers) and Kube Proxy (handles networking).

## 3. Cluster:
- A group of nodes (machines) that work together to run your applications. A Kubernetes cluster consists of a master node (control plane) and worker nodes (where containers run).

## 4. Deployment:
- A higher-level Kubernetes object used to manage updates to your applications. It ensures that the right number of pods are running and can handle updates and rollbacks smoothly.

## 5. Secrets:
- Kubernetes stores sensitive data like passwords or API keys in Secrets to keep them secure and separate from your application code.

## 6. ConfigMap:
- A way to store non-sensitive configuration data that your application can access during runtime. It's a way to decouple configuration from the application code.

## 7. etcd:
- A distributed key-value store used by Kubernetes to store all cluster data, including configuration and state information. It ensures that Kubernetes can retrieve and update the configuration at any time. Max limit 1MB.

## 8. ReplicaSet:
- Ensures that a specified number of identical pod replicas are running at all times. If a pod goes down, it creates a new one to replace it with a new IP address.

## 9. Services:
- A way to expose an application running in a set of pods to the outside world or other parts of the cluster. It helps in load balancing and stable network communication.

## 10. Master Node & it's Components

- The control plane of Kubernetes, responsible for managing the cluster and making decisions about scheduling and scaling.
- It has several important components:
  - **API Server**: Acts as the main entry point to interact with the Kubernetes cluster. It handles all requests and updates to the cluster.
    
  - **Scheduler**: The scheduler is responsible for scheduling pods based on the configuration file. In the configuration file, you can define the number of CPU, memory, 
    and other configurations. Once we pass the configuration file to the API server, the scheduler selects the best worker node to run the pods, based on resource 
    availability on the worker nodes.

    For example, let’s say your cluster has two worker nodes: one with CPU utilization of 60% and another with CPU utilization of 30%. The scheduler will select the worker 
    node with 30% CPU utilization to run the newly created pod.

  - **Controller Manager**: The Controller Manager is responsible for the overall health of the entire cluster. It ensures that worker nodes are up and running and that the 
    correct number of pods are running. It detects changes in the cluster state and attempts to restore it as soon as possible.

    For example, if a pod dies, it will detect the state change by reading the information stored in etcd and create a new pod as soon as possible.
    
  - **etcd**: etcd is the central distributed database, it stores the cluster information in key-value store such as its current state, desired state, configuration of 
    resources, and runtime data, often referred to as the cluster’s brain. Kubernetes interacts with etcd through its API server. It is the single source of truth for 
    cluster information at any given point of time


# Worker Node in Kubernetes

A **worker node** is a virtual/physical server in a data center or a virtual machine running in the cloud where containers are deployed. The worker node is the machine where the actual user applications run inside the **pods**.

## Worker Node Components

Below is a breakdown of the key components of the worker node:

### 1. Kubelet

The **Kubelet** is the primary node agent that runs on each worker node in the cluster. Its primary responsibility is to look at the spec submitted to the API server on the Kubernetes master and ensure that containers defined in the submitted spec file are running inside pods and healthy. If the Kubelet notices any issues while running pods, it tries to restart the pod on the same node.

If the issue is with the worker node itself, the Kubernetes master detects it and selects another suitable worker node in the cluster to run the pods.

### 2. Kube-proxy

**Kube-proxy** is a network proxy that runs on each node in the cluster. It is responsible for managing network connectivity, maintaining network rules across all nodes, pods, and containers inside the cluster, and also exposing services to the outside world. Kube-proxy is the core network component for the entire Kubernetes cluster.

### 3. Container Runtime

The **container runtime** is the software application that runs inside every worker node and is responsible for running containers. Kubernetes supports various container runtimes such as Docker, containerd, CRI-O, etc.

### 4. Pods

A **pod** is one of the most used terms in Kubernetes (k8s). It is the smallest unit of a k8s cluster that wraps the containers. Each pod consists of one or more containers. In most cases, one pod runs one container. Sometimes, there are more than one dependent containers running together inside a single pod, where one container helps the other container complete the job.

The simple relationship between a worker node, pod, and container is as follows:
- Inside a worker node, there is at least one pod.
- Inside a pod, there is at least one container.


## K8s Clusture Represntaion: 
- https://www.prakashbhandari.com.np/posts/understanding-the-basic-concepts-of-kubernetes-cluster/
- https://kubernetes.io/docs/concepts/architecture/


# Tutorial with Spring boot on K8s
- https://medium.com/@javatechie/kubernetes-tutorial-setup-kubernetes-in-windows-run-spring-boot-application-on-k8s-cluster-c6cab8f7de5a


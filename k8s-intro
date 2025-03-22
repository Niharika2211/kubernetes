### **Kubernetes (K8s) Architecture**  

Kubernetes follows a **Master-Worker Node Architecture**, where the **Control Plane (Master Node)** manages the cluster and the **Worker Nodes** run the containerized applications.  

---

### **1. Control Plane (Master Node)**
The **Control Plane** is responsible for managing the cluster, making decisions, and maintaining the desired state.

**Key Components:**
1. **API Server (`kube-apiserver`)**  
   - Acts as the entry point for all Kubernetes commands (kubectl, UI, or API calls).  
   - Handles authentication and validation.  
   
2. **Scheduler (`kube-scheduler`)**  
   - Assigns Pods to Nodes based on resource availability.  

3. **Controller Manager (`kube-controller-manager`)**  
   - Manages different controllers such as Node Controller (detects failures), Replication Controller (ensures desired Pod count), and more.  

4. **etcd (Key-Value Store)**  
   - Stores cluster configuration and state.  
   - Highly available and distributed.  

---

### **2. Worker Nodes (Compute Nodes)**
Worker Nodes run the actual containerized applications.

**Key Components:**
1. **Kubelet**  
   - Ensures containers defined in PodSpec are running on the Node.  
   - Communicates with the API Server.  

2. **Kube-proxy**  
   - Handles networking between Pods and external traffic routing.  
   - Manages load balancing within the cluster.  

3. **Container Runtime (Docker/containerd/cri-o)**  
   - Runs the containers inside Pods.  
   - Interacts with Kubernetes via the **Container Runtime Interface (CRI)**.  

---

### **3. Networking in Kubernetes**
- **CNI (Container Network Interface)** handles networking.  
- Each Pod gets a unique **IP address** and communicates via **Cluster Networking**.  
- Services expose Pods internally (ClusterIP) or externally (NodePort, LoadBalancer, or Ingress).  

---

### **4. Real-World Workflow**
1. A **developer** applies a Deployment (`kubectl apply -f deployment.yaml`).  
2. The **API Server** receives the request and updates `etcd`.  
3. The **Scheduler** assigns the Pod to a suitable Node.  
4. The **Kubelet** on that Node pulls the required container image and starts the Pod.  
5. The **Kube-proxy** enables networking for inter-Pod communication.  

---

### **5. Diagram of Kubernetes Architecture**
```
                  +---------------- Control Plane ----------------+
                  |                                               |
                  |  +---------------+    +-------------------+   |
                  |  |  API Server   | <--|  kubectl/API Call |   |
                  |  +---------------+    +-------------------+   |
                  |          |                                 |
                  |  +---------------+   +--------------------+ |
                  |  |   Scheduler   |   | Controller Manager | |
                  |  +---------------+   +--------------------+ |
                  |          |                                 |
                  |       +------+      +-------------------+  |
                  |       | etcd | <--> | Cluster Metadata |  |
                  |       +------+      +-------------------+  |
                  +-------------------------------------------+

                  +---------------- Worker Nodes -------------+
                  |                                           |
      Node-1     |  +---------+   +----------+   +---------+ |
      ---------  |  | Kubelet |   | Kube-Proxy|   | Pods    | |
      Node-2     |  +---------+   +----------+   +---------+ |
      ---------  |    Container Runtime (Docker/containerd)  |
                  +-------------------------------------------+
```

---

### **6. Key Takeaways**
✅ **Master Node** manages the cluster.  
✅ **Worker Nodes** run the applications.  
✅ **API Server** is the entry point for all operations.  
✅ **etcd** stores cluster state.  
✅ **Kubelet** ensures Pods run as expected.  
✅ **Kube-proxy** manages networking.  

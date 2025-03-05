# Kubernetes Tutorial

## **Introduction**

This tutorial covers basic Kubernetes commands for setting up and managing clusters using Minikube. It includes steps for creating, managing, and deleting Pods, Deployments, and Services.

--- 

## **Prerequisites**

 * Install Minikube and kubectl on your system.

 * Ensure Docker is installed and running.

---

## **Setting Up Minikube**

**1. Start Minikube**

```bash minikube start --driver=docker```

**2. Check Minikube Status**

```bash minikube status```

**3. Find the Minikube IP Address**

```bash minikube ip```

Example Output:

192.168.49.2

**4. SSH into Minikube**

minikube ssh

**5. Default Credentials for Minikube Node**

Username: docker
Password: tcuser

---

---
## **Managing Kubernetes Cluster**

**6. Get Cluster Info**

```bash kubectl cluster-info```

**7. Get Available Nodes**

```bash kubectl get nodes```

**8. Get Available Pods**

```bash kubectl get pods```

**9. Get Available Namespaces**

```bash kubectl get namespaces```

**10. List System Pods Running in Master Node**

```bash kubectl get pods --namespace=kube-system```

---

---
## **Creating and Managing Pods.**

**11. Create a Pod**

```bash kubectl run nginx --image=nginx```

**12. Describe a Pod**

```bash kubectl describe pod nginx```

**13. SSH into Minikube**

```bash minikube ssh```

**14. Verify the Running Container**

```bash docker ps | grep nginx```

**15. Connecting Two Containers**

```bash docker exec -it <container_id> sh```
  ```bash hostname```
  ```bash hostname -i```
  ```bash curl <pod_ip>```

**16. Exit from Container**

```bash logout```

**17. Get Pod Details with IP Address**

```bash kubectl get pods -o wide```

**18. Delete a Pod**

```bash kubectl delete pod nginx```

**19. Verify Deletion**

```bash kubectl get pods```

---
## **Kubernetes Deployments**
---

**20. Create an Alias for kubectl**

```bash alias k="kubectl"```

**21. Create a Deployment**

```bash k create deployment nginx-deployment --image=nginx```

**22. Get Deployment**

```bash k get deployments```

**23. Describe Deployment**

```bash k describe deployment nginx-deployment```

**24. Describe a Specific Pod in Deployment**

```bash k describe pods <pod_name>```

**25. Scale Deployment (Increase Replicas)**

```bash k scale deployment nginx-deployment --replicas=5```

**26. Verify Scaling**

```bash k get pods```

**27. Get Pods with IP Addresses**

```bash k get pods -o wide```

**28. Connect to a Specific Pod**

```bash curl <pod_ip>```

----
## **Exposing Services**
----

**29. Expose Internal Port to External**

```bash k expose deployment nginx-deployment --port=8080 --target-port=80```

**30. Get Services**

```bash k get svc```

**31. Describe a Specific Service**

```bash k describe service nginx-deployment```

----
## **Cleaning Up**
----

**32. Remove Deployment**

```bash k delete deployment nginx-deployment```

**33. Delete Service**

```bash k delete service nginx-deployment```

**34. Verify Cleanup**

```bash k get deployment```
  ```bash k get svc```

**Notes:**

Selectors are used to connect deployments with pods.

In Kubernetes, Pods and Deployments are separate objects, which is why selectors are necessary.

----
## **Conclusion**
----

This tutorial covered the basics of Kubernetes, including setting up Minikube, creating Pods and Deployments, exposing services, and cleaning up resources. For advanced topics, consider exploring ConfigMaps, Persistent Volumes, and Ingress Controllers.

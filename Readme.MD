Name: 

Question 1:
You are tasked with deploying an application in the production namespace.

Create a deployment named web-deployment with the following specifications:

Image: nginx:1.21
3 replicas
Container port: 80
Expose the deployment using a ClusterIP service named web-service.

Target port: 80
Service port: 8080
Save the resulting manifests as deployment-service.yaml.


Question 2:
You need to set up a service and ingress for a backend application.

Create a deployment named backend in the default namespace with the following specifications:

Image: python:3.10-slim
2 replicas
Container port: 5000
Expose the deployment via a NodePort service named backend-service on port 30080.

Configure an ingress resource named backend-ingress to route traffic to the backend-service using the following rules:

Host: backend.example.com
Path: /api
Save all the resource manifests as backend-ingress.yaml.



Here are three Certified Kubernetes Administrator (CKA)-style exam questions covering deployments, services, and ingress:

Question 1: Deployments and Services
You are tasked with deploying an application in the production namespace.

Create a deployment named web-deployment with the following specifications:

Image: nginx:1.21
3 replicas
Container port: 80
Expose the deployment using a ClusterIP service named web-service.

Target port: 80
Service port: 8080
Save the resulting manifests as deployment-service.yaml.

Question 2: Services and Ingress
You need to set up a service and ingress for a backend application.

Create a deployment named backend in the default namespace with the following specifications:

Image: python:3.10-slim
2 replicas
Container port: 5000
Expose the deployment via a NodePort service named backend-service on port 30080.

Configure an ingress resource named backend-ingress to route traffic to the backend-service using the following rules:

Host: backend.example.com
Path: /api
Save all the resource manifests as backend-ingress.yaml.


Question 3:
You are troubleshooting a misconfigured application in the test namespace.

There is a deployment named frontend-deployment with 2 replicas that uses the image nginx:latest.

Update the deployment to use the image nginx:1.23 and scale it to 4 replicas.
The deployment is exposed via a service named frontend-service of type ClusterIP.

The service's target port is incorrectly set to 8080.
Update the target port to 80 without recreating the service.
Verify that the service is accessible on its ClusterIP by running a curl command from a debug pod in the same namespace.

Save the debug commands and explanations as troubleshooting-notes.md.


Question 4:
You are required to configure dynamic provisioning of storage in a Kubernetes cluster.

Create a StorageClass named fast-storage with the following specifications:


Parameters:
type: gp2
Reclaim policy: Delete
Create a PersistentVolume named pv-data with the following specifications:

Capacity: 10Gi
Access modes: ReadWriteOnce
StorageClass: fast-storage
HostPath: /mnt/data
Save the configuration as storageclass-pv.yaml.

Question 5:
You are tasked with deploying an application that uses a PersistentVolumeClaim for storage.

Create a PersistentVolumeClaim named app-pvc in the default namespace with the following specifications:

Storage request: 5Gi
Access mode: ReadWriteOnce
StorageClass: standard
Create a deployment named app-deployment that uses the PVC with the following details:

Image: nginx:1.21
Mount the PVC to /usr/share/nginx/html inside the container.
Save the configuration as pvc-deployment.yaml.

Question 6:
You are troubleshooting a volume issue in the test namespace.

A PersistentVolumeClaim named test-pvc is bound to a PersistentVolume named test-pv, but the pod using this PVC is in a Pending state.

Verify if the PV has sufficient capacity and matches the requested access modes of the PVC.
If there is a mismatch, update the PV to match the PVC requirements without deleting the PV.
After fixing the issue, confirm that the pod successfully mounts the volume by running a kubectl exec command to create a file named test-file.txt in the mounted volume.

Save the troubleshooting steps and commands as volume-troubleshooting-notes.md.

Question 7:
You need to deploy an application on a specific group of nodes with taints applied.

Label a node with the key-value pair env=production.

Use the kubectl label command to apply the label.
Taint the same node with the key dedicated and value critical.

Taint: dedicated=critical:NoSchedule
Create a deployment named critical-app with the following specifications:

Image: busybox
Replica: 1
Command: ["sleep", "3600"]
Add a node selector to schedule the pod on nodes labeled env=production.
Add tolerations to allow the pod to run on tainted nodes.
Save the configuration as taint-toleration-deployment.yaml.


Here are three CKA-style exam questions involving StatefulSet, Deployment, Services, StorageClass, PersistentVolume, PersistentVolumeClaim, and Ingress:

Question 8: StatefulSet with PersistentVolumeClaim
You need to deploy a StatefulSet for a database application.

Create a StorageClass named fast-storage with the following specifications:


Parameters:
type: pd-standard
Reclaim policy: Delete.
Create a StatefulSet named db-statefulset with the following specifications:

Image: postgres:14
3 replicas.
Each pod should have a PersistentVolumeClaim dynamically provisioned using the fast-storage StorageClass.
PVC size: 5Gi.
Expose the StatefulSet with a headless service named db-service.

Service port: 5432.
Save the configuration as statefulset-storage.yaml.

Question 9:
You need to set up a PersistentVolume for an application and restrict its scheduling to specific nodes.

Create a PersistentVolume named app-pv with the following specifications:

Capacity: 10Gi.
Access modes: ReadWriteOnce.
HostPath: /mnt/app-data.
Create a PersistentVolumeClaim named app-pvc with the following specifications:

Storage request: 10Gi.
Access mode: ReadWriteOnce.
Create a Deployment named app-deployment with the following specifications:

Image: httpd:2.4.
2 replicas.
Mount the app-pvc to /usr/local/apache2/htdocs inside the container.
Add a node selector to ensure the pods are scheduled only on nodes labeled disk=ssd.
Expose the deployment using a NodePort service named app-service on port 30080.

Save the configuration as persistentvolume-deployment.yaml.

Question 10:

You need to upgrade your Kubernetes cluster from version the current version to version 1.31.1. Ensure that the control plane components are upgraded first, followed by the worker nodes.

Task:

Upgrade the Kubernetes control plane to version 1.31.1. Upgrade the worker nodes to version 1.31.1 while minimizing downtime.


Question 11: Pod Affinity and Anti-Affinity
You need to ensure that two sets of pods are scheduled with specific affinity and anti-affinity rules.

Create a deployment named frontend-app with the following specifications:

Image: nginx
Replicas: 2
Pods should prefer to be scheduled on nodes where other frontend-app pods are running.
Create another deployment named backend-app with the following specifications:

Image: busybox
Replicas: 1
Command: ["sleep", "3600"]
Pods must not be scheduled on nodes where frontend-app pods are running.
Save both configurations as affinity-deployments.yaml.

Question 12:

You are tasked with configuring access controls for a Kubernetes cluster.

Create a Namespace named dev-team.

Create a Role named dev-role in the dev-team namespace with the following permissions:

Allow listing (get, list, watch) of Pods.
Create a RoleBinding named dev-binding in the dev-team namespace to bind the dev-role to a user named developer-user.

Create a ClusterRole named cluster-reader with the following permissions:

Allow listing (get, list, watch) of Pods across all namespaces.
Create a ClusterRoleBinding named cluster-reader-binding to bind the cluster-reader ClusterRole to a group named ops-group.

Save all the configurations as rbac-config.yaml.



Question 13:
You need to deploy a resource-intensive application with appropriate resource allocations.

Create a Namespace named resource-test.

Create a Deployment named resource-deploy in the resource-test namespace with the following specifications:

Image: nginx:1.23.
3 replicas.
Each container should have the following resource requests and limits:
CPU request: 250m.
Memory request: 256Mi.
CPU limit: 500m.
Memory limit: 512Mi.
Verify that the pods in the deployment are running within the resource constraints.

Save the configuration as resource-deployment.yaml.

Question 14: ConfigMaps and Secrets
You are required to configure an application using ConfigMaps and Secrets.

Create a ConfigMap named app-config with the following key-value pairs:

APP_ENV: production
APP_DEBUG: false.
Create a Secret named app-secret with the following key-value pairs:

DB_USER: admin.
DB_PASSWORD: password123.
Create a Deployment named config-secret-deploy that uses the above ConfigMap and Secret.

The environment variables in the container should use the values from the ConfigMap and Secret.
Verify that the application can access the environment variables inside the pod.

Save the configuration as config-secret-deployment.yaml.

Question 15: Backup and Restore etcd
You are tasked with backing up and restoring the etcd database for a Kubernetes cluster.

Create a backup of the etcd database using the etcdctl tool. Use the following details:

Endpoint: https://127.0.0.1:2379.
Certificate authority file: /etc/kubernetes/pki/etcd/ca.crt.
Client certificate file: /etc/kubernetes/pki/etcd/server.crt.
Client key file: /etc/kubernetes/pki/etcd/server.key.
Save the backup as /tmp/etcd-backup.db.
Simulate a failure by deleting a resource (e.g., a Deployment).

Restore the etcd database from the backup and verify that the deleted resource is restored.

Provide the commands used in a file named etcd-backup-restore-commands.txt.


Question 16:
You are tasked with restricting network communication within a namespace.

Create a Namespace named network-test.

Deploy two pods in the network-test namespace:

Pod 1: Name: frontend, Image: nginx:1.23.
Pod 2: Name: backend, Image: busybox, Command: ["sleep", "3600"].
Create a NetworkPolicy named allow-backend-access in the network-test namespace with the following specifications:

Only allow incoming traffic to the backend pod on port 80 from pods labeled role=frontend.
Deny all other traffic to the backend pod.
Verify the network policy by attempting to curl the backend pod from the frontend pod and another pod without the role=frontend label.

Save the configurations as network-policy.yaml.


Question 17: DaemonSet and Logging
You need to deploy a logging agent across all nodes in the cluster.

Create a DaemonSet named logging-agent with the following specifications:

Image: fluentd:latest.
The pods should run on all nodes in the cluster, including the master nodes.
Ensure the pods have tolerations to run on nodes tainted with node-role.kubernetes.io/master:NoSchedule.
Configure the DaemonSet to mount the host’s /var/log directory to /var/log in the container.

Verify that the DaemonSet is running one pod on each node in the cluster.

Save the configuration as logging-daemonset.yaml.
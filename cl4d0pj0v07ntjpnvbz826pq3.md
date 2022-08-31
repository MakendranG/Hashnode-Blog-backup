## How to Leverage Kubecost to view real-time K8s spend data in Azure

Real-time cost visibility and insights for teams using Kubernetes is provided by **Kubecost**.

Teams can prioritize where to focus their efforts if they install Kubecost on a single cluster or a fleet of clusters. `Up to 80%` of the cost of the Kubernetes cloud infrastructure can be saved by customers using Kubecost. Thousands of teams across companies of all sizes are being given the power to monitor and reduce costs.

It is easy to drive adoption within any organization with the integration of the open source Cloud Native platform.


The instructions walks you through the steps needed to setup a single AKS cluster and view all your K8s data.

We'll be using the portal to create an AKS cluster and deploy a sample application.

The **first step** is to deploy the cluster. Go to the portal and search for `Kubernetes services -> Create -> Create a Kubernetes cluster`.

Cluster details should be configured.

**Basics**
**1. Project details:**

- Select an Azure Subscription.
- Select or create an Azure Resource group, such as `hashnode-demo`.

**2. Cluster details:**

- Choose the `Dev/Test($)` preset configuration.
- Enter a Kubernetes cluster name, such as `hashnode-demo-cluster`.
- Select a Region.
- Select a Kubernetes version for the AKS cluster, the version used is 1.22.6 (default).

- Primary node pool:
Select `Standard B2s` if it is a testing/learning purpose. Otherwise, The default values should be left.

**Networking**

- You can leave the DNS name prefix unchanged by selecting `Kubenet`.

_It is possible to enable HTTP application routing. If you want to expose the dashboard via a Load Balancer, you need this step._

- Click to create a review tab.


![demo](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pk2ce5t8xlq3wqpagxiv.jpg)

The **second step** is configuring access to the cluster.

- We will be using the `az aks` command to access the cluster. You can open the terminal and log in with the same credentials you used to create the AKS cluster.

```
$ az login
```
To confirm your identity, open your browser and look for the sign in page. You need to sign in with your account credentials.

- Use the `az aks get-credentials` command to connect to your cluster. The command downloads credentials and sets the current context to use them.


```
$ az aks get-credentials --resource-group hashnode-demo --name hashnode-demo-cluster
```


- You can use the get to return a list of the cluster nodes to verify the connection to your cluster.

```
$ kubectl get nodes
```

- It is possible to get the nodes with the kubectl. 

```
NAME                                STATUS   ROLES   AGE   VERSION
aks-agentpool-15282599-vmss000000   Ready    agent   36s   v1.22.6
```


A sample application can be deployed. 

- Create a namespace

```
$ kubectl create namespace nginx-app
```

- You can deploy the application.

```
$ kubectl apply -f https://k8s.io/examples/application/deployment.yaml -n nginx-app
```

- The deployment should be verified.

```
$ kubectl get deployments -n nginx-app
```
The output should look like this. Make sure the deployment is `ready`.

```
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   2/2     2            2           19s
```

## Installing Kubecost on AKS

The **first step** is to install Kubecost.

- You need to open the terminal and create a namespace in your cluster.

```
$ kubectl create namespace kubecost 
```

- The official helm repository should be added.

```
$ helm repo add kubecost https://kubecost.github.io/cost-analyzer/ 
```

- The `Prometheus` and `Grafana` dependencies will be installed in a standard installation.

## Without a cost export

```
$ helm install kubecost kubecost/cost-analyzer --namespace kubecost
```

Installation of the cost-analyzer is done by helm. It will take a few minutes to complete. Once it's done, verify that all the containers are running smoothly.

```
$ kubectl get pods -n kubecost
```

The **second step** is to view the data. You can expose the dashboards using port forwarding.

- The `port-forward` command can be run.

```
$ kubectl port-forward --namespace kubecost deployment/kubecost-cost-analyzer 9090
```

- To see the data, open `localhost:9090` in your browser. 


The **third step**  is to expose the deployment outside of the cluster. If you want to open your deployment to the world, you can expose port 9090 via the Load Balancer.

- The file is called `hashnodekubecostcost.yml` has the following contents. This file can be found within this section's files.

```
apiVersion: v1
kind: Service
metadata:
    name: public-svc
spec:
    type: LoadBalancer
    ports:
    - port: 9090
selector:
    app: cost-analyzer
```


- Apply to a cluster.

```
$ kubectl apply -f hashnodekubecostcost.yml -n kubecost
```

- The public-svc service has been created as a Load Balancer.

```
NAME                                TYPE           CLUSTER-IP     EXTERNAL-IP     PORT(S)                      AGE
kubecost-cost-analyzer              ClusterIP      10.2.108.159   <none>          9001/TCP,9003/TCP,9090/TCP   36s
kubecost-grafana                    ClusterIP      10.2.151.57    <none>          80/TCP                       36s
kubecost-kube-state-metrics         ClusterIP      10.2.4.201     <none>          8080/TCP                     36s
kubecost-prometheus-node-exporter   ClusterIP      None           <none>          9100/TCP                     36s
kubecost-prometheus-server          ClusterIP      10.2.218.20    <none>          80/TCP                       36s
public-svc                          LoadBalancer   10.2.114.22   <EXTERNAL-IP>   9090:32373/TCP               36s
```

- View Kubecost data by visiting the public-svc address: http://<EXTERNAL-IP>:9090





Gratitude for perusing my article till end. I hope you realized something unique today. If you enjoyed this article then please share to your buddies and if you have suggestions or thoughts to share with me then please write in the comment box.

   
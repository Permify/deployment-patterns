<img src="https://upload.wikimedia.org/wikipedia/commons/3/39/Kubernetes_logo_without_workmark.svg" alt="Logo of the project" target="_blank" height="100px"  align="right">

# Distributed Deployment with Serf
 in this example there are examples of deployment and scaling to get a distributed Permify & Serf deployment

### Prerequisites
* Kubernetes Cluster
* Kubectl
* Text Editor
* Serf

## Installing / Getting started

You can follow the steps below for the deployment process:

1. First, make sure that the Kubernetes CLI tool `kubectl` is installed and properly connected to your Kubernetes cluster.

2. Then, you can create deployments using your Kubernetes configuration files (your YAML files). You can use the following commands for this:

    ```bash
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
    kubectl apply -f serf.yaml
    ```

These operations will create deployments and related services on your Kubernetes cluster.

These three YAML files define various application run configurations on a Kubernetes cluster. The `deployment.yaml` is used to run 5 copies of an application called `permify`. Each of them uses a specific container image (`permify/permify`) and has a specific memory and CPU resource request and limit.

The `service.yaml` defines a service to provide network access to the `permify` application. This service directs specific ports to the container ports of the `permify` application.

Lastly, the `serf.yaml` defines the deployment and service of another application called `serf`. This application is used to provide the distributed features of the `permify` application. This deployment and service also use a specific container image (`permify/serf`) with its own resource requests and limits.

## Configuration

Absolutely, the provided YAML files define the configuration for Kubernetes resources, such as Deployments and Services. Here's a brief description of what each of them does and how they can be customized:

1. `deployment.yaml`: This file defines a Deployment for the `permify` application. It specifies that five replicas (i.e., instances) of the application should be run. It also includes details about the container image to be used (`permify/permify`), arguments to be passed to the application, and resources allocated to each instance (CPU and memory). You can customize the arguments to match your specific needs. For example, the `--database-uri` argument can be modified to point to a different database if necessary.

2. `service.yaml`: This file defines a Service that provides network access to the `permify` application. The Service routes traffic to the correct Pods based on the `app: permify` label. The `type: LoadBalancer` line indicates that the Service should be exposed through a cloud provider's load balancer. You can change the type of Service (e.g., to `NodePort` or `ClusterIP`), or modify the ports if needed.

3. `serf.yaml`: This file defines both a Deployment and a Service for the `serf` application, which appears to be used for distributed features in `permify`. The Deployment specifies the container image to use (`permify/serf`) and resources for each instance. The Service provides network access to the `serf` application. You can customize the resources and ports as necessary.

Remember, changes to these configurations will need to be applied with `kubectl apply` for them to take effect on your Kubernetes cluster.




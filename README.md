# EKS Cluster Setup with Terraform

This repository contains the configuration to set up an Amazon EKS cluster from scratch using Terraform. The project includes several features such as cluster-autoscaler, load balancer, pod identity (IRSA), EBS, and EFS addons, all deployed using Terraform resources without any external modules.

## Features

- **EKS Cluster**: Set up an EKS cluster using native Terraform resources.
- **Cluster Autoscaler**: Automatically scales the worker nodes in the cluster based on load.
- **Load Balancer**: Configured load balancer for managing external traffic.
- **Pod Identity (IRSA)**: Implemented IAM Roles for Service Accounts (IRSA) for secure AWS API access by the pods.
- **EBS Addon**: Attach Amazon EBS volumes to your pods for persistent storage.
- **EFS Addon**: Use Amazon EFS for scalable and elastic file storage across pods.
- **Helm Provider**: Managed Helm charts to install Kubernetes addons such as the autoscaler, EBS, and EFS.

## Prerequisites

- [Terraform](https://www.terraform.io/downloads.html) 1.0 or later
- AWS CLI configured with appropriate credentials
- AWS account with permissions to manage EKS, EC2, IAM, and VPC resources
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) installed and configured
- [Helm](https://helm.sh/docs/intro/install/) installed for managing Kubernetes addons

## Terraform Providers Used

- **AWS Provider**: To manage AWS resources like EKS, IAM, and EC2.
- **Kubernetes Provider**: To manage Kubernetes resources like service accounts and storage classes.
- **Helm Provider**: To deploy and manage Kubernetes addons such as the Cluster Autoscaler.

## Resources Created

### 1. **VPC and Networking**

- A VPC with subnets across multiple Availability Zones.
- Public and private subnets for load balancers and worker nodes.
- Internet Gateway, NAT Gateway, and appropriate route tables.

### 2. **EKS Cluster**

- An EKS control plane and worker nodes deployed using `aws_eks_cluster` and `aws_eks_node_group`.
- Security groups and IAM roles for the EKS cluster and its worker nodes.
  
### 3. **IAM Roles and Policies**

- IAM roles for service accounts (IRSA) with necessary permissions to manage autoscaling and access EFS, EBS, etc.
- Policies attached to IRSA to allow pods to access AWS services securely.

### 4. **Cluster Autoscaler**

- Deployed using the Helm provider with the `cluster-autoscaler` Helm chart.
- Autoscaling policies configured to automatically scale the worker nodes based on the cluster load.

### 5. **Storage (EBS & EFS)**

- EBS volumes configured for dynamic provisioning of block storage using the EBS CSI driver.
- EFS provisioner deployed for file system storage across multiple pods.

### 6. **Load Balancer**

- Configured AWS ALB or NLB using Kubernetes annotations for exposing services to external traffic.



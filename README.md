# AMLK8s Samples
This repository is intended to serve as an information hub for customers and partners who are interested in AMLK8s (Custmer managed Kubernetes cluster). Use this repository for onboarding and testing instructions as well as an avenue to provide feedback, issues, enhancement requests and stay up to date as the preview progresses.

## Disclaimer 
#### The lifecycle management(health, kubernetes version upgrades, security updates to nodes, scaling, etc.) of the AKS or Arc Kubernetes cluster is the responsibility of the customer.
For AKS, read what is managed and what is shared responsibility [here](https://docs.microsoft.com/en-us/azure/aks/support-policies)

#### All preview features are available on a self-service, opt-in basis and are subject to breaking design and API changes. Previews are provided "as is" and "as available," and they're excluded from the service-level agreements and limited warranty. As such, these features aren't meant for production use.


#### AMLK8s supports targeting ML training on both  [Azure Kubernetes Service (AKS)](https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough) clusters or any cluster that is registered in Azure using [Arc](https://docs.microsoft.com/en-us/azure/azure-arc/kubernetes/overview). 


**Note**: The compute name in Python SDK and CLI may be changed during preview.

## Overview
AMLK8s project enables customer to use their exisiting AKS clusters or Azure Arc for Kubernetes clusters as compute target for AML training workload . Data scientists will have same experience as other compute targets. They can submit different types of training jobs to AMLK8s compute target. AMLK8s Will first support SDK and portal, and restapi/CLI will be supported later.


## Getting Started

To use AMLK8s compute in private preview, follow these steps:

#### IT Operator steps to set up Kubernetes cluster 
1. Create/provision a Kubernetes cluster to attach to an AML workspace
    * [Create AKS cluster](/docs/create-provision-AKS-cluster.md)
    * [Connect Azure Arc Kubernetes cluster](/docs/enable-arc-kubernetes-cluster.md)
    
1. Attaching Kubernetes cluster to AML workspace
    * [AKS](/docs/attach-aks-cluster-aml-workspace.md)
    * [Azure Arc for Kubernetes](/docs/attach-arc-cluster-aml-workspace.md)
    
1. [Manually install AMLK8S operator on kubernetes (AKS or ARC) clusters](/docs/manual-installation-amlk8s-operator.md)

#### Data Scientist steps to submit trainig jobs
1. [Submit AML training jobs to AMLK8s compute](/docs/submit-training-jobs.md)


[Limitations and Known Issues](/docs/limitations-and-knownIssues.md)


## FAQ 
#### Recommend AKS cluster resource 
We recommend you use a at least 3 nodes cluster, each node having at least 2C 4G. And if you want to running GPU jobs, you need some GPU nodes.
#### AML add-on version upgrade
We will install the latest AML add-on services automatically when you first attach AKS cluster to AML workspace. You can check add-on components version using ```helm list``` and update according to [Manage AML Add-on](https://github.com/Azure/CMK8s-Samples/blob/master/docs/5.%20Manage%20AML%20add-on.markdown).
#### Why the nodes run ocupied in a run is more than node count in run list?
The node count in the number of worker, for distribute training job, such as ps-worker or MPI/horovod they may need extra launcher node or ps node, they may also ocuppy one node. We will optimise this in following version.
#### What Azure storage does AMLK8s support?
AML K8s compute only suport Azure blob container, if your data is in other Azure storage, please move it to Azure blob first. We will support other Azure storage in following iteration.
#### What type of jobs deso AMLK8s support?
AML K8s compute doesn't support all AML jobs by now. For more details, please refer to the list in [Using CMAKS Compute in AML Notebooks](https://github.com/Azure/AML-Kubernetes/blob/master/docs/6.%20Using%20CMAKS%20Compute%20in%20AML%20Notebooks.md).
#### How do I use AMLK8s compute in China Region?
Firstly, make sure you have switched the active cloud to AzureChinaCloud with [az cloud set](https://docs.microsoft.com/en-us/cli/azure/manage-clouds-azure-cli?view=azure-cli-latest) command. Then you can use the SDK and CLI sample in this repo.


# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

![Impressions](https://PixelServer20190423114238.azurewebsites.net/api/impressions/CMK8s-Samples/README.png) 

# Azure Cloud Labs

Six hands-on labs on **Microsoft Azure** done at Odisee (Datacenter & Cloud course, Azure for Students subscription). They go from a single virtual machine to a Kubernetes cluster. The labs are **separate exercises**, not one connected environment.

## The six labs

| # | Lab | What I did | Key idea |
|---|-----|-----------|----------|
| 1 | Virtual machine | Created an Ubuntu Server VM and connected to it over SSH | Compute in the cloud, resource groups, availability zones |
| 2 | Virtual network | Created a VNet `10.1.0.0/16` with `frontend` (`10.1.1.0/24`) and `backend` (`10.1.2.0/24`) subnets | Address spaces and subnet design |
| 3 | Container Instances | Deployed a web container with a public DNS name on port 80 | Running containers without managing servers |
| 4 | Storage account | Created a storage account and a Blob container, then uploaded a file | Object storage |
| 5 | ARM template | Deployed a storage account from a JSON template | Infrastructure as Code: repeatable deployments |
| 6 | Kubernetes (AKS) | Created an AKS cluster, connected through Cloud Shell, created a namespace and deployed an application | Container orchestration |

## Infrastructure as Code example

[`storage-account.json`](storage-account.json) is the ARM template used in lab 5. It declares a `StorageV2` account with `Standard_LRS` replication in Switzerland North.

Deploy it with the Azure CLI (replace the resource group and choose a globally unique storage account name):

```bash
az group create --name RG-opslag --location switzerlandnorth
az deployment group create \
  --resource-group RG-opslag \
  --template-file storage-account.json
```

## What I learned

- How Azure resources are organized (subscriptions, resource groups, regions)
- How to design a virtual network with separate subnets
- The difference between clicking in the portal and declaring infrastructure in code, and why the second is repeatable
- The basics of deploying an application on Kubernetes (namespaces, deployments)

## Notes

- The labs were done with an educational subscription (Azure for Students).
- No credentials are stored in this repository.

## Tech

Azure, Virtual Machines, Virtual Network, Container Instances, Storage (Blob), ARM templates, AKS, Kubernetes, Cloud Shell, Linux

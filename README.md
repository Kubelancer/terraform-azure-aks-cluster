# Learn Terraform - Provision AKS Cluster

## Prerequisites


For this tutorial, you will need

    an Azure account
    a configured Azure CLI
    kubectl

## Set up and initialize your Terraform workspace

$ git clone git clone https://github.com/hashicorp/learn-terraform-provision-aks-cluster

cd learn-terraform-provision-aks-cluster

## Create an Active Directory service principal account

$ az ad sp create-for-rbac --skip-assignment

## Update your terraform.tfvars file
# terraform.tfvars
appId    = "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"
password = "aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa"

## Initialize Terraform
$ terraform init

## Provision the AKS cluster
$ terraform plan
$ terraform apply

## Configure kubectl
$ az aks get-credentials --resource-group $(terraform output -raw resource_group_name) --name $(terraform output -raw kubernetes_cluster_name)

## Clean up your workspace
$ terraform destroy
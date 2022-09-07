
#
#     STEP BY STEP GUIDE FOR INSTALLING & SETTING ISTIO SERVICE MESH ON KUBERNETES CLUSTER


##    Use this step-up-step guide if you want to learn how to install istio service mesh 
##    On a Kubernetes cluster so that you can get all the benefits of a service mesh.
#


##    By: Mamun Rashid
###   Connect with me on Linkedin: https://www.linkedin.com/in/mamunrashid/
#

#

## Pre-requisites
#

#


### 1. MacOS or Ubuntu Linux
        I will add Windows equivalent later.
### 2. Access to a GCP project
     Take a note of the project name:
       e.g. foobar-project

### 3. kubernetes Engine API is enabled on that GCP project
        e.g. https://console.cloud.google.com/apis/api/container.googleapis.com/overview

### 4. Your GCP account has permission to admin k8s clusters

### 5. gcloud (GCP cli installed) on your local Mac or Ubuntu Machine

### 6. kubectl installed on your local Mac or Ubuntu Machine

#

#


## COST
#
### As of September 2022, a standard Kubernetes Cluster with 2 N2 Instances will cost $0.72/Hour (72 Cents/Hour)
#

#


##  Steps:
#

### 7. Create vpc, subnet and k8s cluster
         You will ony need to create a vpc abd subnet if you don't already have a default VPC and at least 1 subnet in it
         e.g. gcloud container clusters create foobar-cluster --region us-central1  --project foobar-project
         Make a note of the name of the cluster and the region it is in. You will need that shortly.
         e.g. 
           foobar-cluster
           us-central1
         * If you already have a Kubernetes Cluster , you can skip this step.
      

### 8. kubectl config current-context
         You will see that you are NOT connected to your newest cluster you just created

### 9. Make the kuberneetes cluster your current context:
         gcloud container clusters get-credentials name_of_kubernetes_cluster  --region region_where_kubernetes_cluster_is_in --project foobar-project


### 10. Before you can deploy Istio to a cluster, list all available contexts:
         kubectl config get-contexts
         example:
         mac1238$ kubectl config get-contexts
                  CURRENT   NAME             CLUSTER          AUTHINFO                                           NAMESPACE
                  *         foobar-cluster   foobar-cluster   foobar-cluster-admin   

### 11. Confirm that now you ARE connected to your kubernetes cluster:
         kubectl config current-context


###  12.. Clone the repo https://github.com/DickChesterwood/istio-fleetman
###       This is Dick Chesterwood's repo. This will be the "app" that we will deploy on our cluster
###         So that , when we have Istio, we can see some traffic.
###         Alternatively, you can choose another application of your choice.
            git clone https://github.com/DickChesterwood/istio-fleetman

     


### 30. Destroy the Kubernetes cluster so that you stop incurring cost of running a small cluster.
          gcloud container clusters delete kubernetes_cluster_name --zone zone_where_the_cluster_is --project project_name_where_the_cluster_is



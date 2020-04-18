# KinD
kubernetes in Docker

# Documentation Link:
https://kind.sigs.k8s.io/docs/user/quick-start/

# Installation

Pre-requisite:
  Docker community edition installation
  kubectl client for k8s.

## On macOS / Linux:

curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.7.0/kind-$(uname)-amd64
chmod +x ./kind
mv ./kind /usr/local/bin

kind --version
kind --help

# Creating a Cluster
  Creating a Kubernetes cluster is as simple as 
 $ kind create cluster
 $ kind get nodes
 $ docker ps --> to check how many containers running at the moment
 $ kind delete cluster
 
# Multi-node clusters 

In particular, many users may be interested in multi-node clusters. A simple configuration for this can be achieved with the following config file contents:

# three node (two workers) cluster config
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker

# Control-plane HA

You can also have a cluster with multiple control-plane nodes:

# a cluster with 3 control-plane nodes and 3 workers
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: control-plane
- role: worker
- role: worker
- role: worker
 
# Installing kubernetes dashboard

To deploy Dashboard, execute following command:

  $ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc7/aio/deploy/recommended.yaml
 
To access Dashboard from your local workstation you must create a secure channel to your Kubernetes cluster. Run the following command:

  $ kubectl proxy

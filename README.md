🚀 Kubernetes Setup & Pod Deployment Guide (Minikube + Docker)

This repository provides a simple guide to set up Kubernetes locally using Minikube, verify cluster health, and deploy your first Pod using a YAML file.
A visual workflow diagram is included to help understand how Kubernetes processes your deployment.                                                                                                        
                                                                                                           
                                                                                                           
                                                                                                           
             🧩 Kubernetes Workflow Diagram
             ===============================
                                 
             ┌───────────────────────┐
             │     Developer          │
             │  (Your Local Machine)  │
             └──────────┬────────────┘
                        │
                        │ 1. Write YAML (pod.yml)
                        ▼
             ┌────────────────────────────┐
             │     kubectl Command        │
             │  (kubectl apply -f pod.yml)│
             └──────────┬─────────────────┘
                        │
                        │ 2. kubectl sends request
                        ▼
             ┌────────────────────────────┐
             │  Kubernetes API Server     │
             │ (Inside Minikube Cluster)  │
             └──────────┬─────────────────┘
                        │
                        │ 3. API Server validates YAML
                        ▼
             ┌──────────────────────────────┐
             │   Kubernetes Scheduler        │
             │   Selects a node to run Pod  │
             └──────────┬───────────────────┘
                        │
                        │ 4. Scheduler assigns node
                        ▼
             ┌──────────────────────────────┐
             │     Kubelet (on Node)        │
             │ Starts container via Docker  │
             └──────────┬───────────────────┘
                        │
                        │ 5. Kubelet pulls image
                        ▼
             ┌──────────────────────────────┐
             │     Container Runtime         │
             │    (Docker / containerd)      │
             │ Pulls & runs your image       │
             └──────────┬───────────────────┘
                        │
                        │ 6. Pod running successfully
                        ▼
             ┌──────────────────────────────┐
             │      Running Pod             │
             │ (Your App inside Kubernetes) │
             └──────────────────────────────┘


🛠 Optional Commands

Kubernetes
=========
📦 1. Install Minikube (Windows)
Install Minikube using Winget:

  winget install kubernetes.minikube

🔍 2. Check kubectl Version
Verify Kubernetes CLI is installed:

  kubectl --version --client=true

▶️ 3. Start Minikube Using Docker Driver
Start your local Kubernetes cluster:

  minikube start --driver=docker

🧪 4. Verify Cluster Components
Check if all system pods are running:

  kubectl get po -A

🗄️ 5. List Storage Classes

  kubectl get sc

📄 6. Deploy a Pod from YAML File
Apply your pod configuration:

  kubectl apply -f <path-to-pod.yml>

📋 7. List All Pods

  kubectl get pods

🔎 8. Get Detailed Pod Information
  kubectl get pods -o wide

# get all details of pods
  kubectl describe pods <pod-name>

#delete pod
  kubectl delete pod <pod-name>


Replicaset commands
===================

# create yml file and create a rs
  kubectl apply -f <path-to-replicaset.yml>

# to list rs
  kubectl get rs

# complete detail of rs
  kubectl describe rs [rs name]

# scaling pods - imperative - not recommended
  kubectl scale rs calculator-replicaset --replicas=10

# to stop minikube
  minikube stop

# to delete minikube
  minikube delete

# Managing-Deployments-Using-Kubernetes-Engine
## Overview
Dev Ops practices will regularly make use of multiple deployments to manage application deployment scenarios such as **"continuous deployment"**, **"Blue-Green deployments"**, **"Canary deployments"** and more. This lab is to provide practice in scaling and managing containers so you can accomplish these common scenarios where multiple heterogeneous deployments are being used.

## Introduction to deployments
Heterogeneous deployments typically involve connecting two or more distinct infrastructure environments or regions to address a specific technical or operational need. Heterogeneous deployments are called "hybrid", "multi-cloud", or "public-private", depending upon the specifics of the deployment.

## Rolling update
Deployments support updating images to a new version through a rolling update mechanism. When a deployment is updated with a new version, it creates a new ReplicaSet and slowly increases the number of replicas in the new ReplicaSet as it decreases the replicas in the old ReplicaSet.
![alt text](https://cdn.qwiklabs.com/uc6D9jQ5Blkv8wf%2FccEcT35LyfKDHz7kFpsI4oHUmb0%3D?raw=true)

## Canary deployments
A canary deployment consists of a separate deployment with your new version and a service that targets both your normal, stable deployment as well as your canary deployment.

![alt text](https://cdn.qwiklabs.com/qSrgIP5FyWKEbwOk3PMPAALJtQoJoEpgJMVwauZaZow%3D?raw=true)

## Blue-green deployments
Rolling updates are ideal because they allow you to deploy an application slowly with minimal overhead, minimal performance impact, and minimal downtime. There are instances where it is beneficial to modify the load balancers to point to that new version only after it has been fully deployed. In this case, blue-green deployments are the way to go.

![alt text](https://cdn.qwiklabs.com/POW8Q247ZKNY%2ByHIartCsoEu8MAih7k4u1twusCx6pw%3D?raw=true)

## Solution
Solutione file has the the commands step by step

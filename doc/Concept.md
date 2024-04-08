# Comparative analysis of three tools for deploying Kubernetes clusters in a local environment — minikube, kind and k3d.

## Introduction

AsciiArtify, a startup focused on developing a new software product for transforming images into ASCII art using Machine Learning, faces the challenge of selecting the right tool for local Kubernetes cluster development. Three options are considered: minikube, kind and k3d. 

Minikube is designed for quickly setting up local Kubernetes clusters on your workstation. It is useful for developers who need to test and run applications in a local Kubernetes environment without the need for access to a remote cluster.

Kind is used to create temporary Kubernetes clusters using Docker containers as cluster nodes. It is typically used for testing and development, as well as for creating clusters for deploying local applications.

k3d (Kubernetes 3D) is a tool that creates single-node Kubernetes clusters in Docker containers. It simplifies the creation, management, and deletion of local Kubernetes clusters.

## Characteristics

### Minikube

+ Supported OS and Architectures: Works on multiple operating systems, including Windows, macOS, and Linux. Supports various architectures.
+ Automation Capability: Offers automation for cluster creation and management.
+ Additional Features: Suitable for local development and testing. Concerns arise regarding scalability limitations.

### Kind (Kubernetes IN Docker)


+ Supported OS and Architectures: Compatible with Windows, macOS, and Linux. Works within Docker containers.
+ Automation Capability: Allows the creation of local Kubernetes clusters in Docker containers.
+ Additional Features: Considered for local testing purposes.

### k3d

+ Supported OS and Architectures: Works on multiple operating systems. Uses Rancher Kubernetes Engine (RKE) in Docker containers.
+ Automation Capability: Facilitates quick creation and testing of Kubernetes clusters in Docker containers.
+ Additional Features: Chosen for preparing Proof of Concept (PoC).

## Characteristic

| **Pros and Cons**                               | **Minikube**                                     | **Kind**                                         | **k3d**                                          | **Podman**                                       |
|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|
| **Pros**                                      | + Easy to use<br>+ Suitable for local development and testing | + Suitable for local development and testing<br>+ Works within Docker containers<br>+ Possibility for local testing | + Suitable for local development and testing<br>+ Works within Docker containers<br>+ Fast cluster creation and testing | + Easy to use<br>+ Suitable for local development and testing<br>+ Works within Docker containers<br>+ Light alternative to Docker |
| **Cons**                                      | - Doubts about scalability<br>- Potential limitations | - Limited information on scalability<br>- Limited community documentation | - Limited documentation<br>- Potential scalability concerns | - Limited information on scalability<br>- Limited community documentation |

## Demonstration

minikube
![minikube](minikube.gif)

k3d
![k3d](k3d.gif)

kind
![kind](kind.gif)

## Conclusion

Overall, for the AsciiArtify startup PoC, it is recommended to use Minikube for general Kubernetes evaluation, Kind for isolated testing and development of components, and k3d for rapid prototyping and demonstration of functionality. 

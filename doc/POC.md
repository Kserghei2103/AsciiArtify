# Proof of Concept. ArgoCD

Based on the Concept testing results, deploying a Kubernetes cluster using the k3d tool is recommended. As for the Delivery and Deployment system for the testing environment, we'll opt for ArgoCD.

GOAL: To demonstrate the technical or conceptual viability of the idea and concept of utilizing ArgoCD as a Continuous Delivery (CD) tool. Let's prove that it is technically feasible to implement this idea.

We install the system and configure access to the ArgoCD graphical interface.

1. Let's prepare a separate local cluster for installing ArgoCD. Let's set it up:

   + k3d cluster create argo 
   + kubectl cluster-info
   + alias k=kubectl
   + k version
   + k get all -A

2. We will install ArgoCD using a script from the official [ArgoCD](https://argo-cd.readthedocs.io/en/stable/#quick-start) repository. First, we will create a namespace in which the system will be installed, then we will use the script (manifest) for installation and check the state of the system after installation:

   + kubectl create namespace argocd
   + k get ns
   + kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   + k get all -n argocd
   + k get pod -n argocd -w

3. Let's get access to the ArgoCD GUI interface.

       We use Port Forwarding using local port 8080. In the command, we refer to the svc/argocd-server service located in the namespace -n argocd. Kubectl will automatically find the service endpoint and set port forwarding from local port 8080 to remote port 443.

   + kubectl port-forward svc/argocd-server -n argocd 8080:443&

     ArgoCD works with https by default, so when we try to open 127.0.0.1:8080, we get a certificate error. Therefore, in a productive system, you need to install certificates and configure these points.

4. Obtaining a password Use the command to obtain a password, specify the secret file argocd-initial-admin-secret and the output format jsonpath="{.data.password}". This will return us a base64 encoded password, after which we will use the base64 -d command to return the password to plain text. Enter the received password and admin login into the ArgoCD Web interface.

   + k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo


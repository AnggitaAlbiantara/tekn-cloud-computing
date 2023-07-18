# Kubernetes Intro

## Step 1 : [Minikube Installation & Configuration](https://minikube.sigs.k8s.io/docs/start/)
1. Download Minikube Installer and run the installer for the latest release in [this link](https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe).<br>

2. Start Cluster by run a command prompt with administrator access and then type the following command ```minikube start```:<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/1.PNG)

3. Try Interact With The Cluster and then type the following command ```kubectl get po -A``` in the command prompt.<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/2.PNG)

4. Open a new terminal and type the following command ```minikube dashboard``` in the command prompt and then access in [this link](http://127.0.0.1:65355/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/#/workloads?namespace=default).<br>
![gb3-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4c1ec7c3f9011fa43bb4fafe03ddfd006a5feb58/minggu-12/3-1.PNG)
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/3.PNG)

## Step 2 : [Create a Deployment](https://kubernetes.io/docs/tutorials/hello-minikube/)

1. Type the following command ```kubectl create``` to create a Deployment that manages a Pod in the command prompt. The Pod runs a Container based on the provided Docker image.<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/4.PNG)

2. See the Deployment that was created earlier, with following this command ```kubectl get deployments``` in the command prompt.<br>
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/5.PNG)

3. See the Pod with following this command ```kubectl get pods``` in the command prompt.<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/6.PNG)

4. See the cluster events with following this command ```kubectl get events``` in the command prompt.<br>
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/7.PNG)

5. See the kubectl configuration with following this command ```kubectl config view``` in the command prompt.<br>
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/8.PNG)

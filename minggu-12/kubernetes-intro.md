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

## Step 2 : [Create a Deployment](https://kubernetes.io/docs/tutorials/hello-minikube/#create-a-deployment)

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

## Step 3 : [Create a Service](https://kubernetes.io/docs/tutorials/hello-minikube/#create-a-service)

1. Expose the Pod to the public internet using the ```kubectl expose``` command:<br>
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/9.PNG)<br>
The --type=LoadBalancer flag indicates that you want to expose your Service outside of the cluster.<br>
The application code inside the test image only listens on TCP port 8080. If you used kubectl expose to expose a different port, clients could not connect to that other port.

2. See the Service that was created earlier, with following this command ```kubectl get services``` in the command prompt.<br>
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/10.PNG)
On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On minikube, the LoadBalancer type makes the Service accessible through the minikube service command.

3. Run the following command ```minikube service hello-node``` in the command prompt, and opens up a browser window that serves your app and shows the app's response.<br>
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/11.PNG)<br>
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/12.PNG)

## Step 4 : [Enable add-ons](https://kubernetes.io/docs/tutorials/hello-minikube/#enable-addons)

1. View list the currently supported addons with following this command ```minikube addons list```:<br>
![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/13.PNG)

2. Enable an addons metrics server, with following this command ```minikube addons enable metrics-server```:<br>
![gb14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/14.PNG)

3. View the Pod and Service you created by installing that addon with following this command ```kubectl get pod,svc -n kube-system```:<br>
![gb15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/15.PNG)

4. Disable metrics server with following this command ```minikube addons disable metrics-server```:<br>
![gb16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/16.PNG)

## Step 5 : [Clean Up](https://kubernetes.io/docs/tutorials/hello-minikube/#clean-up)

1. Try to clean up the resources you created in your cluster, with following this command ```kubectl delete service hello-node & kubectl delete deployment hello-node```:<br>
![gb17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/17.PNG)<br>
![gb18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/18.PNG)

2. Stop the Minikube cluster with following this command ```minikube stop```.<br>
![gb19](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/19.PNG)

3. Optionally, delete the Minikube Virtual Machine with following this command ```minikube delete```:<br>
![gb20](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/83c07e4af729039a36c6fc517e195fb7d63c4401/minggu-12/20.PNG)

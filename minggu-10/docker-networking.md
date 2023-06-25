# Docker Networking Hands-on Lab

## Section #1 - Networking Basics

### Step 1: The Docker Network Command
The ```docker network``` command is the main command for configuring and managing container networks. Run the ```docker network``` command from the first terminal.<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/1.PNG)<br>
The command output shows how to use the command as well as all of the docker network sub-commands. As you can see from the output, the docker network command allows you to create new networks, list existing networks, inspect networks, and remove networks. It also allows you to connect and disconnect containers from networks.

### Step 2: List networks
Run a ```docker network ls``` command to view existing container networks on the current Docker host.<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/2.PNG)<br>
The output above shows the container networks that are created as part of a standard installation of Docker.
New networks that you create will also show up in the output of the docker network ls command.
You can see that each network gets a unique ID and NAME. Each network is also associated with a single driver. Notice that the “bridge” network and the “host” network have the same name as their respective drivers.

### Step 3: Inspect a network
The ```docker network inspect``` command is used to view network configuration details. Use ```docker network inspect <network>``` to view configuration details of the container networks on your Docker host. The command below shows the details of the network called ```bridge```.
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/3.PNG)<br>
![gb3-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/3-1.PNG)<br>
![gb3-2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/3-2.PNG)<br>

### Step 4: List network driver plugins
The ```docker info``` command shows a lot of interesting information about a Docker installation. Run the ```docker info``` command and locate the list of network plugins.<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/4.PNG)<br>
The output above shows the bridge, host,macvlan, null, and overlay drivers

## Section #2 - Bridge Networking

### Step 1: The Basics
Every clean installation of Docker comes with a pre-built network called bridge. Verify this with the docker ```network ls```.
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/5.PNG)<br>
The output above shows that the bridge network is associated with the bridge driver. It’s important to note that the network and the driver are connected, but they are not the same. In this example the network and the driver have the same name - but they are not the same thing!<br>

The output above also shows that the bridge network is scoped locally. This means that the network only exists on this Docker host. This is true of all networks using the bridge driver - the bridge driver provides single-host networking.
All networks created with the bridge driver are based on a Linux bridge (a.k.a. a virtual switch).<br>

Install the brctl command and use it to list the Linux bridges on your Docker host. You can do this by running sudo apt-get install bridge-utils.<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/6.PNG)<br>
Then, list the bridges on your Docker host, by running brctl show.<br>
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/7.PNG)<br>

The output above shows a single Linux bridge called docker0. This is the bridge that was automatically created for the bridge network. You can see that it has no interfaces currently connected to it.
You can also use the ip a command to view details of the docker0 bridge.<br>
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/8.PNG)<br>

### Step 2: Connect a container
The bridge network is the default network for new containers. This means that unless you specify a different network, all new containers will be connected to the bridge network. Create a new container by running ```docker run -dt ubuntu sleep infinity```. This command will create a new container based on the ```ubuntu:latest``` image and will run the ```sleep``` command to keep the container running in the background. You can verify our example container is up by running ```docker ps```.
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/9.PNG)<br>

This command will create a new container based on the ubuntu:latest image and will run the sleep command to keep the container running in the background. You can verify our example container is up by running docker ps.<br>
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/10.PNG)<br>

As no network was specified on the ```docker run``` command, the container will be added to the bridge network. Run the ```brctl show``` command again.<br>
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/11.PNG)<br>

Notice how the docker0 bridge now has an interface connected. This interface connects the docker0 bridge to the new container just created. You can inspect the bridge network again, by running ```docker network inspect bridge```, to see the new container attached to it.<br>
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/12.PNG)<br>
![gb12-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/12-1.PNG)<br>

### Step 3: Test network connectivity
The output to the previous docker network inspect command shows the IP address of the new container. In the previous example it is “172.17.0.2” but yours might be different.
Ping the IP address of the container from the shell prompt of your Docker host by running ping -c5 <IPv4 Address>. Remember to use the IP of the container in your environment.<br>
![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/13.PNG)<br>

The replies above show that the Docker host can ping the container over the bridge network. But, we can also verify the container can connect to the outside world too. Lets log into the container, install the ```ping program```, and then ping ```www.github.com```.
First, we need to get the ID of the container started in the previous step. You can run ``docker ps`` to get that. 
![gb14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/14.PNG)<br>

Next, lets run a shell inside that ubuntu container, by running ```docker exec -it <CONTAINER ID> /bin/bash```.<br>
![gb15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/15.PNG)<br>

Next, we need to install the ping program. So, lets run ```apt-get update && apt-get install -y iputils-ping```.<br>
![gb16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/16.PNG)<br>

Lets ping ```www.github.com``` by running ```ping -c5 www.github.com```.<br>
![gb17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/17.PNG)<br>

Finally, lets disconnect our shell from the container, by running ```exit```.<br>
![gb18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/18.PNG)<br>
We should also stop this container so we clean things up from this test, by running ```docker stop <CONTAINER ID>```.<br>
This shows that the new container can ping the internet and therefore has a valid and working network configuration.

### Step 4: Configure NAT for external connectivity
In this step we’ll start a new NGINX container and map port 8080 on the Docker host to port 80 inside of the container. This means that traffic that hits the Docker host on port 8080 will be passed on to port 80 inside the container.<br>
Start a new container based off the official NGINX image by running ```docker run --name web1 -d -p 8080:80 nginx```.<br>
![gb19](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/19.PNG)<br>

Review the container status and port mappings by running ```docker ps```.<br>
![gb20](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/20.PNG)<br>
The top line shows the new web1 container running NGINX. Take note of the command the container is running as well as the port mapping - 0.0.0.0:8080->80/tcp maps port 8080 on all host interfaces to port 80 inside the web1 container. This port mapping is what effectively makes the containers web service accessible from external sources (via the Docker hosts IP address on port 8080).

Now that the container is running and mapped to a port on a host interface you can test connectivity to the NGINX web server.

To complete the following task you will need the IP address of your Docker host. This will need to be an IP address that you can reach (e.g. your lab is hosted in Azure so this will be the instance’s Public IP - the one you SSH’d into). Just point your web browser to the IP and port 8080 of your Docker host. Also, if you try connecting to the same IP address on a different port number it will fail.

If for some reason you cannot open a session from a web broswer, you can connect from your Docker host using the curl 127.0.0.1:8080 command.<br>
![gb21](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/218dc073d7fae120bab0336082c637638dbfb60a/minggu-10/21.PNG)<br>

## Section #3 - Overlay Networking

### Step 1: The Basics
In this step you’ll initialize a new Swarm, join a single worker node, and verify the operations worked. Run ```docker swarm init --advertise-addr $(hostname -i)```. In the first terminal copy the entire ```docker swarm join ...``` command that is displayed as part of the output from your terminal output. Then, paste the copied command into the second terminal. Run a docker node ls to verify that both nodes are part of the Swarm.
<div><img src="gambar/SS16.png"></div><br>

### Step 2: Create an overlay network
Now that you have a Swarm initialized it’s time to create an overlay network. Create a new overlay network called “overnet” by running ```docker network create -d overlay overnet```. Use the ```docker network ls``` command to verify the network was created successfully. Run the same ```docker network ls``` command from the second terminal.
<div><img src="gambar/SS17.png"></div><br>

Notice that the “overnet” network does not appear in the list. This is because Docker only extends overlay networks to hosts when they are needed. This is usually when a host runs a task from a service that is created on the network. We will see this shortly.

Use the ```docker network inspect <network>``` command to view more detailed information about the “overnet” network. You will need to run this command from the first terminal.
<div><img src="gambar/SS18.png"></div><br>

### Step 3: Create a service
Now that we have a Swarm initialized and an overlay network, it’s time to create a service that uses the network.

Execute the following command from the first terminal to create a new service called myservice on the overnet network with two tasks/replicas.

```
docker service create --name myservice \
--network overnet \
--replicas 2 \
ubuntu sleep infinity
```

Verify that the service is created and both replicas are up by running ```docker service ls```.
<div><img src="gambar/SS19.png"></div><br>

The ```2/2``` in the ```REPLICAS``` column shows that both tasks in the service are up and running. Verify that a single task (replica) is running on each of the two nodes in the Swarm by running ```docker service ps myservice```.
<div><img src="gambar/SS20.png"></div><br>

We can also run ```docker network inspect overnet``` on the second terminal to get more detailed information about the “overnet” network and obtain the IP address of the task running on the second terminal.
<div><img src="gambar/SS21.png"></div><br>

### Step 4: Test the network
To complete this step you will need the IP address of the service task. Execute the following commands, ```docker network inspect overnet```. Notice that the IP address listed for the service task (container) running on the first node is different to the IP address for the service task running on the second node. Note also that they are on the same “overnet” network.
<div><img src="gambar/SS22.png"></div><br>

Run a ```docker ps``` command to get the ID of the service task so that you can log in to it in the next step. Log on to the service task. Be sure to use the container ```ID``` from your environment as it will be different from the example shown below. We can do this by running ```docker exec -it <CONTAINER ID> /bin/bash```. Install the ping command and ping the service task running on the both node.
<div><img src="gambar/SS23.png"></div><br>
<div><img src="gambar/SS24.png"></div><br>
The output above shows that both tasks from the myservice service are on the same overlay network spanning both nodes and that they can use this network to communicate.

### Step 5: Test service discovery

Run ```cat /etc/resolv.conf``` form inside of the container. The value that we are interested in is the ```nameserver 127.0.0.11```. This value sends all DNS queries from the container to an embedded DNS resolver running inside the container listening on ```127.0.0.11:53```. All Docker container run an embedded DNS server at this address. Try and ping the “myservice” name from within the container by running ```ping -c5 myservice```.
<div><img src="gambar/SS25.png"></div><br>

Type the ```exit``` command to leave the ```exec``` container session and return to the shell prompt of your Docker host. Inspect the configuration of the “myservice” service by running ```docker service inspect myservice```. Lets verify that the VIP value matches the value returned by the previous ```ping -c5 myservice``` command.
<div><img src="gambar/SS26.png"></div><br>

## Cleaning Up
Execute the ```docker service rm myservice``` command to remove the service called myservice. Execute the ```docker ps``` command to get a list of running containers. You can use the ```docker kill <CONTAINER ID ...>``` command to kill the ubuntu and nginx containers we started at the beginning.
<div><img src="gambar/SS27.png"></div><br>

Finally, lets remove node1 and node2 from the Swarm. We can use the ```docker swarm leave --force``` command to do that.
<div><img src="gambar/SS28.png"></div>
<div><img src="gambar/SS29.png"></div>

Congratulations! You’ve completed this lab!

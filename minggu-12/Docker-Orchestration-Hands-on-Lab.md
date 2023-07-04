# Docker Orchestration Hands-on Lab

### Steps

- [Section #1 - What is Orchestration](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#section-1-what-is-orchestration)
- [Section #2 - Configure Swarm Mode](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#section-2-configure-swarm-mode)
- [Section #3 - Deploy applications across multiple hosts](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#section-3-deploy-applications-across-multiple-hosts)
- [Section #4 - Scale the application](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#section-4-scale-the-application)
- [Section #5 - Drain a node and reschedule the containers](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#section-5-drain-a-node-and-reschedule-the-containers)
- [Cleaning Up](https://github.com/isaanggi/tekn-cloud-computing/new/main/minggu-12#cleaning-up)

## Section 1: What is Orchestration

So, what is Orchestration anyways? Well, Orchestration is probably best described using an example. Let’s say that you have an application that has high traffic along with high-availability requirements. Due to these requirements, you typically want to deploy across at least 3+ machines, so that in the event a host fails, your application will still be accessible from at least two others. Obviously, this is just an example and your use-case will likely have its own requirements, but you get the idea.

Deploying your application without Orchestration is typically very time consuming and error prone, because you would have to manually SSH into each machine, start up your application, and then continually keep tabs on things to make sure it is running as you expect.

But, with Orchestration tooling, you can typically off-load much of this manual work and let automation do the heavy lifting. One cool feature of Orchestration with Docker Swarm, is that you can deploy an application across many hosts with only a single command (once Swarm mode is enabled). Plus, if one of the supporting nodes dies in your Docker Swarm, other nodes will automatically pick up load, and your application will continue to hum along as usual.

If you are typically only using ```docker run``` to deploy your applications, then you could likely really benefit from using Docker Compose, Docker Swarm mode, or both Docker Compose and Swarm.

## Section 2: Configure Swarm Mode
Real-world applications are typically deployed across multiple hosts as discussed earlier. This improves application performance and availability, as well as allowing individual application components to scale independently. Docker has powerful native tools to help you do this.

An example of running things manually and on a single host would be to create a new container on <strong>node1</strong> by running ```docker run -dt ubuntu sleep infinity```.<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/1.PNG)

This command will create a new container based on the ```ubuntu:latest``` image and will run the ```sleep``` command to keep the container running in the background. You can verify our example container is up by running ```docker ps``` on <strong>node1</strong>.
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/2.PNG)

But, this is only on a single node. What happens if this node goes down? Well, our application just dies and it is never restarted. To restore service, we would have to manually log into this machine, and start tweaking things to get it back up and running. So, it would be helpful if we had some type of system that would allow us to run this “sleep” application/service across many machines.

In this section you will configure *Swarm Mode*. This is a new optional mode in which multiple Docker hosts form a self-orchestrating group of engines called a *swarm*. Swarm mode enables new features such as *services* and *bundles* that help you deploy and manage multi-container apps across multiple Docker hosts.

You will complete the following:
- Configure Swarm mode
- Run the app
- Scale the app
- Drain nodes for maintenance and reschedule containers

For the remainder of this lab we will refer to *Docker native clustering* as *<strong>Swarm mode</strong>*. The collection of Docker engines configured for Swarm mode will be referred to as the *swarm*.

A swarm comprises one or more *Manager Nodes* and one or more *Worker Nodes*. The manager nodes maintain the state of swarm and schedule application containers. The worker nodes run the application containers. As of Docker 1.12, no external backend, or 3rd party components, are required for a fully functioning swarm - everything is built-in!

In this part of the demo you will use all three of the nodes in your lab. <strong>node1</strong> will be the Swarm manager, while <strong>node2</strong> and <strong>node3</strong> will be worker nodes. Swarm mode supports highly available redundant manager nodes, but for the purposes of this lab you will only deploy a single manager node.

### Step 2.1 - Create a Manager node
In this step you’ll initialize a new Swarm, join a single worker node, and verify the operations worked.

Run ```docker swarm init``` on <strong>node1</strong>.<br>
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/3.PNG)

You can run the ```docker info``` command to verify that <strong>node1</strong> was successfully configured as a swarm manager node.<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/4.PNG)

The swarm is now initialized with <strong>node1</strong> as the only Manager node. In the next section you will add <strong>node2</strong> and <strong>node3</strong> as *Worker nodes*.

### Step 2.2 - Join Worker nodes to the Swarm
You will perform the following procedure on <strong>node2</strong> and <strong>node3</strong>. Towards the end of the procedure you will switch back to <strong>node1</strong>.

Now, take the entire ```docker swarm join ...``` command we copied earlier from ```node1``` where it was displayed as terminal output. We need to paste the copied command into the terminal of <strong>node2</strong> and <strong>node3</strong>.

It should look something like this for <strong>node2</strong>. By the way, if the ```docker swarm join ...``` command scrolled off your screen already, you can run the ```docker swarm join-token worker``` command on the Manager node to get it again.

``Remember, the tokens displayed here are not the actual tokens you will use. Copy the command from the output on node1. On node2 and node3 it should look like this:``<br>
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/5.PNG)<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/6.PNG)<br>
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/7.PNG)

Once you have run this on <strong>node2</strong> and <strong>node3</strong>, switch back to <strong>node1</strong>, and run a ```docker node ls``` to verify that both nodes are part of the Swarm. You should see three nodes, <strong>node1</strong> as the Manager node and <strong>node2</strong> and <strong>node3</strong> both as Worker nodes.<br>
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/8.PNG)

The ```docker node ls``` command shows you all of the nodes that are in the swarm as well as their roles in the swarm. The ```*``` identifies the node that you are issuing the command from.

Congratulations! You have configured a swarm with one manager node and two worker nodes.
## Section 3: Deploy applications across multiple hosts
Now that you have a swarm up and running, it is time to deploy our really simple sleep application.

You will perform the following procedure from <strong>node1</strong>.

### Step 3.1 - Deploy the application components as Docker services
Our ```sleep``` application is becoming very popular on the internet (due to hitting Reddit and HN). People just love it. So, you are going to have to scale your application to meet peak demand. You will have to do this across multiple hosts for high availability too. We will use the concept of *Services* to scale our application easily and manage many containers as a single entity.

``Services were a new concept in Docker 1.12. They work with swarms and are intended for long-running containers.``

You will perform this procedure from <strong>node1</strong>.

Let’s deploy ```sleep``` as a *Service* across our Docker Swarm.<br>
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/9.PNG)

Verify that the ```service create``` has been received by the Swarm manager.<br>
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5726e2bbb3b0af82e191b90b0dbc62245ec550eb/minggu-12/10.PNG)

The state of the service may change a couple times until it is running. The image is being downloaded from Docker Store to the other engines in the Swarm. Once the image is downloaded the container goes into a running state on one of the three nodes.

At this point it may not seem that we have done anything very differently than just running a ```docker run ....``` We have again deployed a single container on a single host. The difference here is that the container has been scheduled on a swarm cluster.

Well done. You have deployed the sleep-app to your new Swarm using Docker services.
## Section 4: Scale the application

<div><img src="gambar/ss9.jpg"></div>
<div><img src="gambar/ss10.jpg"></div>
<div><img src="gambar/ss11.jpg"></div>
<div><img src="gambar/ss12.jpg"></div>
<div><img src="gambar/ss13.jpg"></div>

## Section 5: Drain a node and reschedule the containers

<div><img src="gambar/ss14.jpg"></div>
<div><img src="gambar/ss15.jpg"></div>
<div><img src="gambar/ss16.jpg"></div>
<div><img src="gambar/ss17.jpg"></div>
<div><img src="gambar/ss18.jpg"></div>
<div><img src="gambar/ss19.jpg"></div>
<div><img src="gambar/ss20.jpg"></div>

## Cleaning Up

<div><img src="gambar/ss21.jpg"></div>
<div><img src="gambar/ss22.jpg"></div>
<div><img src="gambar/ss23.jpg"></div>
<div><img src="gambar/ss24.jpg"></div>
<div><img src="gambar/ss25.jpg"></div>
<div><img src="gambar/ss26.jpg"></div>

Congratulations! You’ve completed this lab. You now know how to build a swarm, deploy applications as collections of services, and scale individual services up and down.

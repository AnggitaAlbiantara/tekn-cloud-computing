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

<div><img src="gambar/ss6.jpg"></div>
<div><img src="gambar/ss7.jpg"></div>

## Section 3: Deploy applications across multiple hosts

### Step 3.1 - Deploy the application components as Docker services

<div><img src="gambar/ss8.jpg"></div>

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

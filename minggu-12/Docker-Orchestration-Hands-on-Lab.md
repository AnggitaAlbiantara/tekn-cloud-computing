# Docker Orchestration Hands-on Lab

Laporan beserta gambar dibawah ini adalah hasil praktikum melalui [Docker Orchestration Hands-on Lab](https://training.play-with-docker.com/orchestration-hol/), sehingga untuk materi dan penjelasan lebih detailnya dapat diakses melalui web tersebut.

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

<div><img src="gambar/ss1.jpg"></div>

## Section 2: Configure Swarm Mode

<div><img src="gambar/ss2.jpg"></div>
<div><img src="gambar/ss3.jpg"></div>

### Step 2.1 - Create a Manager node

<div><img src="gambar/ss4.jpg"></div>
<div><img src="gambar/ss5.jpg"></div>

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

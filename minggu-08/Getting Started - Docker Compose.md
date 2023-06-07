# Getting Started - Docker Compose

## Prerequisites <br>
You need to have Docker Engine and Docker Compose on your machine. You can either: <br>

- Install Docker Engine and Docker Compose as standalone binaries 
- Install Docker Desktop which includes both Docker Engine and Docker Compose 

You don’t need to install Python or Redis, as both are provided by Docker images.<br>

## Step 1: Define the application dependencies<br>

1. Create a directory for the project:<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%201.PNG)<br>

2. Create a file called app.py in your project directory.<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%202.PNG)<br>

3. Create another file called requirements.txt in your project directory.<br>
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%203.PNG)<br>

## Step 2: Create a Dockerfile<br>

1. In your project directory, create a file named Dockerfile.<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%204.PNG)<br>

## Step 3: Define services in a Compose file<br>

1. Create a file called docker-compose.yml in your project directory.<br>
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%205.PNG)<br>

2. Finally, the files in your project directory will be like this. <br>

## Step 4: Build and run your app with Compose<br>

1. From your project directory, start up your application by running docker compose up.<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%206.PNG)<br>

2. Enter http://localhost:8000/ in a browser to see the application running.<br>

![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%207.PNG)<br>

3. Refresh the page. The number should increment.<br>

![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%208.PNG)<br>

4. Switch to another terminal window, and type docker image ls to list local images.<br>

![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%209.PNG)<br>

5. Stop the application, either by running docker compose down from within your project directory in the second terminal, or by hitting CTRL+C in the original terminal where you started the app. <br>

## Step 5: Edit the Compose file to add a bind mount<br>

1. Edit docker-compose.yml in your project directory to add a bind mount for the web service.<br>
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2010.PNG)<br>

## Step 6: Re-build and run the app with Compose <br>

1. From your project directory, type docker compose up to build the app with the updated Compose file, and run it. <br>
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2011.PNG)<br>

2. Check the Hello World message in a web browser again, and refresh to see the count increment.<br>
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2012.PNG)<br>

## Step 7: Update the application <br>

1. Because the application code is now mounted into the container using a volume, you can make changes to its code and see the changes instantly, without having to rebuild the image. Change the greeting in app.py and save it. For example, change the Hello World! message to Hello from Docker!.<br>
![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2013.PNG)<br>
![gb14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2014.PNG)<br>

## Step 8: Experiment with some other commands

1. If you want to run your services in the background, you can pass the -d flag (for “detached” mode) to docker compose up and use docker compose ps to see what is currently running. <br>
![gb15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2015.PNG)<br>

2. The docker compose run command allows you to run one-off commands for your services. For example, to see what environment variables are available to the web service. <br>
![gb16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2016.PNG)<br>

3. If you started Compose with docker compose up -d, stop your services once you’ve finished with them. <br>
![gb17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2017.PNG)<br>

4. You can bring everything down, removing the containers entirely, with the down command. Pass --volumes to also remove the data volume used by the Redis container. <br>
![gb18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/54575accb6f57d3f6fef78d6b17e02ec563c4cc1/minggu-08/Lat%2018.PNG)<br>

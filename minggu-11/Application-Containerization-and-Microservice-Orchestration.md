# Application Containerization and Microservice Orchestration

Laporan beserta gambar dibawah ini adalah hasil praktikum melalui [Application Containerization and Microservice Orchestration](https://training.play-with-docker.com/microservice-orchestration/), sehingga untuk materi dan penjelasan lebih detailnya dapat diakses melalui web tersebut.

### Steps

- [Stage Setup](app-containerization-orchestration.md#stage-setup)
- [Step 0: Basic Link Extractor Script](app-containerization-orchestration.md#step-0-basic-link-extractor-script)
- [Step 1: Containerized Link Extractor Script](app-containerization-orchestration.md#step-1-containerized-link-extractor-script)
- [Step 2: Link Extractor Module with Full URI and Anchor Text](app-containerization-orchestration.md#step-2-link-extractor-module-with-full-uri-and-anchor-text)
- [Step 3: Link Extractor API Service](app-containerization-orchestration.md#step-3-link-extractor-api-service)
- [Step 4: Link Extractor API and Web Front End Services](app-containerization-orchestration.md#step-4-link-extractor-api-and-web-front-end-services)
- [Step 5: Redis Service for Caching](app-containerization-orchestration.md#step-5-redis-service-for-caching)
- [Step 6: Swap Python API Service with Ruby](app-containerization-orchestration.md#step-6-swap-python-api-service-with-ruby)
- [Conclusions](app-containerization-orchestration.md#conclusions)

## Stage Setup

Let’s get started by first cloning the demo code repository, changing the working directory, and checking the ```demo``` branch out.<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/1.PNG)

## Step 0: Basic Link Extractor Script

Checkout the ```step0``` branch and list files in it.<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/2.PNG)

The ```linkextractor.py``` file is the interesting one here, so let’s look at its contents: <br>
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/3.PNG)<br>
This is a simple Python script that imports three packages: sys from the standard library and two popular third-party packages requests and bs4. User-supplied command line argument (which is expected to be a URL to an HTML page) is used to fetch the page using the requests package, then parsed using the BeautifulSoup. The parsed object is then iterated over to find all the anchor elements (i.e., <a> tags) and print the value of their href attribute that contains the hyperlink.<br>

However, this seemingly simple script might not be the easiest one to run on a machine that does not meet its requirements. The ```README.md``` file suggests how to run it, so let’s give it a try.<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/4.PNG)

When we tried to execute it as a script, we got the ```Permission denied``` error. Let’s check the current permissions on this file.<br>
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/5.PNG)

This current permission ```-rw-r--r--``` indicates that the script is not set to be executable. We can either change it by running ```chmod a+x linkextractor.py``` or run it as a Python program instead of a self-executing script as illustrated below:<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/6.PNG)

Here we got the first ```ImportError``` message because we are missing the third-party package needed by the script. We can install that Python package (and potentially other missing packages) using one of the many techniques to make it work, but it is too much work for such a simple script, which might not be obvious for those who are not familiar with Python’s ecosystem.<br>
Depending on which machine and operating system you are trying to run this script on, what software is already installed, and how much access you have, you might face some of these potential difficulties:
- Is the script executable?
- Is Python installed on the machine?
- Can you install software on the machine?
- Is pip installed?
- Are requests and beautifulsoup4 Python libraries installed?

This is where application containerization tools like Docker come in handy. In the next step we will try to containerize this script and make it easier to execute.

## Step 1: Containerized Link Extractor Script

Checkout the ```step1``` branch and list files in it.<br>
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/7.PNG)

We have added one new file (i.e., ```Dockerfile```) in this step. Let’s look into its contents:<br>
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/8.PNG)<br>
Using this Dockerfile we can prepare a Docker image for this script. We start from the official python Docker image that contains Python’s run-time environment as well as necessary tools to install Python packages and dependencies. We then add some metadata as labels (this step is not essential, but is a good practice nonetheless). Next two instructions run the pip install command to install the two third-party packages needed for the script to function properly. We then create a working directory /app, copy the linkextractor.py file in it, and change its permissions to make it an executable script. Finally, we set the script as the entrypoint for the image.

Using this ```Dockerfile``` we can prepare a Docker image for this script.<br>
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/9.PNG)

So far, we have just described how we want our Docker image to be like, but didn’t really build one. So let’s do just that:<br>
This command should yield an output as illustrated below:<br>
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/10.PNG)

We have created a Docker image named ```linkextractor:step1``` based on the ```Dockerfile``` illustrated above. If the build was successful, we should be able to see it in the list of image:<br>
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/11.PNG)

This image should have all the necessary ingredients packaged in it to run the script anywhere on a machine that supports Docker. Now, let’s run a one-off container with this image and extract links from some live web pages:<br>
This outputs a single link that is present in the simple ```example.com``` web page.<br>
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/11.PNG)

Let’s try it on a web page with more links in it:<br>
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/12.PNG)<br>
This looks good, but we can improve the output. For example, some links are relative, we can convert them into full URLs and also provide the anchor text they are linked to. In the next step we will make these changes and some other improvements to the script.

## Step 2: Link Extractor Module with Full URI and Anchor Text

Checkout the step2 branch and list files in it.<br>
![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/13.PNG)

In this step the ```linkextractor.py``` script is updated with the following functional changes. 
- Paths are normalized to full URLs
- Reporting both links and anchor texts
- Usable as a module in other scripts

Let’s have a look at the updated script.<br>
![gb14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/14.PNG)

The link extraction logic is abstracted into a function ```extract_links``` that accepts a URL as a parameter and returns a list of objects containing anchor texts and normalized hyperlinks. This functionality can now be imported into other scripts as a module (which we will utilize in the next step).<br>

Now, let’s build a new image and see these changes in effect:
![gb15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/15.PNG)

We have used a new tag ```linkextractor:step2``` for this image so that we don’t overwrite the image from ```the step1``` to illustrate that they can co-exist and containers can be run using either of these images.<br>
![gb16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/16.PNG)

Running a one-off container using the ```linkextractor:step2``` image should now yield an improved output:
![gb17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/17.PNG)

Running a container using the previous image ```linkextractor:step1``` should still result in the old output:<br>
![gb18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/18.PNG)

So far, we have learned how to containerize a script with its necessary dependencies to make it more portable. We have also learned how to make changes in the application and build different variants of Docker images that can co-exist. In the next step we will build a web service that will utilize this script and will make the service run inside a Docker container.

## Step 3: Link Extractor API Service

Checkout the ```step3``` branch and list files in it.<br>
![gb19](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/19.PNG)

The following changes have been made in this step:
- Added a server script ```main.py``` that utilizes the link extraction module written in the last step
- The ```Dockerfile``` is updated to refer to the ```main.py``` file instead
- Server is accessible as a WEB API at ```http://<hostname>[:<prt>]/api/<url>```
- Dependencies are moved to the ```requirements.txt``` file
- Needs port mapping to make the service accessible outside of the container (the ```Flask``` server used here listens on port ```5000``` by default)

Let’s first look at the ```Dockerfile``` for changes:<br>
![gb20](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/20.PNG)

Since we have started using ```requirements.txt``` for dependencies, we no longer need to run ```pip install``` command for individual packages. The ```ENTRYPOINT``` directive is replaced with the ```CMD``` and it is referring to the ```main.py``` script that has the server code it because we do not want to use this image for one-off commands now.

The ```linkextractor.py``` module remains unchanged in this step, so let’s look into the newly added ```main.py``` file:
![gb21](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/21.PNG)

Here, we are importing ```extract_links``` function from the ```linkextractor``` module and converting the returned list of objects into a JSON response.<br>
It’s time to build a new image with these changes in place:
![gb22](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/22.PNG)

Then run the container in detached mode (```-d``` flag) so that the terminal is available for other commands while the container is still running. Note that we are mapping the port ```5000``` of the container with the ```5000``` of the host (using ```-p 5000:5000``` argument) to make it accessible from the host. We are also assigning a name (```--name=linkextractor```) to the container to make it easier to see logs and kill or remove the container.<br>
![gb23](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/23.PNG)

If things go well, we should be able to see the container being listed in ```Up``` condition:<br>
![gb24](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/24.PNG)

We can now make an HTTP request in the form ```/api/<url>``` to talk to this server and fetch the response containing extracted links:<br>
![gb25](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/25.PNG)

Now, we have the API service running that accepts requests in the form ```/api/<url>``` and responds with a JSON containing hyperlinks and anchor texts of all the links present in the web page at give ```<url>```.<br>

Since the container is running in detached mode, so we can’t see what’s happening inside, but we can see logs using the name ```linkextractor``` we assigned to our container:
![gb26](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/26.PNG)

We can see the messages logged when the server came up, and an entry of the request log when we ran the ```curl``` command. Now we can kill and remove this container.<br>
![gb27](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/27.PNG)

In this step we have successfully ran an API service listening on port ```5000```. This is great, but APIs and JSON responses are for machines, so in the next step we will run a web service with a human-friendly web interface in addition to this API service.

## Step 4: Link Extractor API and Web Front End Services

Checkout the ```step4``` branch and list files in it.<br>
![gb28](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/28.PNG)

In this step the following changes have been made since the last step:
- The link extractor JSON API service (written in Python) is moved in a separate ```./api``` folder that has the exact same code as in the previous step
- A web front-end application is written in PHP under ```./www``` folder that talks to the JSON API
- The PHP application is mounted inside the official ```php:7-apache``` Docker image for easier modification during the development
- The web application is made accessible at ```http://<hostname>[:<prt>]/?url=<url-encoded-url>```
- An environment variable ```API_ENDPOINT``` is used inside the PHP application to configure it to talk to the JSON API server
- A ```docker-compose.yml``` file is written to build various components and glue them together

In this step we are planning to run two separate containers, one for the API and the other for the web interface. The latter needs a way to talk to the API server. For the two containers to be able to talk to each other, we can either map their ports on the host machine and use that for request routing or we can place the containers in a single private network and access directly. Docker has excellent support for networking and provides helpful commands for dealing with networks. Additionally, in a Docker network containers identify themselves using their names as hostnames to avoid hunting for their IP addresses in the private network. However, we are not going to do any of this manually, instead we will be using Docker Compose to automate many of these tasks.

So let’s look at the ```docker-compose.yml``` file we have:<br>
![gb29](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/29.PNG)

This is a simple YAML file that describes the two services ```api``` and ```web```. The ```api``` service will use the ```linkextractor-api:step4-python``` image that is not built yet, but will be built on-demand using the ```Dockerfile``` from the ```./api``` directory. This service will be exposed on the port ```5000``` of the host.

The second service named ```web``` will use official ```php:7-apache``` image directly from the DockerHub, that’s why we do not have a ```Dockerfile``` for it. The service will be exposed on the default HTTP port (i.e., ```80```). We will supply an environment variable named ```API_ENDPOINT``` with the value ```http://api:5000/api/``` to tell the PHP script where to connect to for the API access. Notice that we are not using an IP address here, instead, ```api:5000``` is being used because we will have a dynamic hostname entry in the private network for the API service matching its service name. Finally, we will bind mount the ```./www``` folder to make the ```index.php``` file available inside of the ```web``` service container at ```/var/www/html```, which is the default web root for the Apache web server.

Now, let’s have a look at the user-facing ```www/index.php``` file:<br>

This is a long file that mainly contains all the markup and styles of the page. However, the important block of code is in the beginning of the file as illustrated below:<br>
![gb30](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/30.PNG)

The ```$api_endpoint``` variable is initialized with the value of the environment variable supplied from the ```docker-compose.yml``` file as ```$_ENV["API_ENDPOINT"]``` (otherwise falls back to a default value of ```http://localhost:5000/api/```). The request is made using ```file_get_contents``` function that uses the ```$api_endpoint``` variable and user supplied URL from ```$_GET["url"]```. Some analysis and transformations are performed on the received response that are later used in the markup to populate the page.

Let’s bring these services up in detached mode using ```docker-compose``` utility.<br>
![gb31](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/31.PNG)<br>
This output shows that Docker Compose automatically created a network named ```linkextractor_default```, pulled ```php:7-apache``` image from DockerHub, built ```api:python``` image using our local ```Dockerfile```, and finally, spun two containers ```linkextractor_web_1``` and ```linkextractor_api_1``` that correspond to the two services we have defined in the YAML file above.<br>

Checking for the list of running containers confirms that the two services are indeed running:<br>
![gb32](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/32.PNG)

We should now be able to talk to the API service as before:<br>
![gb33](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/33.PNG)<br>

To access the web interface [click to open the Link Extractor](https://training.play-with-docker.com/). Then fill the form with ```https://training.play-with-docker.com/``` (or any HTML page URL of your choice) and submit to extract links from it.
![gb35](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/013d9de96103b3d39c0d8f6628d010e2cac6a614/minggu-11/35-1.png)<br>

We have just created an application with microservice architecture, isolating individual tasks in separate services as opposed to monolithic applications where everything is put together in a single unit. Microservice applications are relatively easier to scale, maintains, and move around. They also allow easy swapping of components with an equivalent service. More on that later.

Now, let’s modify the ```www/index.php``` file to replace all occurrences of ```Link Extractor``` with ```Super Link Extractor``` :
![gb34](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/34.PNG)<br>

Reloading the web interface of the application (or [clicking here](https://training.play-with-docker.com/)) should now reflect this change in the title, header, and footer. This is happening because the ```./www``` folder is bind mounted inside of the container, so any changes made outside will reflect inside the container or the vice versa. This approach is very helpful in development, but in the production environment we would prefer our Docker images to be self-contained. 
![gb35-2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/013d9de96103b3d39c0d8f6628d010e2cac6a614/minggu-11/35-2.png)

Let’s revert these changes now to clean the Git tracking:<br>
![gb36](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/36.PNG)<br>
![gb36-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/013d9de96103b3d39c0d8f6628d010e2cac6a614/minggu-11/36-1.png)<br>

Before we move on to the next step we need to shut these services down, but Docker Compose can help us take care of it very easily:
![gb37](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/37.PNG)<br>

In the next step we will add one more service to our stack and will build a self-contained custom image for our web interface service.

## Step 5: Redis Service for Caching

Checkout the ```step5``` branch and list files in it.<br>
![gb38](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/38.PNG)<br>
Some noticeable changes from the previous step are as following:
- Another ```Dockerfile``` is added in the ```./www``` folder for the PHP web application to build a self-contained image and avoid live file mounting
- A Redis container is added for caching using the official Redis Docker image
- The API service talks to the Redis service to avoid downloading and parsing pages that were already scraped before
- A ```REDIS_URL``` environment variable is added to the API service to allow it to connect to the Redis cache

Let’s first inspect the newly added ```Dockerfile``` under the ```./www``` folder:<br>
![gb39](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/39.PNG)

This is a rather simple ```Dockerfile``` that uses the official ```php:7-apache``` image as the base and copies all the files from the ```./www``` folder into the ```/var/www/html/``` folder of the image. This is exactly what was happening in the previous step, but that was bind mounted using a volume, while here we are making the code part of the self-contained image. We have also added the ```API_ENDPOINT``` environment variable here with a default value, which implicitly suggests that this is an important information that needs to be present in order for the service to function properly (and should be customized at run time with an appropriate value).

Next, we will look at the API server’s ```api/main.py``` file where we are utilizing the Redis cache:<br>
The file has many lines, but the important bits are as illustrated below:<br>
![gb40](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/40.PNG)

This time the API service needs to know how to connect to the Redis instance as it is going to use it for caching. This information can be made available at run time using the ```REDIS_URL``` environment variable. A corresponding ```ENV``` entry is also added in the ```Dockerfile``` of the API service with a default value.

A ```redis``` client instance is created using the hostname ```redis``` (same as the name of the service as we will see later) and the default Redis port ```6379```. We are first trying to see if a cache is present in the Redis store for a given URL, if not then we use the ```extract_links``` function as before and populate the cache for future attempts.

Now, let’s look into the updated ```docker-compose.yml``` file:<br>
![gb41](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/41.PNG)

The ```api``` service configuration largely remains the same as before, except the updated image tag and added environment variable ```REDIS_URL``` that points to the Redis service. For the ```web``` service, we are using the custom ```linkextractor-web:step5-php``` image that will be built using the newly added ```Dockerfile``` in the ```./www``` folder. We are no longer mounting the ```./www``` folder using the ```volumes``` config. Finally, a new service named ```redis``` is added that will use the official image from DockerHub and needs no specific configurations for now. This service is accessible to the Python API using its service name, the same way the API service is accessible to the PHP front-end service.

Let’s boot these services up:<br>
![gb42](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/42.PNG)

Now, that all three services are up, access the web interface by [clicking the Link Extractor](https://training.play-with-docker.com/). There should be no visual difference from the previous step. However, if you extract links from a page with a lot of links, the first time it should take longer, but the successive attempts to the same page should return the response fairly quickly. To check whether or not the Redis service is being utilized, we can use ```docker-compose exec``` followed by the ```redis``` service name and the Redis CLI’s [monitor](https://redis.io/commands/monitor) command:<br>
![gb43](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/43.PNG)

Now, try to extract links from some web pages using the web interface and see the difference in Redis log entries for pages that are scraped the first time and those that are repeated. Before continuing further with the tutorial, stop the interactive ```monitor``` stream as a result of the above ```redis-cli``` command by pressing ```Ctrl + C``` keys while the interactive terminal is in focus.<br>
![gb44-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c2f2ec77685a6ab7c9a306713d63ae7ad874dbbb/minggu-11/44-1.png)<br>
![gb44-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c2f2ec77685a6ab7c9a306713d63ae7ad874dbbb/minggu-11/44-1.png)

Now that we are not mounting the ```/www``` folder inside the container, local changes should not reflect in the running service:<br>
![gb45](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/45.PNG)<br>
![gb45-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c2f2ec77685a6ab7c9a306713d63ae7ad874dbbb/minggu-11/45-1.png)

Verify that the changes made locally do not reflect in the running service by reloading the web interface and then revert changes:<br>
![gb46](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/46.PNG)<br>
![gb46-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c2f2ec77685a6ab7c9a306713d63ae7ad874dbbb/minggu-11/46-1.png)

Now, shut these services down and get ready for the next step:
![gb47](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/47.PNG)<br>

We have successfully orchestrated three microservices to compose our Link Extractor application. We now have an application stack that represents the architecture illustrated in the figure shown in the introduction of this tutorial. In the next step we will explore how easy it is to swap components from an application with the microservice architecture.

## Step 6: Swap Python API Service with Ruby

Checkout the step6 branch and list files in it.<br>
![gb48](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/48.PNG)<br>

Some significant changes from the previous step include:
- The API service written in Python is replaced with a similar Ruby implementation
- The ```API_ENDPOINT``` environment variable is updated to point to the new Ruby API service
- The link extraction cache event (HIT/MISS) is logged and is persisted using volumes

Notice that the ```./api``` folder does not contain any Python scripts, instead, it now has a Ruby file and a ```Gemfile``` to manage dependencies.

Let’s have a quick walk through the changed files:<br>
![gb49](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/49.PNG)<br>

This Ruby file is almost equivalent to what we had in Python before, except, in addition to that it also logs the link extraction requests and corresponding cache events. In a microservice architecture application swapping components with an equivalent one is easy as long as the expectations of consumers of the component are maintained.<br>
![gb50](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/50.PNG)<br>

Above Dockerfile is written for the Ruby script and it is pretty much self-explanatory.<br>
![gb51](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/51.PNG)<br>

The ```docker-compose.yml``` file has a few minor changes in it. The ```api``` service image is now named ```linkextractor-api:step6-ruby```, the port mapping is changed from ```5000``` to ```4567``` (which is the default port for Sinatra server), and the `API_ENDPOINT` environment variable in the ```web``` service is updated accordingly so that the PHP code can talk to it.

With these in place, let’s boot our service stack:<br>
![gb52](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/52.PNG)<br>

We should now be able to access the API (using the updated port number):<br>
![gb53](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/53.PNG)<br>

Now, open the web interface by [clicking the Link Extractor](https://training.play-with-docker.com/) and extract links of a few URLs. Also, try to repeat these attempts for some URLs. Also, try to repeat these attempts for some URLs. If everything is alright, the web application should behave as before without noticing any changes in the API service (which is completely replaced).

We can use the ```tail``` command with the ```-f``` or ```--follow``` option to follow the log output live.<br>
![gb54](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/54.PNG)<br>
![gb55-1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c2f2ec77685a6ab7c9a306713d63ae7ad874dbbb/minggu-11/55-1.png)

Try a few more URLs in the web interface. You should see the new log entries appear in the terminal.<br>
To stop following the log, press ```Ctrl + C``` keys while the interactive terminal is in focus.<br>
We can shut the stack down now:<br>
![gb56](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/56.PNG)<br>

Since we have persisted logs, they should still be available after the services are gone:<br>
![gb57](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/6d00c22b7522e0eb3b28de4b6ddd257719015837/minggu-11/57.PNG)<br>

This illustrates that the caching is functional as the second attempt to the ```http://example.com/``` resulted in a cache ```HIT```.

In this step we explored the possibility of swapping components of an application with microservice architecture with their equivalents without impacting rest of the parts of the stack. We have also explored data persistence using bind mount volumes that persists even after the containers writing to the volume are gone.

So far, we have used ```docker-compose``` utility to orchestrate the application stack, which is good for development environment, but for production environment we use ```docker stack deploy``` command to run the application in a [Docker Swarm Cluster](https://training.play-with-docker.com/swarm-stack-intro).

## Conclusions

We started this tutorial with a simple Python script that scrapes links from a given web page URL. We demonstrated various difficulties in running the script. We then illustrated how easy to run and portable the script becomes onces it is containerized. In the later steps we gradually evolved the script into a multi-service application stack. In the process we explored various concepts of microservice architecture and how Docker tools can be helpful in orchestrating a multi-service stack. Finally, we demonstrated the ease of microservice component swapping and data persistence.

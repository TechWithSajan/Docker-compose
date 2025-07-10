# docker-compose

Tutorial: [Get started with Docker Compose](https://docs.docker.com/compose/gettingstarted/)

## How can I start my services in the background?

```bash
docker compose up -d
```

## How can I see what environment variables are available to the $SERVICE service defined in my docker-compose file?

```bash
SERVICE=web
docker compose run $SERVICE env
```

Note how this creates a container and then exists
```
$ docker ps -a
CONTAINER ID   IMAGE                COMMAND                  CREATED          STATUS                     PORTS     NAMES
0352eb7204cf   docker-compose_web   "env"                    2 seconds ago    Exited (0) 1 second ago              docker-compose_web_run_cf43592bca36
567aa67651ab   docker-compose_web   "env"                    3 minutes ago    Exited (0) 3 minutes ago             docker-compose_web_run_a506a07db24
```

## How can I stop services running in the background?

```
docker compose stop
```

## How can I bring everything down, removing the containers entirely? What if I also want to remove the data volume?

```
docker compose down
```
And to also remove the data volume:
```bash
docker compose down --volumes
```

## Will stopping (ctrl+C or `docker compose stop`) remove containers?

No, the containers just exit. `docker compose down` will remove the containers. The stopped container is why the counter will remain the same when runing `docker compose up` in a loop while stopping it each time, the data remains the redis container.

====================================================================================================================================================================================

Install Docker Compose in Linux
We can download the binary file for Docker Compose in the Linux machine from the following GitHub link . The latest stable version of Docker Compose is 1.29.0. We will use the curl command to download this release. 1. Let’s run the below curl command which will allow us to download the latest stable version 1.29.0 of Docker Compose.

$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose


2. Next, we need to give the binary file, permissions to execute.

$ sudo chmod +x /usr/local/bin/docker-compose


3. In case the docker-compose command does not execute after installation, we need to make sure that the installation path is correct. Or we can simply create a symbolic link to the following path - /usr/bin

$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
4. After we have completed all these steps, we are now set to run our first Docker Compose command. Let’s try to verify the installation by checking the version.

$ docker-compose --version


Alternative Methods to install Docker Compose
In case you are not able to install Docker Compose using the above methods, there are two alternative methods that you can use. The first one is installing the Docker Compose tool using the pip command and the second one is installing it as a container.

Method 1:
We can easily install Docker Compose from the PyPI. However, it is recommended that if we opt for this method to install Docker Compose, we should create a virtual environment to do so because there are many conflicts between python system packages and the dependencies that Docker Compose requires. To install Docker Compose using pip, we can use the following command.

$ pip install docker-compose
Method 2
The next alternative option is to install Docker Compose inside a container. We can do so using a simple bash script. To do so, we can use the following commands.

$ sudo curl -L --fail https://github.com/docker/compose/releases/download/1.29.0/run.sh -o /usr/local/bin/docker-compose
This will download the bash script from the GitHub link and move it to the target path. Next, we need to provide execute permissions to this.

$ sudo chmod +x /usr/local/bin/docker-compose
How to uninstall Docker Compose?
If you installed Docker Compose using the curl command, you can simply remove the docker-compose binary from the path using the following command. sudo rm /usr/local/bin/docker-compose If you had installed Docker Compose using the pip command, you can use pip uninstall command to remove it.

$ pip uninstall docker-compose
Wrapping Up!
To conclude, in this article, we discussed how to install Docker Compose in Linux. We discussed three different methods to do so.

Using the curl command to download the binary.
Installing from PyPI using pip command.
Running Docker Compose inside a Container.
Finally, we also saw how we can uninstall Docker Compose in Linux. We certainly hope that with the help of this article, you will be able to get started with Docker Compose seamlessly. Happy Learning!

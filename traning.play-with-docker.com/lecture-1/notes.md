# Introduction:
This lecture explains the following 3 concepts
1. Running Simple Docker Commands
2. Run a Web Application in Docker
3. Modifying the customer Web Application in Docker

## Simple Docker Commands:
To run a container you can simply type
```
docker container run image_name 
```
This is run a container. It will close if the container has no function. Resources are not released from docker until explicitly being told. We can tell docker to romve a contianer by running it with `--rm` flag. 
To Run an interactive session of docker we can use the following command
```
docker container --interactive --tty --rm image_name bash
```
- **--interative**: To run an interactive session of the container.
- **--rm**: Remove the container when exited.
- **--tty**: Is to pass the data to the terminal. This is a lunix built in command
- **bash**: Is to access the bash terminal, if it is supported by the image that we have requested.

Running a MySql in the background
```
docker conatiner run --deatch --name mysql_local -e MYSQL_ROOT_PASSWORD=pass mysql:latest
```
This company will create a mysql database with the latest version available in the docker image. Explains of each flag in the command
- **--detach**: This is the run the conatiner in detach mode. Short hand for this flag is also **-d**.
- **--name**: This sets the name of the container 
- **-e**: This is to set environment variables in the container running
The last part of the command is the actual **mysql** images with the **Latest** tag.

To check the logs of a container
```
docker container logs container_name
```

To exec a command directly in the container we can use `exec` flag in the docker command
```
docker exec -it container_name command
docker exec -it mysql_local mysql --user=root --password=$MYSQL_ROOT_PASSWORD --version
```

## Creating Web App in Docker:

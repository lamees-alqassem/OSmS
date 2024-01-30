# OsmS: Microservice Platform
The platform can run all microservices using the docker-compose YML file located in the main directory of the framework folder. There are two docker-compose files:
1. 'docker-compose': it runs all main microservice containers of the platform
2. 'docker-compose-eval': it runs the evaluation microservices to monitor the resource usage of all running containers and display their usage in graphs.
All other forlders are for the Python Flask web application and load testing (i.e., Locust). 
## To start the platform:
1.  To get the containers running, build the images and then start the services:
   ```console
docker-compose up --build -d
```
2. After you run the previuos command, for thr first time ONLY, run the following command first to build the database tables: (use one of these two commands)
 ```console
   docker-compose run web -m  app.create_db
```
```console
docker-compose run web /bin/bash -c " python -c 'from app.app import db, create_app;db.create_all(app=create_app())'
```
3. To access the web page that is running on the local host of your machine:
```console
http://localhost:5000
```
Now the Web app and all microservices are running. If you face an issue especially with nginx, then this means that you need to edit the nginx.conf file located in nginx folder as follows:
```console
<project directory name>_<service name>
```
## Other usefull commands to scale, get information of running containers and inspect them:
1. To scale a service in Docker-compose:
    ```console
   docker-compose scale <service name> = <no of instances> 
```
                    OR
```console
docker-compose up --scale <service name> = <no of instances> -d
```
                            OR 
  ```console
docker-compose up --build --scale <service name> = <no of instances> -d
```
2. To see inside container
 ```console
   docker logs container name -f
```

3. get names of running containers:
```console
docker ps --format '{{.Names}}'
```

## For evaluation and load testing:
The instructions and commands are available in 'Evaluation_Commands_and_Instructions.txt' file. 

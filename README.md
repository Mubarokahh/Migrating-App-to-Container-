 # MIGRATING TO THE CLOUD WITH CONTAINERIZATION
In this project,when i talk about containers, I imply docker. Although there are other containerization technology,docker is the standard tool for deploying application its dependencies and configuration in a sandbox also known as containers in an operating system.

For my previous projects, i have been using VMs to deploy web solution. For efficiency purpose, i will be using docker to deploy my application.Unlike a VM, Docker allocated not the whole guest OS for your application, but only isolated minimal part of it - this isolated container has all that your application needs and at the same time is lighter, faster, and can be shipped as a Docker image to multiple physical or virtual environments, as long as this environment can run Docker engine. This approach also solves the environment incompatibility issue. It is a well-known problem when a developer sends his application to you, you try to deploy it, deployment fails, and the developer replies, "- It works on my machine!". With Docker - if the application is shipped as a container, it has its own environment isolated from the rest of the world, and it will always work the same way on any server that has Docker engine.

 ## Installing docker engine
For the purpose of this project, i installed docker desktop that is conpartible with my local host.

<img width="546" alt="Screenshot 2024-01-18 at 21 18 16" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/6fbe288d-d6dc-4efa-af59-05f586f17c5a">

## Deploying mySQL into a container in docker engine.

`docker run --name <container_name> -e MYSQL_ROOT_PASSWORD=<my-secret-pw> -d mysql/mysql-server:latest`

I aaded the needed values into the command and the got the container up and running.

<img width="1121" alt="Screenshot 2024-01-18 at 21 47 29" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/aacc9a33-a1f0-45f2-92bb-c877436afd15">

## Connecting to the MySQL Docker Container

I connected directly to the mySQL server as to creating another container to serve as mySQL client

`docker exec -it mubarokah mysql -uroot -p`

<img width="691" alt="Screenshot 2024-01-20 at 18 09 57" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/78b00cd2-3a73-4996-97c4-85b014f29b04">


## Preparing database schema

- Cloning the following repository (git clone https://github.com/darey-devops/tooling.git)

- Exporting the location of the SQL file that contains data for setting up the MySQL database: `export tooling_db_schema=~/tooling_db_schema.sql`

- Using the SQL script to create the database and prepare the schema:  `docker exec -i mysql-server mysql -uroot -p$MYSQL_PW < $tooling_db_schema`

  <img width="675" alt="Screenshot 2024-01-20 at 22 23 34" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/c9c2628a-96f9-4fbf-b8fc-2d1f0eca3fa1">

- I updated the db_conn.php with the connection details to the database.

    $servername = "mysqlserverhost";
    $username = "mubarokah";
    $password = "*****";
    $dbname = "toolingdb";


## Runing the Tooling Application

Containerizing the Tooling Appliaction

- I ran the following command in the directory that has dockerfile

  'docker build -t tooling:0.0.1'

  <img width="1059" alt="Screenshot 2024-01-21 at 17 37 57" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/57d368cc-2549-43c9-a499-f9c9f5022e01">

  - Running the container
 
   'docker run --network tooling_app_network -p 8085:80 -it tooling:0.0.1'

  <img width="1390" alt="Screenshot 2024-01-21 at 18 03 17" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/394ee02a-b2fc-4629-b650-e0481a7d3d15">

<img width="776" alt="Screenshot 2024-01-25 at 12 09 09" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/ae9b7842-79e0-41a3-baad-b1d9641361a6">


## Migarating the php-Todo app into a containerized application


- Cloning this repsository 'https://github.com/Mubarokahh/php-todo.git'
- I created mysql container for the php-todo
  
  <img width="1244" alt="Screenshot 2024-01-29 at 12 11 20" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/7eb5666d-85b9-43f0-9b7c-651a03f1a843">
- The dockerfile

  <img width="793" alt="Screenshot 2024-01-29 at 13 15 02" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/6b27ad3e-628e-4b2d-b59a-a33c25e6204f">

- Creating a docker image with the build command




















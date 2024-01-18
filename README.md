# MIGRATING TO THE CLOUD WITH CONTAINERIZATION
In this project,when i talk about containers, I imply docker. Although there are other containerization technology,docker is the standard tool for deploying application its dependencies and configuration in a sandbox also known as containers in an operating system.

For my previous projects, i have been using VMs to deploy web solution. For efficiency purpose, i will be using docker to deploy my application.Unlike a VM, Docker allocated not the whole guest OS for your application, but only isolated minimal part of it - this isolated container has all that your application needs and at the same time is lighter, faster, and can be shipped as a Docker image to multiple physical or virtual environments, as long as this environment can run Docker engine. This approach also solves the environment incompatibility issue. It is a well-known problem when a developer sends his application to you, you try to deploy it, deployment fails, and the developer replies, "- It works on my machine!". With Docker - if the application is shipped as a container, it has its own environment isolated from the rest of the world, and it will always work the same way on any server that has Docker engine.

 ## Installing docker engine
For the purpose of this project, i installed docker desktop that is conpartible with my local host.

<img width="546" alt="Screenshot 2024-01-18 at 21 18 16" src="https://github.com/Mubarokahh/Migration-to-the-Cloud-with-Containerization/assets/135038657/6fbe288d-d6dc-4efa-af59-05f586f17c5a">


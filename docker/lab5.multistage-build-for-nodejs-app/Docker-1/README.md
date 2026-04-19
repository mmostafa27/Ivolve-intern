# Lab5: multistage build for nodejs app
 This lab demonstrates how to build and run a Spring-Boot Application using a multi-stage Dockerfile to produce a lightweight and efficient production image.

 **step1** clone the repository 
 ```
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1

 ```
 **step2** write the Dockerfile
 ![alt text](<Screenshot from 2026-04-18 20-24-28.png>)

Stage 1: builds the JAR file using Maven.
Stage 2: copies the JAR into a clean Alpine image for runtime.

**step3** build the docker image and run the container 
```
docker build -t multistage-lab .

```
![alt text](<Screenshot from 2026-04-18 20-28-52.png>)

```
docker run -d --name multistage-app -p 75:8080 multistage-lab 
```
![alt text](<Screenshot from 2026-04-18 20-31-35.png>)

## comparison with the single stage Dockerfile images
![alt text](<Screenshot from 2026-04-18 20-34-36.png>)

**Note** : The image size is almost the same as running the application before building the image,  that makes sense.


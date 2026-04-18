# Lab 4: Run Java Spring Boot App in a Docker Container

## Lab instrument Summary 

**Step1** clone the repository 
```
git clone https://github.com/Ibrahim-Adel15/Docker-1.git
cd Docker-1
```
**Step2** create Dockerfile (build inside Container version)
*Dockerfile*(docker-1.1)
![alt text](<Screenshot from 2026-04-18 16-31-08.png>)
 
**step3** build the image and run the container
```
docker build -t lab1.1 . 
```
![alt text](<Screenshot from 2026-04-18 16-28-55.png>)

```
docker run -d --name app1.1 -p 77:8080 lab1.1 
curl localhost:77
```
![alt text](<Screenshot from 2026-04-18 16-35-32.png>)

### Second Attempt (Build App Locally First)

**step4** copy the files and run the application locally 
```
cp -r Docker-1.1 Docker-1.2
cd Docker-1.2
mvn package
```
![alt text](<Screenshot from 2026-04-18 16-39-42.png>)

**step5** write the Dockerfile
![alt text](<Screenshot from 2026-04-18 16-43-48.png>)

**step6** build the image and run the container 
```
docker build -t lab1.2 . 
```
![alt text](<Screenshot from 2026-04-18 16-45-59.png>)

```
docker run -d --name app1.2 -p 78:8080 lab1.2 
```
![alt text](<Screenshot from 2026-04-18 16-47-11.png>)

-----------------------------------------------------------------------------------------------------------------------
## Comparison Between Both Images
| Image |	Built Inside Container | Base Image                               |Size     |
|-------| -----------------------| -----------------------------------------|---------|
| lab1.1|	Yes	                   |maven:4.0.0-rc-5-eclipse-temurin-17-alpine|	 720MB  |
| lab1.2|	No (JAR prebuilt)      |maven:4.0.0-rc-5-eclipse-temurin-17-alpine|  593MB  |

**Note**: if we used a lighter base image in the Dockerfile the built image might be lighter as well
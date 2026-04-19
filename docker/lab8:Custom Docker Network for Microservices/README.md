# Lab8: custom docker network for microservices

This lab demonstrates how to build a basic microservices architecture using Docker and a custom network. It includes two simple Flask applications: a backend service and a frontend that communicates with it.

**Step1** clone the repository 
```
git clone https://github.com/Ibrahim-Adel15/Docker5.git
cd Docker5
```
**Step2**
write Docker files for both frontend and backend

**First** frontend Dockerfile
```
FROM python:3.15.0a8-alpine
WORKDIR /app
RUN pip install flask 
RUN pip install requests 
COPY . . 
CMD ["python","app.py"]
EXPOSE 5000
```
**Second** backend Dockerfile
```
FROM python:3.15.0a8-alpine
WORKDIR /app 
RUN pip install flask 
COPY . . 
CMD ["python","app.py"]
EXPOSE 5000
```
 **Step3** create a custom docker network 
```
docker network create ivolve-network
```
![alt text](<Screenshot from 2026-04-18 22-34-37.png>)
 
**Step4** build the images 
**frontend**
```
cd frontend 
docker build -t frontend-img . 
```
**backend**
```
cd backend
docker build -t backend-img . 
```
**Step5** run containers in the custom network 
docker run -d --name backend --network ivolve-network backend-img
docker run -d --name frontend1 --network ivolve-network frontend-img
docker run -d --name frontend2  frontend-img


 **step5** test the containers connection 
From frontend1 (same network):

```
docker exec -it frontend1 sh
curl backend:5000
```
![alt text](<Screenshot from 2026-04-18 22-30-50.png>)


From frontend2(different network) : 
```
docker exec -it frontend2 sh 
curl backend:5000
```
![alt text](<Screenshot from 2026-04-18 22-33-56.png>)


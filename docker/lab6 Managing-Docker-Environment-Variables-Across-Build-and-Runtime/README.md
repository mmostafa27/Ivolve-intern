# Lab6 managing docker environment variables acroos build and runtime 

This lab demonstr ates how to work with Docker Environment Variables using a simple Flask app.  -

- Setting environment variables using :
    - d-ocker run -e
    - --env-file- 
    - ENV in Doc- kerfile
- Running multiple containers with different configurations
- Verifyi- ng environment behavior via cur- l

**Step1** clone the repository 
```
git clone https://github.com/Ibrahim-Adel15/Docker-3.git
cd Docker-3

```
**Step2** write Docker files
- Dockerfile for runtime env variables 
```
FROM python:3.15-rc-trixie
WORKDIR /app
RUN pip install flask
COPY . .
CMD ["python","app.py"]
EXPOSE 8080

```
- Dockerfile-env for embeded env variables
```
FROM python:3.15-rc-trixie
WORKDIR /app
RUN pip install flask
COPY . .
CMD ["python","app.py"]
ENV APP_MODE=production
ENV APP_REGION=canada-west
EXPOSE 8080

```
**Step3** build the images
```
docker build -t lab6-img .
```
![alt text](<Screenshot from 2026-04-18 21-11-55.png>)

```
docker build -f Dockerfile-env -t lab6-img:v2 .
```
![alt text](<Screenshot from 2026-04-18 21-12-37.png>)


**Step4** build the envfile 
```
vim envfile 
```
![alt text](<Screenshot from 2026-04-18 21-22-49.png>)

**Step5** run the three container 
```
docker run -d -p 76:8080 --name container1 -e APP_MODE=development \
  -e APP_REGION=us-east \
  lab6-img
```
![alt text](<Screenshot from 2026-04-18 21-24-32.png>)

 ```
docker run -d -p 75:8080 --env-file envfile --name container2 lab6-img 
 ```
 ![alt text](<Screenshot from 2026-04-18 21-25-34.png>)

 ```
docker run -d -p 74:8080 --name container3 lab6-img:v2
 ```
 ![alt text](<Screenshot from 2026-04-18 21-26-12.png>)

 
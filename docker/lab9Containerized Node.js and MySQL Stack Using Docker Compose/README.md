# Lab9 containerized Nodr js and mysql using docker compose

This project demonstrates how to use Docker Compose to set up a Node.js application with a PostgreSQL database as services.

**Step1** clone the repository 
```
git clone https://github.com/Ibrahim-Adel15/kubernets-app.git
cd kubernetes-app

```

**Step2** create docker-compose YAML file
```
services:
   app: 
      build: . 
      container_name: App-service 
      ports: 
        - "3000:3000"
      environment: 
        - DB_HOST=db_service
        - DB_USER=appuser
        - DB_PASSWORD=pass123
      depends_on:
        - db 

   db:
     image: mysql:8
     container_name: db-service
     environment: 
       - MYSQL_ROOT_PASSWORD=pass123
       - MYSQL_DATABASE=ivolve
       - MYSQL_USER=appuser
       - MYSQL_PASSWORD=pass123
     volumes: 
        - db_data:/var/lib/mysql

volumes: 
    db_data: 
```


**Step3** build and run the docker compose file 
```
docker-compose up --build 
```

**Step3** performing it is working 
```
docker-compose ps

```

![alt text](<Screenshot from 2026-04-19 14-36-14.png>)

```
docker volume ls 
```
![alt text](<Screenshot from 2026-04-19 14-42-41.png>)


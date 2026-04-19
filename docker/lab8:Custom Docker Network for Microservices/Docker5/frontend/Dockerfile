FROM python:3.15.0a8-alpine
WORKDIR /app
RUN pip install flask 
RUN pip install requests 
COPY . . 
CMD ["python","app.py"]
EXPOSE 5000

FROM python:3.15-rc-trixie
WORKDIR /app 
RUN pip install flask 
COPY . .
CMD ["python","app.py"]
ENV APP_MODE=production
ENV APP_REGION=canada-west
EXPOSE 8080 

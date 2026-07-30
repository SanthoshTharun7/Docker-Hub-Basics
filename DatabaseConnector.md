Docker Database Connector Assignment

Objective

Build a Docker image for a Python Flask application that connects to aMySQL database running on XAMPP.

Project Structure

DatabaseConnector/
├── Dockerfile
├── app.py
└── requirements.txt

requirements.txt

Flask
mysql-connector-python

Dockerfile

FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

ENV DB_HOST=host.docker.internal
ENV DB_PORT=3306
ENV DB_USER=dockeruser
ENV DB_PASSWORD=password123
ENV DB_NAME=company

EXPOSE 8080

CMD ["python","app.py"]

Create MySQL User

In phpMyAdmin:

CREATE USER 'dockeruser'@'localhost' IDENTIFIED BY 'password123';

GRANT ALL PRIVILEGES ON company.* TO 'dockeruser'@'localhost';

FLUSH PRIVILEGES;

Create Database and Table

USE company;

CREATE TABLE employeese(
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
);

INSERT INTO employeese(name, department)
VALUES
('Alice','HR'),
('Bob','IT'),
('Charlie','Finance');

Build Docker Image

docker build -t dbconnector .

Run Container

docker run --add-host=host.docker.internal:host-gateway -p 8080:8080 dbconnector

Explanation

docker run starts a container.

--add-host=host.docker.internal:host-gateway creates the hostnamehost.docker.internal inside the container so it can reach the hostmachine (where XAMPP MySQL is running).

-p 8080:8080 maps host port 8080 to container port 8080.

dbconnector is the Docker image name.

Push to Docker Hub

docker login

docker tag dbconnector santhoshtharun7/db-conn-dockerimage:latest

docker push santhoshtharun7/db-conn-dockerimage:latest

Result

Open:

http://localhost:8080

Expected output:

Database Connected Successfully

Employee Details

Alice - HR

Bob - IT

Charlie - Finance

Troubleshooting

Port already allocated

docker ps
docker stop <container_id>
docker rm <container_id>

Or run on another port:

docker run -p 8081:8080 dbconnector

Access denied

Verify MySQL username and password.

Grant privileges to the MySQL user.

Ensure DB_HOST points to host.docker.internal.

Rebuild the image after Dockerfile changes.

Commands Summary

docker build -t dbconnector .

docker run --add-host=host.docker.internal:host-gateway -p 8080:8080 dbconnector

docker ps

docker logs <container_id>

docker stop <container_id>

docker rm <container_id>

docker login

docker tag dbconnector santhoshtharun7/db-conn-dockerimage:latest

docker push santhoshtharun7/db-conn-dockerimage:latest

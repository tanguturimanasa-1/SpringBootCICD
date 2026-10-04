# SpringBootCICD

Simple Java Spring Boot web application with an automated Jenkins CI/CD pipeline.

## Application

Open:

http://localhost:8085/

Expected:

Welcome to Automated Spring Boot CI/CD!

Health check:

http://localhost:8085/health

Expected:

Application is running successfully!

## Local Build

```cmd
mvn clean test
mvn clean package

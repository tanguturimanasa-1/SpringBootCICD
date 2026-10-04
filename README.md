# SpringBootCICD

Simple Java Spring Boot web application with an automated Jenkins CI/CD pipeline.

## Application

Open:
http://localhost:8080/

Expected:
Welcome to Automated Spring Boot CI/CD!

Health check:
http://localhost:8080/health

## Local build

mvn clean test
mvn clean package

Run:
java -jar target/SpringBootCICD-1.0.jar

## Docker

Build:
docker build -t springboot-cicd:latest .

Run:
docker run -d -p 8080:8080 --name springboot-cicd-container springboot-cicd:latest

## Git

git init
git add .
git commit -m "Initial Spring Boot CI/CD application"
git branch -M main
git remote add origin YOUR_GITHUB_REPOSITORY_URL
git push -u origin main

## Jenkins

Create a Pipeline job.

Pipeline Definition:
Pipeline script from SCM

SCM:
Git

Branch:
*/main

Script Path:
Jenkinsfile

Enable GitHub webhook triggering. The Jenkins server must be reachable by GitHub for a webhook to work.

Pipeline stages:
1. Checkout
2. Build
3. Test
4. Docker Build
5. Docker Run

## Required on Jenkins machine

- Java
- Maven
- Git
- Docker Desktop / Docker Engine
- Jenkins GitHub integration

For Windows Jenkins service, verify these commands are available to Jenkins:
java -version
mvn --version
git --version
docker --version

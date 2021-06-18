# apache2-php7-java11
Based on Alpine 3.11 Contains a basic apache2 configured, php7 and java11 and ready to run

## How to Run?
You can download and install Docker [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
Docker runs processes in isolated containers. A container is a process which runs on a host. The host may be local or remote.

**Docker Pull Command**

```
docker pull sidpro/apache2-php7-java11
```
**Start a apache server instance**

```
docker run -p 8080:80 --name compiler -d sidpro/apache2-php7-java11
```
Now you can check http://localhost:8080/ in your browser.


**Stop instance**
```
docker stop compiler
```
**Remove container**
```
docker rm compiler
```
**Remove Docker image**
```
docker rmi sidpro/apache2-php7-java11
```

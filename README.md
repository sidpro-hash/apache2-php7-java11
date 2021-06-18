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

## How to Deploye on Heroku?

To Deploye on Heroku needs [Heroku account](https://signup.heroku.com/login), [Heroku cli](https://devcenter.heroku.com/articles/heroku-cli#download-and-install), [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

**Replace CMD command in Docker file**
```
CMD ["run-apache2.sh"] 
# needs to run on local
#CMD ["/usr/sbin/httpd","-D","FOREGROUND"] 
```
**Give permission to Docker**

Replce sidpro with your username

```
sudo chown sidpro:docker ~/.docker
sudo chown sidpro:docker ~/.docker/config.json
sudo chmod g+rw ~/.docker/config.json
sudo chmod 777 /var/run/docker.sock
```
**Login to Heroku & Heroku container**
```
heroku login
# or use this $ heroku login -i
heroku container:login
```
**Initialize Git**
```
git init
git add .
git commit -m "initial commit"
```
**Create App and Push**
```
heroku create "lowercaseappname"
heroku labs:enable --app=lowercaseappname runtime-new-layer-extract
heroku container:push web
heroku container:release web
```
**Open APP**
```
heroku open
heroku logs --tail
```

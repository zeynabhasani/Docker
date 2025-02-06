# Simple Website Deployment with Nginx and Docker
This project is assigned as a task to assess the relevant skills for entering the DevOps department at Mohaymen Company.

## Getting Started
This project demonstrates how to deploy a simple website using Nginx within a Docker container.


### Prerequisities

In order to run this container you'll need docker installed.

* [Windows](https://docs.docker.com/windows/started)
* [OS X](https://docs.docker.com/mac/started/)
* [Linux](https://docs.docker.com/linux/started/)

During the Docker installation process, you may encounter filtering issues. In this case, use the "Shecan" website to change your DNS setting configuration.
* [Shecan](https://shecan.ir/)

If you are using the terminal environment, set proxy for terminal using the following commands:
* `export http_proxy='http://proxyServerSddress:proxyPort'`    
* `export https_proxy='http://proxyServerSddress:proxyPort'`

## Usage


Before you can run the application, you need to get the application source code onto your machine.

1. Clone the repository using the following command: 
```shell
git clone https://github.com/zeynabhasani/Docker.git
```
2. View the contents of the cloned repository. You should see the following files and sub-directories:
    * default.conf
    * Dockerfile
    * README.md
    * index.html

  
### Handling restricted IP access

In the task's To-Do-list, we wanted to allow access only to certain ip addresses.
In `default.conf` file, line (6,7,8), required configuration has been done:

```shell
    #allow access to certain IP address
    allow 172.17.0.1;   //*You should replace your own IP address in here if you want to have access*//
    deny all;
```

 
 In the Dockerfile,line 2, we copy this confuguration to nginx container configurations loaded in first line using `FROM nginx`.

```shell
COPY ./default.conf /etc/nginx/conf.d/default.conf
```


### Build the container's image
 
In the terminal, make sure you're in the directory where cloned repository is located.
Build the image using the following commands:

```shell
$ docker build -t  nginx/MOHAYMEN-website .
```
**NOTE:** You can use your desired repository name for this image instead of `-t nginx/MOHAYMEN-website`.


### Runnig the container's image
Now you can run the image in a container using command below:

```shell
$ docker run -it --rm -d -p 8080:80 --name web nginx/MOHAYMEN-websit
```

**NOTE** 
We can use `Docker exec -it web /bash/sh` to interactively run commands in terminal within container environment.This is usefull to access nginx configuration files.


## Authors

* **Zeynab Hasani** - *MOHAYMEN's Entry Task* - [zeynabhasani](https://github.com/zeynabhasani)

## Acknowledgments
### Resource & References
* [https://www.docker.com](https://www.docker.com/blog/how-to-use-the-official-nginx-docker-image/)
* [http://nginx.org](http://nginx.org/en/docs/http/ngx_http_geo_module.html)
* [Very Academy](https://www.youtube.com/watch?v=9bIsFxJoFWY)
* [https://docs.docker.com](https://docs.docker.com/reference/cli/docker/image/)
* [https://hub.docker.com/](https://hub.docker.com/_/nginx)

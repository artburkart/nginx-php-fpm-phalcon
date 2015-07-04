## Introduction
This is a Dockerfile to build a container image for nginx, php-fpm, and phalcon. This Dockerfile uses the work of Richard Harvey in [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm)

## Nginx Version
- Mainline Version (see [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm))

## Phalcon Version
- **1.3.5**
- **latest**

## PHP Version
- **5.5.x**

### Git repository
The source files for this project can be found here: [https://github.com/artburkart/nginx-php-fpm-phalcon](https://github.com/artburkart/nginx-php-fpm-phalcon)

If you have any improvements please submit a pull request.

### Docker hub repository
The Docker hub build can be found here: [https://registry.hub.docker.com/u/artburkart/nginx-php-fpm-phalcon/](https://registry.hub.docker.com/u/artburkart/nginx-php-fpm-phalcon/)

## Installation
Pull the image from the docker index rather than downloading the git repo. This prevents you having to build the image on every docker host.

```
docker pull artburkart/nginx-php-fpm-phalcon:1.3.5
```

## Running
To run the container:

```
docker run --name phalcon -p 8080:80 -d artburkart/nginx-php-fpm-phalcon
```
You can then browse to http://\<docker_host\>:8080 to view the default install files.
### Volumes
If you want to link to your web site directory on the docker host to the container run:

```
sudo docker run --name nginx -p 8080:80 -v /your_code_directory:/usr/share/nginx/html -d artburkart/nginx-php-fpm-phalcon
```

## There are lots of other nice features,
but I didn't do any of them. Check out [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm) to find out what they are!
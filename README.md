rpi-bWAPP
=================

# bWAPP

This is just an instance of the OWASP [bWAPP project](http://www.itsecgames.com/) as a docker container for raspberry pi.

The container is based on resin/rpi-raspbian with reference taken from [tutum/lamp](https://hub.docker.com/r/tutum/lamp/)

To run the container 

```
docker run -d -p 80:80 sumitraina/pi0-bwapp
```

and you should be able to go to <ip>/install.php to set up your instance.

# docker compose file

Create a file named **docker-compose.yml** and add the below text. Then run **docker-compose up --detach** command to start the container. This will add a volume to container and save your progress. 

```
version: "3"

#Run command docker-compose up --detach 
services:
  pibwapp:
    container_name: pi0-bwapp
    image: sumitraina/pi0-bwapp:latest
    ports:
      - "80:80"
      - "3306:3306"
    # Volumes to store your data
    volumes:
      - './etc/mysql:/etc/mysql'
      - './var/lib/mysql:/var/lib/mysql'

```


Usage
-----

To create your own image `rpi/bwapp`, execute the following command on the current folder:

	docker build -t rpi/bwapp .

Running your bWAPP docker image
--------------------------------

Start your image binding the external ports 80 and 3306 in all interfaces to your container:

	docker run -d -p 80:80 -p 3306:3306 rpi/bwapp

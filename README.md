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


Usage
-----

To create your own image `rpi/bwapp`, execute the following command on the current folder:

	docker build -t rpi/bwapp .

Running your bWAPP docker image
--------------------------------

Start your image binding the external ports 80 and 3306 in all interfaces to your container:

	docker run -d -p 80:80 -p 3306:3306 rpi/bwapp
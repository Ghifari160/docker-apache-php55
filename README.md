# A Better PHP Image for Docker #
This image is not just another PHP5.5 image for Docker.

## Why use this image ##
This image is based on [ghifari160/apache], which forces Apache to run in the
foreground and output its log into the container's stdio.

__Note:__ PHP5.5 has reached its End of Life, it should not be used on a
production environment. This image utilizes PHP5.5.38. The use of this image
on a production server is ill advised. __*Use at your own risk.*__

## Installation ##
By default this image should be run as a daemon.
```
docker run -d -p 8080:80 ghifari160/apache-php55
```
However, this image may be run in the foreground for debugging purposes.
```
docker run -it -p 8080:80 ghifari160/apache-php55
```

### Further configurations ###
#### Name your container ####
Use the parameter `--name=<name>` to name the container. Example:
```
docker run --name=apache-php55 -d ghifari160/apache-php55
```

#### Run your code from a folder on the host computer ####
Use the parameter `-v /path/on/the/host/computer:/var/www/html` to run codes
from the host computer. Example:
```
docker run -d -v /d/workspace/project:/var/www/html ghifari160/apache-php55
```

#### Change the port on the container ####
Use the parameter `-p <port on the host>:80` to map the container's port to
another port on the host computer. Example:
```
docker run -d -p 8080:80 ghifari160/apache-php55
```

## Tags ##
| Tags                      | Ubuntu Version | Size  |
|---------------------------|----------------|-------|
| `latest` `16.04` `xenial` | 16.04          | _TBA_ |
| `17.10` `artful`          | 17.10          | _TBA_ |

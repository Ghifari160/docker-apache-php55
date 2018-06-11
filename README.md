# A Better PHP Image for Docker #
[![Docker Hub: ghifari160/apache-php55](https://img.shields.io/badge/docker%20hub-ghifari160%2Fapache--php55-ABD8EB.svg)](https://hub.docker.com/r/ghifari160/apache-php55/)
[![](https://images.microbadger.com/badges/image/ghifari160/apache-php55.svg)](https://microbadger.com/images/ghifari160/apache-php55 "Get your own image badge on microbadger.com")

This image is not just another PHP5.5 image for Docker.

Looking for a PHP5.6 image for Docker? Checkout [ghifari160/apache-php56]!

## Why use this image ##
This image is based on [ghifari160/apache], which forces Apache to run in the
foreground and output its log into the container's stdio.

### Warnings ###
- PHP5.5 has reached its End of Life, it should not be used on a
  production environment. This image utilizes PHP5.5.38. The use of this image
  on a production server is ill advised. __*Use at your own risk.*__
- Reliable PHP5.5 binaries are no longer available on any package manager. This
  image builds PHP5.5 binaries during the build process. Build tools and their
  dependencies are installed purely to build the binaries. They are removed
  after the binaries are built, installed, and configured.

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

#### macOS permission fixes
On macOS, shared volumes remains owned by the host user and group. Permissions
on these shared volumes are also determined by the host, unchangeable from
guest. On the home directory, the default owner and permission are
`<user>:staff` and `755`. Apache needs write access to its files and
directories. A workaround is to set the `www-data` UID and GID to `1000` and
`50`. The init script will do this if the value of `G16_MACOS` is `yes`. Use
the parameter `-e G16_MACOS=yes` to enable this workaround. Example:
```
docker run -d -e G16_MACOS=yes ghifari160/apache-php55
```

## Tags ##
| Tags                      | Ubuntu Version | Size  |
|---------------------------|----------------|:-----:|
| `16.04` `xenial`          | 16.04          | [![](https://images.microbadger.com/badges/image/ghifari160/apache-php55:16.04.svg)](https://microbadger.com/images/ghifari160/apache-php55:16.04 "Get your own image badge on microbadger.com")|
| `17.10` `artful`          | 17.10          | [![](https://images.microbadger.com/badges/image/ghifari160/apache-php55:17.10.svg)](https://microbadger.com/images/ghifari160/apache-php55:17.10 "Get your own image badge on microbadger.com")|
| `latest` `18.04` `bionic` | 18.04          |[![](https://images.microbadger.com/badges/image/ghifari160/apache-php55.svg)](https://microbadger.com/images/ghifari160/apache-php55 "Get your own image badge on microbadger.com")|

[ghifari160/apache]: https://github.com/ghifari160/docker-apache
[ghifari160/apache-php56]: https://github.com/ghifari160/docker-apache-php56

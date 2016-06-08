# docker-tutorial

The following tutorial explains how to start using Docker. The instructions were tested on MacOS X.

# What is Docker and why should I care?


# Initial Setup

* Install `docker-machine` from https://docs.docker.com/machine/
* Run `docker-machine --help` in your terminal
* Check the status of the Docker VM and start it if necessary
```$ docker-machine status
$ docker-machine start
```
* Once the Docker VM is running, run the following command in order to be able to run containers: `eval $(docker-machine env)`. Note that you will have to run the `eval` command on each new session you start. Consider moving this into your `~/.bash_profile` to execute it every time you start a new shell.
* Confirm you are able to run the Docker command in your current terminal session:

```
$ docker version
Client:
 Version:      1.10.3
 API version:  1.22
 Go version:   go1.5.3
 Git commit:   20f81dd
 Built:        Thu Mar 10 21:49:11 2016
 OS/Arch:      darwin/amd64

Server:
 Version:      1.10.3
 API version:  1.22
 Go version:   go1.5.3
 Git commit:   20f81dd
 Built:        Thu Mar 10 21:49:11 2016
 OS/Arch:      linux/amd64
```

# Example: Running MongoDB in a container

For more information see https://docs.docker.com/engine/examples/mongodb/.

* Download a MongoDB docker container, run it locally, and connect to it.

```
$ docker pull mongo                  # Downloads the mongo container
[...]
$ docker run -d -p 27017:27017 mongo # runs container in the background
$ docker ps                          # lists the running containers
$ telnet 192.168.99.100 27017        # Tries to connect to mongo running inside the container
```

* If all of those steps worked successfully, you can connect your application to the MongoDB instance running on `192.168.99.100:27017`.

# Example: Running Ubuntu Linux in a container

```
$ docker pull ubuntu
$ docker run -it ubuntu /bin/bash # runs bash inside the container
```

In another terminal session, list the running containers by running `docker ps`.

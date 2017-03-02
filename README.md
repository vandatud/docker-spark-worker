# VANDA - Spark Worker Container

_This image is only intended for being part of the VANDA Deap Learning Stack!_ 
Runs [Spark 2.1.0](http://spark.apache.org/docs/2.1.0/) on top of the [phusion/baseimage](https://hub.docker.com/r/phusion/baseimage/) with Ubuntu 16.04 as base system.

## Dockerfile

[`vandatud/spark-worker` Dockerfile](https://github.com/vandatud/docker-spark-worker/blob/master/Dockerfile)

## How to rebuild an extended image

After pulling this repository and changing the Dockerfile first build the new image locally to test it.
Optionally specify the repository and tag at which to save the new image if the build succeeds.
```
$ cd /path/to/Dockerfile
$ docker build -t vandatud/spark-worker:0.0.1 -t vandatud/spark-worker:latest
```

If this Git repository is pushing back to the server, DockerHub will automatically build this image.
For manually push the locally build to the DockerHub use the docker cli.

```
$ docker login
```

```
$ docker push vandatud/spark-worker:0.0.1
```

## How to use this image

Run a new container instance without

```
$ docker run -d -t -p 8081 --name vanda-spark-worker_inst vandatud/spark-worker:latest
```

or with an interactive bash session for inspecting the image.

```
$ docker run --rm -t -i -p 8081 --name vanda-spark-worker_inst vandatud/spark-worker:latest /sbin/my_init -- bash -l
```

```
$ docker ps
CONTAINER ID        IMAGE                   COMMAND             CREATED             STATUS              PORTS                     NAMES
105287df93ce        vandatud/spark-worker   "/sbin/my_init"     About an hour ago   Up About an hour    0.0.0.0:32772->8081/tcp   vanda-spark-worker_inst1
```

Once the container is running you can open the web interface under the attached host port (i.e. [localhost:32772](http://localhost:32772))
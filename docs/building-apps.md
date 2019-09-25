# Building your app with Docker
## Overview
So we have containers, we know what images are, and we can pull images from Docker Hub. Next up is building and sharing our apps, but that requires some stuff.

## Binding containers and building images
See [Docker docs](https://docs.docker.com/storage/bind-mounts/) for more.

Bind mounting is when a file or directory from the *host machine* is mounted onto the container. When you bind mount the file or directory, that file is accessed directly from the relative or full path.

To bind mount a particular directory, we can run the below:
```
  docker container run -d -p 8080:80 -v $(pwd):/usr/share/nginx/html --name nginx-website nginx
```

Where the `-v` flag is the flag for bind mounting a directory and the input argument is in the format:
```
  <host-directory>:<container-directory>
```

We can then make a Dockerfile in order to build an image from it, and it looks like the below:
```Dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

# COPY . . is COPY <ALL> TO <ALL>
COPY . .
```

And then build it and push it to Docker Hub like so:
```
  docker image build -t wilsonj806/nginx-website .
```

So this has a couple of things going on. First we're building an image duh, but we're also defining a name for this image, and pushing it to our Docker Hub account.

Also note that we don't need to run a whole new container in order to build our image, you can just run `docker container create` instead of `docker container run`

We can then run as many containers as we want with:
```
  docker container run [OPTIONS] -p 8082:80 --name mylocalnginx wilsonj806/nginx-website
```

Where `wilsonj806/nginx-webiste` is the image name.
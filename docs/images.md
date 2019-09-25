# Docker Images
## What's a Docker Image
In short a Docker Image is basically a series of layers which can be built into a container. As someone on [StackOverflow](https://stackoverflow.com/questions/23735149/what-is-the-difference-between-a-docker-image-and-a-container) said, an image is basically a recipe, and a container is your cake.

You can have multiple containers based on an image, but not the other way around. In addition, once an image is built, you cannot modify it and if you want to upgrade the image, another newer image is built. Another way to describe it is that images are basically are like `.exe` files for installing and running dependencies.

## Listing available images
To get a list of available images run:
```
  docker images
```

## Removing images
To remove an image, run the below:
```
  docker images rm <first three characters from the Image ID>
```

## Pulling Images
To pull an image, run the below:
```
  docker pull <image-name>
```

The full version of the command is actually the below and lets you do more:
```
  docker pull [OPTIONS] <IMAGE-NAME>[:TAG | @DIGEST]
```

So for the latest stable build of Nginx we'd run:
```
  docker pull nginx:stable

  OR

  docker pull nginx:1.16
```
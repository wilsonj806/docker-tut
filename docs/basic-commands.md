# Basic Docker Commands
Basic Docker commands will be listed here with a brief explanation of them.

See the [Traversy Media gist](https://gist.github.com/bradtraversy/89fad226dc058a41b596d586022a9bd3) on it as well

## Docker Version
```
  docker version
```

Lists the version of Docker running for the client and server. The server version is the one that runs in the background and handles containers, while the client version handles communicating with the server.

## Docker Info
```
  docker info
```

Lists information about Docker and what's currently running(containers, images, etc)


## Docker Images
```
  docker images
```

Lists images

## Interpolating a command
Interpolation a command can be done with the below syntax:
```
  $(your stuff here)
```

This lets you do some fast stuff such as deleting all of your containers with the below:
```
  docker containers rm $(docker ps -aq)
```

Where the above is removing all of the listed containers, and is doing it quietly.
# Docker Containers
## What's a container
A Docker container is where you app lives pretty much. It's isolated, and only includes what you want the container to include. At least to start, we'll be spinning up an Nginx container for use.

## Running our first container
To run a new container in interactive mode/ run it in the foreground and to publish it onto a port on localhost, run the below:
```
  docker container run -it -p 80:80 nginx
```

The arg after the `-p` or `--publish` flag is the port we want to expose on the client end to access if via localhost, and then the port that the container exposes. So here we access Nginx via `localhost:80` and our container exposes port 80 as well.
- as a side note, PORT 80 is the default port for Nginx


If we wanted to connect to our container with a different port, we'd use:
```
  docker container run -it -p 50:80 nginx
```

When we first run this(with no other containers/ images loaded), note that Docker pulls the files required for Nginx if it can't find it locally. Then on subsequent runs of Nginx, it just runs it without pulling it as it's already pulled.

## Checking running containers
To check our running containers we can run the below:
```
  docker container ls
```

Alternatively we can run:
```
  docker ps
```

Note that if we terminated the Nginx process from the above container, we won't have anything listed. So we can run the below:
```
  docker container ls -a

  OR

  docker ps -a
```

## Removing containers
To remove a container, we'd need to know the container's id, which we can do with the above. Once we do that, we can run the below:
```
  docker container rm <first three characters of the container's id>

  OR

  docker container rm <container name>
```

## Running detached processes
To run a detached container of Nginx(it runs in the background and you can't just ^C out), run the below:
```
  docker container run -d -p 8080:80 --name mynginx nginx
```

Note that `-d` is the flag for detaching a process, and `--name` is the name of the container. When you run it, you still have access to your terminal, but if you run `docker ps`, you'll see that it's running.

## Configuring a container's environment
So certain applications need to be configured before we run it. Something like MySQL for instance, requires a root user and password before you run it.

To build a Docker container for MySQL, run the below:
```
  docker container run -d -p 3307:3306 --name mysql3307 --env MYSQL_ROOT_PASSWORD=1234 mysql
```

Note the `--env` flag which lets us define environment variables to run in the container.

## Bashing into your container
You can also bash into your container, similar to or exactly how Heroku lets you run terminal commands on your dynos. To do so run the below:
```
  docker container exec -it mynginx bash
```
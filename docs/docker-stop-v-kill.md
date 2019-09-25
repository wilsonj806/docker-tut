# Docker stop vs kill
## Why do we need to differentiate between the two
There's a very subtle difference between using `docker container stop` over `docker container kill`.

This [SuperUser](https://superuser.com/questions/756999/whats-the-difference-between-docker-stop-and-docker-kill) is a pretty good reference on it. But basically `docker stop` sends a SIGTERM signal first, then a SIGKILL signal while `docker kill` sends a SIGKILL signal.

Now if you check the `--help` output for both you get:

```
  $ docker container stop --help

Usage: docker container stop [OPTIONS] CONTAINER [CONTAINER...]

Stop one or more running containers

Options:

-t, --time int    Seconds to wait before killing it(default 10)

  $ docker container kill --help

Usage: docker container kill [OPTIONS] CONTAINER [CONTAINER...]

Kill one or more running containers

Options:

-s, --signal starting    Signal to send to the container(default "KILL")
```

So while both do the same thing, `docker stop` tells the container to gracefully shutdown, while `docker kill` force terminates the container. In addition, `docker stop` has a grace period, where if the container hasn't shutdown in the alowed period, a SIGKILL signal is sent.

A good analogy is pressing the shutdown button over just unplugging your computer.
# Docker 101
## Overview
This is a docker tutorial repo based on Traversy Media's Docker tutorial on Youtube. This repo, will have notes on Docker/ Docker-Compose as well.

## Notes
- [Docker Stop vs Kill](./docs/docker-stop-v-kill.md)
- [Basic Commands](./docs/basic-commands.md)
- [Building Apps](./docs/building-apps.md)
- [Containers](./docs/containers.md)
- [Images](./docs/images.md)

## What is Docker
Docker is a containerization platform that lets you package and deliver software in isolated bundles called containers. This lets you worry less about syncing versions of your dependencies to your app for deployment and more on building your app(i.e it works on my local machine, why doesn't it work on deploy). It also makes it easier to upgrade your dependencies as well since each dependent service can be run in a separate container.

This is different from a virtual machine as seen in the below diagram:
![docker vs vm](https://www.nakivo.com/blog/wp-content/uploads/2019/05/Docker-containers-are-not-lightweight-virtual-machines.png)

## Docker CLI help
As a general note, Docker's CLI gives pretty good help for any of it's CLI commands, just run
```
  docker COMMAND-HERE --help
```
for more details on the command.

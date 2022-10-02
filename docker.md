# Docker commands

## docker pull \<image name>

To pull images from the docker repository (hub.docker.com). Similar to git pull. Can use to update the existing local image.

## docker ps

To list the running containers

## docker ps -a

To show all the running and exited containers

## docker stop \<container id>

To stop a running container. Can use container id or name

## docker kill \<container id>

This command kills the container by stopping its execution immediately. The difference between ‘docker kill’ and ‘docker stop’ is that ‘docker stop’ gives the container time to shutdown gracefully, in situations when it is taking too much time for getting the container to stop, one can opt to kill it

## docker stats

To list the stats of all running containers. Note that only press Ctrl + C, not other buttons. Otherwise the terminal will get stuck.

CPU%: CPU is expressed as a percentage (%) of the overall host capacity. 




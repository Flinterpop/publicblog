

# Docker/Containers



Containers utilize operating system kernel features to provide partially virtualized environments. 

Containers are lightweight, self-sufficient, and better suited to throwaway use cases. As Docker shares the host's kernel, containers have a negligible impact on system performance. Container launch time is almost instantaneous, as you're only starting processes, not an entire operating system.



 Registries [provide centralized storage](https://www.howtogeek.com/devops/how-do-docker-container-registries-work/) so that you can share containers with others. The default registry is [Docker Hub](https://hub.docker.com/).



### Managing Containers

### Listing Containers

`docker ps` shows you all your running containers. Adding the `-a` flag will show stopped containers, too.

### Stopping and Starting Containers

To stop a container, run `docker stop my-container`. Replace `my-container` with the container's name or ID. You can get this information from the `ps` command. A stopped container is restarted with `docker start my-container`.

Containers usually run for as long as their main process stays alive. [Restart policies](https://www.howtogeek.com/devops/how-to-use-docker-restart-policies-to-keep-containers-running/) control what happens when a container stops or your host restarts.

Pass `--restart always` to `docker run` to make a container restart immediately after it stops.

### Getting a Shell

You can [run a command in](https://www.howtogeek.com/devops/the-difference-between-cmd-and-entrypoint-in-docker-images/) a container using `docker exec my-container my-command`. This is useful when you want to manually invoke an executable that's separate to the container's main process.

Add the `-it` flag if you need interactive access. This lets you drop into a shell by running `docker exec -it my-container sh`.

### Monitoring Logs

Docker automatically collects output emitted to a container's standard input and output streams. The [`docker logs my-container`](https://www.howtogeek.com/devops/how-to-monitor-docker-container-logs/) command will show a container's logs inside your terminal. The `--follow` flag sets up a continuous stream so that you can view logs in real time.

### Cleaning Up Resources

Old containers and images can quickly pile up on your system. Use `docker rm my-container` to delete a container by its ID or name.

The command for images is `docker rmi my-image:latest`. Pass the image's ID or full tag name. If you specify a tag, the image won't be deleted until it has no more tags assigned. Otherwise, the given tag will be removed but the image's other tags will remain usable.

## Persistent Data Storage

Docker containers are ephemeral by default. Changes made to a container's filesystem won't persist after the container stops. It's not safe to [run any form of file storage system](https://www.howtogeek.com/devops/should-you-run-a-database-in-docker/) in a container started with a basic `docker run` command.

There are a few different approaches to [managing persistent data](https://www.howtogeek.com/devops/how-to-deal-with-docker-container-persistence-and-storage/). The most common is to use a Docker Volume. [Volumes are storage units](https://www.howtogeek.com/devops/what-are-docker-volumes-and-how-do-you-use-them/) that are mounted into container filesystems. Any data in a volume will remain intact after its linked container stops, letting you connect another container in the future.

## Working with Multiple Containers

The `docker` command only works with one container at a time. You'll often want to use containers in aggregate. [Docker Compose](https://www.howtogeek.com/devops/what-is-docker-compose-and-how-do-you-use-it/) is a tool that lets you define your containers declaratively in a YAML file. You can start them all up with a single command.

This is helpful when your project depends on other services, such as a web backend that relies on a database server. You can define both containers in your `docker-compose.yml` and benefit from streamlined management with [automatic networking](https://docs.docker.com/compose/networking).






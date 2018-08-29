# Docker Cheat Sheet
#### Run an image
Run a Docker container in detached mode and expose port 8080.

```bash
$ docker run -d --name my_docker -p 8080:8080 image_name
```

#### Get the IP Address
`$ docker inspect -f "{{ .NetworkSettings.IPAddress }}" my_docker`

#### Attach to a container
Attach to a running Docker container by ID.

```bash
$ docker exec -it 32adfbf6eb62 /bin/bash
```

Attach to a running Docker container by name and enter a Bash shell.

```bash
$ docker exec -it my_docker /bin/bash
```

To detach use the following escape sequence: `CTRL + p CTRL + q`.

#### Mount current directory

```bash
docker run --rm -v ${PWD}:/home/jovyan/work jupyter/scipy-notebook
```

On Windows. Note the above works with PowerShell.

```bash
docker run --rm %cd%:/home/jovyan/work jupyter/scipy-notebook
```

See https://stackoverflow.com/a/41489151

#### Stop a container

`$ docker kill <container_id>`

#### Remove stopped container

`$ docker rm <container_id>`

#### Start container with remove switch

`$ docker run -d --name my_docker image_name --rm`

See [single command to stop and remove docker container](http://stackoverflow.com/a/35122815/6146580)

#### See all containers
`$ docker ps -a`

#### Clean up everything
`docker system prune`

#### Remove all exited containers
`$ docker rm $(docker ps -a -f status=exited -q)`

#### Remove all stopped containers
`$ docker rm $(docker ps -a -q)`

#### See all images
`$ docker images -a`

#### Format image list
```bash
$ docker images --format "table {{.Repository}}\\t{{.Tag}}\\t{{.ID}}"
```

Store the format in `~/.docker/config.json`. E.g.

```json
{
  "psFormat": "table {{.Names}}\\t{{.Image}}\\t{{.RunningFor}} ago\\t{{.Status}}\\t{{.Command}}",
  "imagesFormat": "table {{.Repository}}\\t{{.Tag}}\\t{{.ID}}\\t{{.Size}}"
}
```

[See Docker Quicktip #7: docker ps --format](http://container42.com/2016/03/27/docker-quicktip-7-psformat/).

#### Remove all untagged images
```bash
$ docker rmi $(docker images -q -f dangling=true)
$ docker rmi $(docker images | grep "^<none>" | awk '{print $3}')
$ docker images -q -a | xargs --no-run-if-empty docker rmi
```

#### Remove all unused volumes
```bash
$ docker volume prune -f
```

#### Rebuild when composing
```bash
$ docker-compose up -d --build
```

#### Tag image after building it
```bash
$ docker build -t dev:latest .
```

### Resources
* [Remove Untagged Images From Docker](http://jimhoskins.com/2013/07/27/remove-untagged-docker-images.html)
* [What are Docker \<none\>:\<none\> images?](http://www.projectatomic.io/blog/2015/07/what-are-docker-none-none-images/)
* [Docker – Clean Up After Yourself!](http://blog.yohanliyanage.com/2015/05/docker-clean-up-after-yourself/)
* [How to remove unused Docker containers and images](https://gist.github.com/ngpestelos/4fc2e31e19f86b9cf10b)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [How do you attach and detach from Docker's process?](https://stackoverflow.com/questions/19688314/how-do-you-attach-and-detach-from-dockers-process)
* [How to remove old and unused Docker images](http://stackoverflow.com/a/32723127/6146580)
* [How to remove \<none\> images after building](https://forums.docker.com/t/how-to-remove-none-images-after-building/7050/10)
* [How To Remove Docker Images, Containers, and Volumes](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes)

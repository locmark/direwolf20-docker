# Feed-The-Beast Presents Direwolf20 (Minecraft 1.12.2) in a Docker Container

Forked from [audiohacked/docker-direwolf20_110](https://github.com/audiohacked/docker-direwolf20_110).

A Direwolf20 1.12 server in a docker. Nothing more, nothing less.

To pull the image:
```
docker pull willwill56/direwolf20_112:stable
```

It's highly recommended to run a named data volume:
```
docker volume create minecraft_direwolf20_world
docker volume create minecraft_direwolf20_backups
```

Then, run the server container:
```
docker run --detach --interactive --tty \
    --name direwolf20 \
    --volume minecraft_direwolf20_world:/minecraft/world \
	--volume minecraft_direwolf20_backups:/minecraft/backups \
    --publish 25565:25565 \
    --env EULA=TRUE \
    willwill56/direwolf20_112:stable
```

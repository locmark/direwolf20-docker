
# Feed-The-Beast Presents Direwolf20 (Minecraft 1.12.2) in a Docker Container

Forked from [audiohacked/docker-direwolf20_110](https://github.com/audiohacked/docker-direwolf20_110).

A Direwolf20 1.12 server in a docker. Nothing more, nothing less.

## Creating the container
Pull the image first if you'd like:
```
docker pull willwill56/direwolf20_112:latest
```

It is highly recommended to bind folders on your host OS to the directories in the docker. If you'd prefer not to, at least set up some named volumes so you can find them later, e.g.:
```
docker volume create minecraft_direwolf20112_world
docker volume create minecraft_direwolf20112_backups
```

To create and run the container:
```
docker run --detach --interactive --tty \
    --name direwolf20_112 \
    --volume /path/on/host/minecraft/world:/minecraft/world \
    --volume /path/on/host/minecraft/backups:/minecraft/backups \
    --publish 25565:25565 \
    --env EULA=TRUE \
    willwill56/direwolf20_112:latest
```

or if you're using named volumes, substitute the volume lines for these:
```
    --volume minecraft_direwolf20112_world:/minecraft/world \
    --volume minecraft_direwolf20112_backups:/minecraft/backups \
```

## Using the server console
If the `--interactive` and `--tty` options are correctly set for the container, you can use the command `docker attach direwolf20_112` to access the server console and enter commands that way. Use the escape sequence `Ctrl+P, Ctrl+Q` to safely exit the server console without killing the server. Giving yourself operator status is a good idea, since it allows access to the commands in-game, which is much more convenient.

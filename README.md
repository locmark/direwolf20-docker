# Feed-The-Beast Presents Direwolf20 (Minecraft 1.10.2) in a Docker Container
To pull the image:
```
docker pull audiohacked/direwolf20_110:stable
```

It's highly recommended run a data container:
```
docker run --name direwolf20_datastore audiohacked/direwolf20_110:stable true
```

Then, run the server container:
```
docker run --detach --interactive --tty \
    --name direwolf20 \
    --volumes-from direwolf20_datastore \
    -p 25565:25565 \
    -e EULA=TRUE \
    audiohacked/direwolf20_110:stable
```

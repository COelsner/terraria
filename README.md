# Terraria related stuff
A mixture of terraria related files ...

## Vanilla Dedicated Server

[![](https://images.microbadger.com/badges/image/coelsner/terraria.svg)](coelsner/vanilla-docker)

The Dockerfile within `vanilla-docker` containerizes a vanilla dedicated terraria server. Due to the shipped mono runtime by terraria itself, it isn't necessary to install `mono-complete`.

Starting a dedicated server in interactive mode:

    docker run -it -p 7777:7777 -v $HOME/terraria/world:/world --name="terraria" coelsner/terraria:vanilla-latest

The world will be saved within the container at `/world`. With the `-v path/on/your/machine:/world` option you can specify a location on your host which will be maped to `/world`.

To start your server with a different config file just use `-e CONFIG="/path/to/config"`. The path to use here refers to the path **inside** of the container, e.g.:

    docker run -it -p 7777:7777 -v $HOME/terraria/world:/world -e CONFIG="/world/serverconfig.txt" --name="terraria" coelsner/terraria:vanilla-latest

Shoutout to [Ryan Sheehan](https://github.com/ryansheehan) for providing a dockerized server with TShock: [ryshe/terraria](https://hub.docker.com/r/ryshe/terraria/)

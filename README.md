# Minecraft tmux service

With these files a minecraft server can be started in a tmux session via systemd. This allows to easily start and stop the server while still being able to connect to its console.

## Requirements

`tmux` needs to be installed on the system.

The script was written for the following settings. If any of those don't match your system, you might have to change the script accordingly.
* A user named `minecraft` exists on the system. This user will run the minecraft server.
* The users home directory is `/var/minecraft`
* The server files and its working directory match the home directory (`/var/minecraft`)
* The server is a spigot server (although other minecraft servers or a vanilla server should work too)

## Installation

* Place the `service.sh` file in the home directory of the `minecraft` user.
* Change the owner of the script to `minecraft` and make sure it is executable.
* Copy the `minecraft.service` file to `/lib/systemd/system/` and reload the systemd daemon
```
systemctl daemon-reload
```

## Usage

You can now start the server via systemd:
```
systemctl start minecraft
```

To attach to the tmux session that the service is running in, run:
```
/var/minecraft/service.sh attach
```

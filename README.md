**Application**

[RustRover](https://www.jetbrains.com/rust/)

**Description**

RustRover allows you to write code faster by completing relevant names everywhere in your code, adding details such as missing fields, imports, or trait methods, and generating typical constructs with live templates.
While you type, RustRover applies a set of inspections to your code and suggests quick-fixes to resolve any problems automatically. RustRover offers many refactorings that work across the whole codebase.

**Build notes**

Latest EAP RustRover release from Arch User Repository (AUR).

**Usage**
```
docker run -d \
    -p 5900:5900 \
    -p 6080:6080 \
    --name=<container name> \
    --security-opt seccomp=unconfined \
    -v <path for config files>:/config \
    -v <path for data files>:/data \
    -v /etc/localtime:/etc/localtime:ro \
    -e WEBPAGE_TITLE=<name shown in browser tab> \
    -e VNC_PASSWORD=<password for web ui> \
    -e ENABLE_STARTUP_SCRIPTS=<install additional packages> \
    -e UMASK=<umask for created files> \
    -e PUID=<uid for user> \
    -e PGID=<gid for user> \
    binhex/arch-rustrover
```

Please replace all user variables in the above command defined by <> with the correct values.

**Example**
```
docker run -d \
    -p 5900:5900 \
    -p 6080:6080 \
    --name=rustrover \
    --security-opt seccomp=unconfined \
    -v /apps/docker/rustrover:/config \
    -v /apps/docker/rustrover/projects:/data \
    -v /etc/localtime:/etc/localtime:ro \
    -e WEBPAGE_TITLE=Tower \
    -e VNC_PASSWORD=mypassword \
    -e ENABLE_STARTUP_SCRIPTS=yes \
    -e UMASK=000 \
    -e PUID=0 \
    -e PGID=0 \
    binhex/arch-rustrover
```

**Access via web interface (noVNC)**

`http://<host ip>:<host port>/vnc.html?resize=remote&host=<host ip>&port=<host port>&&autoconnect=1`

e.g.:-

`http://192.168.1.10:6080/vnc.html?resize=remote&host=192.168.1.10&port=6080&&autoconnect=1`

**Access via VNC client**

`<host ip>::<host port>`

e.g.:-

`192.168.1.10::5900`

**Notes**

`ENABLE_STARTUP_SCRIPTS` when set to `yes` will allow a user to install additional packages from the official Arch Repository or the Arch User Repository (AUR) via scripts located in the folder `/config/home/scripts/`. A sample script is located at `/config/home/scripts/example-startup-script.sh` with comments to guide the user on script creation.

User ID (PUID) and Group ID (PGID) can be found by issuing the following command for the user you want to run the container as:-

```
id <username>
```
___
If you appreciate my work, then please consider buying me a beer  :D

[![PayPal donation](https://www.paypal.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MM5E27UX6AUU4)

[Documentation](https://github.com/binhex/documentation) | [Support forum](https://forums.unraid.nets/topic/62598-support-binhex-rustrover/)
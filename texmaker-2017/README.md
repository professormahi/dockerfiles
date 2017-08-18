# Texmaker 2017
You can have texmaker with latex (`texlive 2017`) redirected to your X.

## To run
```bash

docker run -it --rm=true \
  -e USER=$USER -e USERID=$UID \		# bind user for file permissions
	-v /tmp/.X11-unix:/tmp/.X11-unix \ 	# mount the X11 socket
	-e DISPLAY=unix$DISPLAY \ 			# pass the display
	--device /dev/dri \
	-v $HOME:/home/texmaker \			# mount $HOME
	--name texmaker professormahi/texmaker-2017
```

or you can create an alias:

```bash
alias texmaker-docker='docker run -it --rm=true -e USER=$USER -e USERID=$UID -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY --device /dev/dri -v $HOME:/home/texmaker --name texmaker professormahi/texmaker-2017'
```
## Possible Problems
If you have this error:

> QXcbConnection: Could not connect to display unix:0.0

you can must use `xhost +` to allow using of display.

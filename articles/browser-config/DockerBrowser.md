Using the i2p Browser via Docker
================================

Docker users can run a modified Tor Browser intended for use with i2p by using
a pre-built container or by building and running their own containers.

If you just want to pull the image from Docker Hub and get started, you can run:

```sh
docker run --rm -i -t \
	-e DISPLAY=:0 \
	--net host \
	--name i2p-browser \
	--volume /tmp/.X11-unix:/tmp/.X11-unix:ro \
    eyedeekay/firefox.profile.i2p
```

To launch a Tor Browser configured with this profile from the terminal.

If you have trouble connecting the Dockerized application to the X server, you
may need to authorize the Docker user to access the X server.

```sh
xhost +"local:docker@"
```

and run the previous 'docker run' command again.

If you want to build the container locally from source, you can clone the
firefox.profile.i2p repository

```sh
git clone https://github.com/eyedeekay/firefox.profile.i2p && cd firefox.profile.i2p
```

and run the docker build command to set up the image

```sh
docker build -f Dockerfiles/Dockerfile -t eyedeekay/firefox.profile.i2p .
```

or use the docker-browser make target(it does the same thing).

```sh
make docker-browser
```

Now you can use the same command from before to launch your locally-built
version of the container.

In order to examine or build the upstream package locally, see:
[eyedeekay/tbb-docker](https://github.com/eyedeekay/tbb-docker).


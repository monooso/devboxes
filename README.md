# Devboxes
Experiments in using Docker as an IDE.

## Building the base image
The `base-alpine` image copies your SSH keys into the image[^1]. In order to accomplish this madness, it requires multiple build contexts, which are a feature of [BuildX](https://github.com/docker/buildx).

If you're using Docker for Mac, BuildX is already installed. If you're using Linux, you're probably in the wrong place.

Here's the command to build the base image. Note the trailing period:

```sh
docker buildx build -t monooso/base-alpine:latest -f base-alpine --build-context /path/to/your/home/directory/.ssh:/root/.ssh .
```

[^1]: Yes, I'm aware this is a terrible thing to do, but: (1) it's an experiment; (2) is is strictly intended for local use only; (3) getting SSH commit signing to work with forwarded SSH keys is beyond me.



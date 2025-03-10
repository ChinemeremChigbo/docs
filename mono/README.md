<!--

********************************************************************************

WARNING:

    DO NOT EDIT "mono/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "mono/" combined with a set of templates)

********************************************************************************

-->

# Quick reference

-	**Maintained by**:  
	[the Mono Project](https://github.com/mono/docker)

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://dockr.ly/slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

# Supported tags and respective `Dockerfile` links

-	[`6.12.0.182`, `latest`, `6.12.0`, `6.12`, `6`](https://github.com/mono/docker/blob/9293c0cddf31a3dc829fccc6f8e1eb507a91cd34/6.12.0.182/Dockerfile)
-	[`6.12.0.182-slim`, `slim`, `6.12.0-slim`, `6.12-slim`, `6-slim`](https://github.com/mono/docker/blob/9293c0cddf31a3dc829fccc6f8e1eb507a91cd34/6.12.0.182/slim/Dockerfile)
-	[`6.10.0.104`, `6.10.0`, `6.10`](https://github.com/mono/docker/blob/0403aaf506b8f6859332a5035f660a7a228d3a97/6.10.0.104/Dockerfile)
-	[`6.10.0.104-slim`, `6.10.0-slim`, `6.10-slim`](https://github.com/mono/docker/blob/0403aaf506b8f6859332a5035f660a7a228d3a97/6.10.0.104/slim/Dockerfile)

# Quick reference (cont.)

-	**Where to file issues**:  
	[https://github.com/mono/docker/issues](https://github.com/mono/docker/issues)

-	**Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
	[`amd64`](https://hub.docker.com/r/amd64/mono/), [`arm32v5`](https://hub.docker.com/r/arm32v5/mono/), [`arm32v7`](https://hub.docker.com/r/arm32v7/mono/), [`arm64v8`](https://hub.docker.com/r/arm64v8/mono/), [`i386`](https://hub.docker.com/r/i386/mono/), [`ppc64le`](https://hub.docker.com/r/ppc64le/mono/)

-	**Published image artifact details**:  
	[repo-info repo's `repos/mono/` directory](https://github.com/docker-library/repo-info/blob/master/repos/mono) ([history](https://github.com/docker-library/repo-info/commits/master/repos/mono))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images repo's `library/mono` label](https://github.com/docker-library/official-images/issues?q=label%3Alibrary%2Fmono)  
	[official-images repo's `library/mono` file](https://github.com/docker-library/official-images/blob/master/library/mono) ([history](https://github.com/docker-library/official-images/commits/master/library/mono))

-	**Source of this description**:  
	[docs repo's `mono/` directory](https://github.com/docker-library/docs/tree/master/mono) ([history](https://github.com/docker-library/docs/commits/master/mono))

# What is Mono

Sponsored by Xamarin, Mono is an open source implementation of Microsoft's .NET Framework based on the ECMA standards for C# and the Common Language Runtime. A growing family of solutions and an active and enthusiastic contributing community is helping position Mono to become the leading choice for development of cross platform applications.

-	[Mono Project homepage](http://www.mono-project.com/)
-	[http://en.wikipedia.org/wiki/Mono_(software)](http://en.wikipedia.org/wiki/Mono_%28software%29)

![logo](https://raw.githubusercontent.com/docker-library/docs/7413e5cdbaae1016411b9fc20950dd913a799e2c/mono/logo.png)

# How to use this image

To run a pre-built .exe file with the Mono image, use the following commands:

```dockerfile
FROM mono:latest
RUN mkdir /opt/app
COPY HelloWorld.exe /opt/app
CMD ["mono", "/opt/app/HelloWorld.exe"]
```

You can build and run the Docker Image as shown in the following example:

```console
docker build -t monoapp .
docker run -it --rm monoapp
```

# Credits

This Docker image is provided by Xamarin, for users of the Mono Project.

Thanks to [Michael Friis](http://friism.com/) for his preliminary work.

# Image Variants

The `mono` images come in many flavors, each designed for a specific use case.

## `mono:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of.

## `mono:<version>-slim`

This image does not contain the common packages contained in the default tag and only contains the minimal packages needed to run `mono`. Unless you are working in an environment where *only* the `mono` image will be deployed and you have space constraints, we highly recommend using the default image of this repository.

# License

This Docker Image is licensed with the Expat License. See the [Mono Project licensing FAQ](http://www.mono-project.com/docs/faq/licensing/) for details on how Mono and associated libraries are licensed.

As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).

Some additional license information which was able to be auto-detected might be found in [the `repo-info` repository's `mono/` directory](https://github.com/docker-library/repo-info/tree/master/repos/mono).

As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

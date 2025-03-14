<!--

********************************************************************************

WARNING:

    DO NOT EDIT "traefik/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "traefik/" combined with a set of templates)

********************************************************************************

-->

# Quick reference

-	**Maintained by**:  
	[the Traefik Project](https://github.com/traefik/traefik-library-image)

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://dockr.ly/slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

# Supported tags and respective `Dockerfile` links

-	[`v2.8.3-windowsservercore-1809`, `2.8.3-windowsservercore-1809`, `v2.8-windowsservercore-1809`, `2.8-windowsservercore-1809`, `vacherin-windowsservercore-1809`, `windowsservercore-1809`](https://github.com/traefik/traefik-library-image/blob/1b242b751fe417c2db296d283f1d85d29f455ddd/windows/1809/Dockerfile)
-	[`v2.8.3`, `2.8.3`, `v2.8`, `2.8`, `vacherin`, `latest`](https://github.com/traefik/traefik-library-image/blob/1b242b751fe417c2db296d283f1d85d29f455ddd/alpine/Dockerfile)
-	[`v1.7.34-windowsservercore-1809`, `1.7.34-windowsservercore-1809`, `v1.7-windowsservercore-1809`, `1.7-windowsservercore-1809`, `maroilles-windowsservercore-1809`](https://github.com/traefik/traefik-library-image/blob/4434758cf14bbd1ec9511b3f2a37b0a6ce846db6/windows/1809/Dockerfile)
-	[`v1.7.34-alpine`, `1.7.34-alpine`, `v1.7-alpine`, `1.7-alpine`, `maroilles-alpine`](https://github.com/traefik/traefik-library-image/blob/4434758cf14bbd1ec9511b3f2a37b0a6ce846db6/alpine/Dockerfile)
-	[`v1.7.34`, `1.7.34`, `v1.7`, `1.7`, `maroilles`](https://github.com/traefik/traefik-library-image/blob/4434758cf14bbd1ec9511b3f2a37b0a6ce846db6/scratch/Dockerfile)

# Quick reference (cont.)

-	**Where to file issues**:  
	[https://github.com/traefik/traefik-library-image/issues](https://github.com/traefik/traefik-library-image/issues)

-	**Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
	[`amd64`](https://hub.docker.com/r/amd64/traefik/), [`arm32v6`](https://hub.docker.com/r/arm32v6/traefik/), [`arm64v8`](https://hub.docker.com/r/arm64v8/traefik/), [`s390x`](https://hub.docker.com/r/s390x/traefik/), [`windows-amd64`](https://hub.docker.com/r/winamd64/traefik/)

-	**Published image artifact details**:  
	[repo-info repo's `repos/traefik/` directory](https://github.com/docker-library/repo-info/blob/master/repos/traefik) ([history](https://github.com/docker-library/repo-info/commits/master/repos/traefik))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images repo's `library/traefik` label](https://github.com/docker-library/official-images/issues?q=label%3Alibrary%2Ftraefik)  
	[official-images repo's `library/traefik` file](https://github.com/docker-library/official-images/blob/master/library/traefik) ([history](https://github.com/docker-library/official-images/commits/master/library/traefik))

-	**Source of this description**:  
	[docs repo's `traefik/` directory](https://github.com/docker-library/docs/tree/master/traefik) ([history](https://github.com/docker-library/docs/commits/master/traefik))

![logo](https://raw.githubusercontent.com/docker-library/docs/a6cc2c5f4bc6658168f2a0abbb0307acaefff80e/traefik/logo.png)

[Traefik](https://traefik.io) is a modern HTTP reverse proxy and load balancer that makes deploying microservices easy.

Traefik integrates with your existing infrastructure components ([Docker](https://www.docker.com/), [Swarm mode](https://docs.docker.com/engine/swarm/), [Kubernetes](https://kubernetes.io), [Marathon](https://mesosphere.github.io/marathon/), [Consul](https://www.consul.io/), [Etcd](https://coreos.com/etcd/), [Rancher](https://rancher.com), [Amazon ECS](https://aws.amazon.com/ecs), ...) and configures itself automatically and dynamically.

Pointing Traefik at your orchestrator should be the *only* configuration step you need.

# Traefik v2 - Example usage

Enable `docker` provider and web UI:

```yml
## traefik.yml

# Docker configuration backend
providers:
  docker:
    defaultRule: "Host(`{{ trimPrefix `/` .Name }}.docker.localhost`)"

# API and dashboard configuration
api:
  insecure: true
```

Start Traefik:

```bash
docker run -d -p 8080:8080 -p 80:80 \
-v $PWD/traefik.yml:/etc/traefik/traefik.yml \
-v /var/run/docker.sock:/var/run/docker.sock \
traefik:v2.5
```

Start a backend server, named `test`:

```bash
docker run -d --name test traefik/whoami
```

And finally, you can access to your `whoami` server throught Traefik, on the domain name `test.docker.localhost`:

```console
# $ curl --header 'Host:test.docker.localhost' 'http://localhost:80/'
$ curl test.docker.localhost
Hostname: 390a880bdfab
IP: 127.0.0.1
IP: 172.17.0.3
GET / HTTP/1.1
Host: test.docker.localhost
User-Agent: curl/7.65.3
Accept: */*
Accept-Encoding: gzip
X-Forwarded-For: 172.17.0.1
X-Forwarded-Host: test.docker.localhost
X-Forwarded-Port: 80
X-Forwarded-Proto: http
X-Forwarded-Server: 7e073cb54211
X-Real-Ip: 172.17.0.1
```

The web UI [http://localhost:8080](http://localhost:8080) will give you an overview of the routers, services, and middlewares.

![Web UI](https://raw.githubusercontent.com/traefik/traefik/v2.5/docs/content/assets/img/webui-dashboard.png)

# Traefik v1 - Example usage

Grab a [sample configuration file](https://raw.githubusercontent.com/traefik/traefik/v1.7/traefik.sample.toml) and rename it to `traefik.toml`. Enable `docker` provider and web UI:

```toml
## traefik.toml

# API and dashboard configuration
[api]

# Docker configuration backend
[docker]
  domain = "docker.localhost"
```

Start Traefik:

```bash
docker run -d -p 8080:8080 -p 80:80 \
-v $PWD/traefik.toml:/etc/traefik/traefik.toml \
-v /var/run/docker.sock:/var/run/docker.sock \
traefik:v1.7
```

Start a backend server, named `test`:

```bash
docker run -d --name test traefik/whoami
```

And finally, you can access to your `whoami` server throught Traefik, on the domain name `{containerName}.{configuredDomain}` (`test.docker.localhost`):

```console
# $ curl --header 'Host:test.docker.localhost' 'http://localhost:80/'
$ curl 'http://test.docker.localhost'
Hostname: 117c5530934d
IP: 127.0.0.1
IP: ::1
IP: 172.17.0.3
IP: fe80::42:acff:fe11:3
GET / HTTP/1.1
Host: test.docker.localhost
User-Agent: curl/7.35.0
Accept: */*
Accept-Encoding: gzip
X-Forwarded-For: 172.17.0.1
X-Forwarded-Host: 172.17.0.3:80
X-Forwarded-Proto: http
X-Forwarded-Server: f2e05c433120
```

The web UI [http://localhost:8080](http://localhost:8080) will give you an overview of the frontends/backends and also a health dashboard.

![Web UI Providers](https://raw.githubusercontent.com/traefik/traefik/v1.7/docs/img/web.frontend.png)

# Documentation

You can find the complete documentation:

-	for [v2.x](https://doc.traefik.io/traefik/)
-	for [v1.7](https://doc.traefik.io/traefik/v1.7)

A community support is available at [https://community.traefik.io](https://community.traefik.io)

A collection of contributions around Traefik can be found at [https://awesome.traefik.io](https://awesome.traefik.io).

# Image Variants

The `traefik` images come in many flavors, each designed for a specific use case.

## `traefik:<version>`

This is the defacto image. If you are unsure about what your needs are, you probably want to use this one. It is designed to be used both as a throw away container (mount your source code and start the container to start your app), as well as the base to build other images off of.

## `traefik:<version>-windowsservercore`

This image is based on [Windows Server Core (`microsoft/windowsservercore`)](https://hub.docker.com/r/microsoft/windowsservercore/). As such, it only works in places which that image does, such as Windows 10 Professional/Enterprise (Anniversary Edition) or Windows Server 2016.

For information about how to get Docker running on Windows, please see the relevant "Quick Start" guide provided by Microsoft:

-	[Windows Server Quick Start](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/quick_start/quick_start_windows_server)
-	[Windows 10 Quick Start](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/quick_start/quick_start_windows_10)

# License

View [license information](https://github.com/traefik/traefik/blob/master/LICENSE.md) for the software contained in this image.

As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).

Some additional license information which was able to be auto-detected might be found in [the `repo-info` repository's `traefik/` directory](https://github.com/docker-library/repo-info/tree/master/repos/traefik).

As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

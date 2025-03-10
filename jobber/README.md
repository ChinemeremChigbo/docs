<!--

********************************************************************************

WARNING:

    DO NOT EDIT "jobber/README.md"

    IT IS AUTO-GENERATED

    (from the other files in "jobber/" combined with a set of templates)

********************************************************************************

-->

# **DEPRECATION NOTICE**

This project is not actively maintained. See [dshearer/jobber#334](https://github.com/dshearer/jobber/pull/334) for more details.

# Quick reference

-	**Maintained by**:  
	[Jobber](https://github.com/dshearer/jobber-docker)

-	**Where to get help**:  
	[the Docker Community Forums](https://forums.docker.com/), [the Docker Community Slack](https://dockr.ly/slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

# Supported tags and respective `Dockerfile` links

-	[`1.4.4-alpine3.11`, `1.4-alpine3.11`, `1-alpine3.11`, `latest`](https://github.com/dshearer/jobber-docker/blob/cd07d76987097b5389aa9be5f48df041aa74d699/alpine3.11/Dockerfile)

# Quick reference (cont.)

-	**Where to file issues**:  
	[https://github.com/dshearer/jobber-docker/issues](https://github.com/dshearer/jobber-docker/issues)

-	**Supported architectures**: ([more info](https://github.com/docker-library/official-images#architectures-other-than-amd64))  
	[`amd64`](https://hub.docker.com/r/amd64/jobber/)

-	**Published image artifact details**:  
	[repo-info repo's `repos/jobber/` directory](https://github.com/docker-library/repo-info/blob/master/repos/jobber) ([history](https://github.com/docker-library/repo-info/commits/master/repos/jobber))  
	(image metadata, transfer size, etc)

-	**Image updates**:  
	[official-images repo's `library/jobber` label](https://github.com/docker-library/official-images/issues?q=label%3Alibrary%2Fjobber)  
	[official-images repo's `library/jobber` file](https://github.com/docker-library/official-images/blob/master/library/jobber) ([history](https://github.com/docker-library/official-images/commits/master/library/jobber))

-	**Source of this description**:  
	[docs repo's `jobber/` directory](https://github.com/docker-library/docs/tree/master/jobber) ([history](https://github.com/docker-library/docs/commits/master/jobber))

# What is Jobber?

Jobber is a utility for Unix-like systems that can run arbitrary commands, or "jobs", according to a schedule. It is meant to be a better alternative to the classic Unix utility cron.

Along with the functionality of cron, Jobber also provides:

-	**Job execution history:** you can see what jobs have recently run, and whether they succeeded or failed.
-	**Sophisticated error handling:** you can control whether and when a job is run again after it fails. For example, after an initial failure of a job, Jobber can schedule future runs using an exponential backoff algorithm.
-	**Sophisticated error reporting:** you can control whether Jobber notifies you about each failed run, or only about jobs that have been disabled due to repeated failures.

# How to use this image

This image contains Jobber running as an unprivileged user named "jobberuser". The jobs are defined in the file /home/jobberuser/.jobber. By default, the only job is one that prints "Jobber is running!" every second. You should replace it with your own jobs. Refer to [the documentation](https://dshearer.github.io/jobber/doc/v1.4/#jobfile) to learn how to do this.

# License

[Jobber's license](https://github.com/dshearer/jobber/blob/master/LICENSE)

As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).

Some additional license information which was able to be auto-detected might be found in [the `repo-info` repository's `jobber/` directory](https://github.com/docker-library/repo-info/tree/master/repos/jobber).

As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

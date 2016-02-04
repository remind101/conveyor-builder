# Conveyor Builder

This is a Docker image for use with [Conveyor](https://github.com/remind101/conveyor) and the [Docker builder](https://github.com/remind101/conveyor/tree/master/builder/docker)

It does the following:

* Clones the GitHub repo.
* Pulls the last built docker image for the given branch.
* Builds a new image.
* Tags the new image with latest as well as the name of the branch and the git sha.
* Pushes the image to the docker registry.

## Usage

This image expects the following files to be present:

* `/var/run/conveyor/.dockercfg`: `.dockercfg` file for credentials to use when pulling.
* `/var/run/conveyor/.ssh`: Should contain an `id_rsa` and `id_rsa.pub` file which gives access to pull GitHub repos.

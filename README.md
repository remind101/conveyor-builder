# Conveyor Builder

This is a Docker image for use with [Conveyor](https://github.com/remind101/conveyor) and the [Docker builder](https://github.com/remind101/conveyor/tree/master/builder/docker)

It does the following:

* Clones the GitHub repo.
* Pulls the last built docker image for the given branch.
* Builds a new image.
* Tags the new image with latest as well as the name of the branch and the git sha.
* Pushes the image to the docker registry.

## Usage

You can use this image outside of Conveyor to build and push images:

```console
$ docker run --privileged=true \
  -v "${HOME}/.dockercfg:/var/run/conveyor/.dockercfg" \
  -v "${HOME}/.ssh/id_rsa:/var/run/conveyor/.ssh/id_rsa" \
  -v "${HOME}/.ssh/id_rsa.pub:/var/run/conveyor/.ssh/id_rsa.pub" \
  -e REPOSITORY=remind101/acme-inc \
  -e BRANCH=master \
  -e SHA=d4c832fcc95974bd017567b44868194a38b3b03a \
  -e DRY=true \
  remind101/conveyor-builder
```

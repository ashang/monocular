# Monocular

- Under ACTIVE development

Monocular is a search and discovery front end for Helm Charts Repositories. Charts Repositories are collections of curated Kubernetes application definitions.

A monocular is a single-lensed telescope, and perhaps a twee synonym for the kind of kit that would be useful when inspecting a disordered stack of nautical charts, like a magnifying glass or microscope with a spyglass aesthetic. Its adjectival form suggests a Cyclops, with whom Oddysseus was definitely on familiar terms; and its closest synonym is monocle, a well-worn accoutrement of Victorian Great Britain, surely the greatest of all naval empires. `kubernetes` indeed.

As with The Beatles, some things are better in mono.

Visit [the Helm repository](https://github.com/kubernetes/helm) to learn more about Helm, the package manager for Kubernetes.

Visit [the Charts repository](https://github.com/kubernetes/charts) to learn more about Charts, the Helm unit of configuration for a Kubernetes application definition.

# App Structure

Monocular comprises a UI front end, and a RESTFul HTTP back end API.

# UI Prerequisites

The UI is an angular 2 client application located in `src/ui/`.

More UI docs are [here](src/ui/README.md).

# API Prerequisites

The API is a golang HTTP server located in `src/api/`.

`Makefile` assumes [docker](https://www.docker.com) for containerized development; and [glide](http://glide.sh) for dependency enforcement.

`cd src/api/ && make bootstrap` will launch a docker container, and run a `glide install` command to install all API dependencies in the `src/api/vendor/` directory.

More API docs are [here](src/api/README.md).

# Running a development environment

We leverage [docker](https://www.docker.com) (via `docker-compose`) to provide a multi-tier setup for development.

Running `docker-compose up` from the root directory will expose:

* API backend endpoint via `http://{your-docker-machine-ip-address}:8080`
* UI frontend via `http://{your-docker-machine-ip-address}:4200`  

**IMPORTANT**: 
* If your Docker Machine hostname is different than *localhost*, you need to change
the `backendHostname` value in the file `src/ui/src/app/config.ts`.
* Run `docker pull bitnami/angular:2.0.0` OR Run `docker login` which will cache your docker hub credentials. 
Angular:2.0.0 image is required during `docker-compose up` and docker will search local cache or pull image from docker hub.

You can restart individual services doing `docker-compose restart api|ui`

# Status of the Project

This project is still under active development, so you'll likely encounter [issues](https://github.com/helm/monocular/issues). Please participate by filing issues or contributing a pull request!

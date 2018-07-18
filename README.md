# go-aws-bitbucket-docker

This is a template for a Go monolithic API development and deployment pipeline/

* Development is done locally in a Docker container
* Using Bitbucket Pipelines for CI/CD
* Same Docker container is pushed to AWS ECS

## Go, GOPATH and symlink setup

The `go-aws-bitbucket-docker` project requires Go version 1.10.3. Please ensure your GOPATH is set up correctly, i.e `echo $GOPATH` should return your Go directory, for example `/Users/Olliepop/go`.

The project should be cloned into a src directory structure, properly representing ownership i.e `~/go/src/github.com/Olliepop/go-aws-bitbucket-docker`.

It is recommended you set up a symlink so that the directory is more easily accessible. For example, given the above directories and structure, set up a symlink to the project in your home directory with `ln -s ~/go/src/github.com/Olliepop/go-aws-bitbucket-docker ~/go-aws-bitbucket-docker`.

## Docker

Build the container.

`docker build -t go-aws-bitbucket-docker .`

Run the container in detached mode (in the background).

`docker run -d --rm -it -p 80:80 go-aws-bitbucket-docker`

## CI/CD on branches

This repository uses Bitbucket Pipelines to test, build, and deploy. The rules are defined in [bitbucket-pipelines.yml](bitbucket-pipelines.yml).

### `develop` branch

The `develop` branch is always maintained on staging.

### `release` branch

The `release` branch is always maintained on production. Releases should **always** be tagged, but this is not a requirement for the deployment.

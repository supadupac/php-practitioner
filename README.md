# Chris' Docker Config
This Github Repo is used alongside with the Docker Hub repo.

https://hub.docker.com/

https://hub.docker.com/repository/docker/supadupac/lamp

## Pre-Configuration

1. Ensure to have configured an External Docker Bridge Network
2. Create a new folder or branch when building new environments

## Docker Network
`docker network create --driver=bridge --subnet=42.42.0.0/16 --ip-range=42.42.42.2/24 --gateway=42.42.42.1 name-net`

## Image Repo

`docker pull supadupac/lamp:latest`

## Running

`docker-compose up -d`

## If image is bad

Rebuild the dockerfile to make a new image. Ensure to push the image to Dockerhub.

`docker-compose up --build`
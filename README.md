# Chris' Docker Config
This Github Repo is used alongside with the Docker Hub repo.

https://hub.docker.com/

https://hub.docker.com/repository/docker/supadupac/lamp

## Pre-Configuration

1. Ensure to have configured an External Docker Bridge Network
2. Create a new folder or branch when building new environments

## Docker Network
`docker network create --driver=bridge --subnet=42.42.0.0/16 --ip-range=42.42.42.2/24 --gateway=42.42.42.1 name-net`

`docker network create --driver=bridge --subnet=42.42.0.0/16 --ip-range=42.42.42.2/24 --gateway=42.42.42.1 capus-net`

## Image Repo

`docker pull supadupac/lamp:latest`

## Running

`docker-compose up -d`

## If image is bad

Rebuild the dockerfile to make a new image. Ensure to push the image to Dockerhub.

`docker-compose up --build`

# Mysql
## Post-configuration

Default MySql login
`root`
`[blank]`


### Reset your root password for mysql

```mysql
ALTER USER 'root'@'%' IDENTIFIED BY 'password';
```

## Set up the Database

```mysql
CREATE mytodos; 
```

## Set up the tables
```mysql
create table todos
(
    id          int auto_increment
        primary key,
    description varchar(255) null,
    completed   tinyint(1)   null
);
```

### Set up the data

```mysql
INSERT INTO mytodo.todos (description, completed)
VALUES ('goto the store', 1);
```

```mysql
INSERT INTO mytodo.todos (description, completed)
VALUES ('finish up screencast', 0);
```
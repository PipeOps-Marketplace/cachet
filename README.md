# Cachet on PipeOps

Cachet is a beautiful and powerful open source status page system, a free replacement for services such as StatusPage.io, Status.io and others.

[![Deploy on PipeOps](https://pub-a1fbf367a4cd458487cfa3f29154ac93.r2.dev/Default.png)](https://railway.app/template/0ELOuE?referralCode=IQhE0B)


# Supporting Cachet

Cachet is a BSD-3-licensed open source project. If you'd like to support future development, check out the Cachet Patreon campaign.


# Quickstart

Clone this repository

    git clone https://github.com/CachetHQ/Docker.git

Edit the docker-compose.yml file to specify your ENV variables.

To build an image containing a specific Cachet release, set the cachet_ver ARG in the docker-compose.yml

The master branch and cachethq/docker:latest Docker automated build are a work in progress / development version of the upstream https://github.com/CachetHQ/Cachet project. As such, master or latest should not be used in a production environment as it can change at anytime.

We strongly recommend specifying a stable Cachet Release at build time as mentioned above.

Build and run the image

    docker-compose build
    docker-compose up

cachethq/docker runs on port 8000 by default. This is exposed on host port 80 when using docker-compose.

Setup the APP_KEY

Whilst the container is up and running, find the name of the Cachet container via docker ps.

Run docker exec -i ID_OF_THE_CONTAINER php artisan key:generate.

Replace ${APP_KEY:-null} in docker-compose.yml with the newly generated Application key.

Note: make sure you include base64: prefix. E.g. base64:YOUR_UNIQUE_KEY

Restart the Docker containers.


# Debugging

The services such as Cachet, supervisord, nginx, and php-fpm log to stdout and stderr, and are visible in the Docker runtime output.

Setting the DEBUG Docker environment variable within the docker-compose.yml file or at runtime to true will enable debugging of the container entrypoint init script.

# Testing

Pull requests must pass the Bash Automated Testing System tests, which run on Travis CI via located in the test directory.

Use make test to manually run the tests.

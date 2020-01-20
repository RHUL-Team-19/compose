# compose
Docker compose config files

### wait, what is Docker?
Docker is a application containerisation platform. It allows you to 'compile' your programs and their necessary runtime environments into 'images' - which can be 'deployed' as 'containers' on any machine running Docker. The names and terminology surrounding Docker come from the freight industry's very ubiquitous shipping container - a great example of standardisation and abstraction in the real world. All shipping containers are the same on the outside - and thus will fit on any ship that carries containers. A container can contain anything (literally anything) and it will still fit on any freight ship.

In Docker, your application (which can be/do anything, and can depend on a whole bunch of things to run correctly) is put inside a container, and that container is deployed on the Docker daemon. Docker doesn't know - or care - about the contents of any container, it only knows about each container at a superficial level.

### and what is compose?
Docker, by itself, just handles containers - you must manually create and destroy those containers via the command line. This can quickly become tedious, especially when your program/project consists of multiple containers (usually referred to as a 'stack'). Docker compose is a small CLI tool that allows you to define (or compose) stacks in a configuration file, and then deploy and re-deploy those stacks using one command. These configuration files are always named 'docker-compose.yml' and are written in YAML, a special mark-up language.

### microservices
The oaxaca-com stack consists of three core applications: two web UI, one backend API. The API persists data to a Postgres instance (which also runs as a container, but with a persistent storage volume).

#### training-oaxaca-com
Is the web application for training Oaxaca's staff. It is simply a React app that pulls menu data down from the api-oaxaca-com service. When deployed, the container will listen on <container's hostname>:8080. The compose config for this service is in frontend/docker-compose.yml.

#### waiting-oaxaca-com
Is the web application for running Oaxaca's day-to-day restaurant business. It is used by waiters to manage cutsomer orders. It is simply a React app that pushes and pulls data from the api-oaxaca-com service. When deployed, the container will listen on <container's hostname>:8080. The compose config for this this service is in frontend/docker-compose.yml.

#### api-oaxaca-com
Is the backend RESTful HTTP API for managing data in Oaxaca's database. It defines resources and allows GET/POST/PUT/PATCH/DELETE opereations on those resources. It handles database schema, input validation, authentication, and authorisation. This service depends on a Postgres container with the hostname 'postgres' on a separate Docker virtual network listening on 5432. The compose config for this service (and Postgres) is in backend/docker-compose.yml.

:)

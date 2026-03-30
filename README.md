# SCA UEPA - Backend

<!--toc:start-->
- [SCA UEPA - Backend](#sca-uepa-backend)
  - [Description](#description)
  - [Dependencies](#dependencies)
  - [Tools](#tools)
  - [Initial setup](#initial-setup)
  - [Essential commands](#essential-commands)
    - [Running other commands inside containers](#running-other-commands-inside-containers)
    - [Git](#git)
    - [Docker and Docker Compose](#docker-and-docker-compose)
      - [Building the environment](#building-the-environment)
      - [Handling containers and images](#handling-containers-and-images)
    - [Prisma](#prisma)
    - [Node.js](#nodejs)
<!--toc:end-->

## Description

SCA UEPA is a web app built with NestJS + Prisma for the backend and React + Vite for the user interface. The goal is to provide a simple and effective way to manage the allocation of rooms in the State University of Pará.

This is the repository for the backend development of SCA.

## Dependencies

To run this project it is recommend you have the following dependencies installed on your machine:

- `git`
- `docker`
- `docker-compose`

## Tools

- NestJS API with Prisma for the backend and structure of the database.
- Neon Database for hosting the cloud database server.
- Docker and Docker compose for multi-service dev/prod setups.

## Initial setup

- Clone the repository:
  - `git clone https://github.com/Felopssauro/sca-backend.git`
- Provide environment variables inside a .env file for Docker Compose:
  - `DATABASE_URL`: set this to the link of a Neon Database Server.
  - `JWT_SECRET`
  - Build the containers with docker compose:
    - For development:
      - `docker compose up --build -d`

Now you have a complete setup for development with running containers.

The backend is accessible at `htpp://localhost:3000`

But you also need to know how to make contributions and keep track of your changes using git.

## Essential commands

All commands are explained assuming you are running them from the root directory `sca-backend/`

### Running other commands inside containers

It is important to run all `npm` and `npx prisma` commands inside the containers, because this is where all the installed dependencies will be.

- format: `docker compose exec <command>`
  - e.g.: `docker compose exec npm test`

### Git

- `git checkout dev`: change your work branch to dev.
- `git pull origin dev`: fetch and merge the latest changes of this repository
- `git push origin dev`: push your commits to the dev branch on you remote repository

### Docker and Docker Compose

When running commands using docker compose, you will have to use `-f` flag to select the specific compose file you will be using on the command. You will to add this every time you run a docker compose command.

#### Building the environment

- For development:
  - `docker compose up --build -d`

#### Handling containers and images

- `docker compose exec`: executes commands inside the container.
- `docker compose stop`: stop containers built with compose file.
- `docker compose up`: start containers built with compose file.
- `docker compose rm -f`: force removes stopped containers built with compose file.
- `docker compose down -v`: removes the containers and
networks for that compose file and deletes named volumes.
- `docker image ls`: list docker images.
- `docker image rm <image-id-or-name>`: remove docker images.

### Prisma

All prisma commands also happen inside the container, so be sure to follow the format above to run commands inside containers.

- `npx prisma db push`: Push the new structure to the Neon database.
- `npx prisma generate`: Rebuild the client.
- `npx prisma studio`: Initialize prisma studio to manually add/view rows using the browser interface of Prisma.
  - Access prisma studio at `http://localhost:5555`

### Node.js

- `npm run start:dev`: Generate Prisma client and run NestJS in watch mode.
- `npm run build`: Build the NestJS app.
- `npm run start`: Start the app normally.
- `npm run start:prod`: Run the compiled app (`dist/main`).
- `npm run lint`: ESLint with `--fix`.
- `npm run format`: Prettier on `src/**/*.ts` and `test/**/*.ts`.
- `npm test`: Jest unit tests.
- `npm run test:e2e`: Jest e2e tests (`test/jest-e2e.json`).

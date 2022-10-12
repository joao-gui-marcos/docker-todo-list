# Welcome to the Docker Todo List project repository!

### README Translations:

-   [English](/README.en.md)
-   [Portuguese](/README.md)

* * *

## 👨‍💻 What was developed:

In this project:

1.  **_containerized_**applications;
2.  I created a connection between them;
3.  I orchestrated its operation.

We have a full-stack application (docker/todo-app). This application needs to be containerized to work. I developed the configuration files for each specific front:`Front-end`,`Back-end`and, in this case, for an application of`teste`that validates whether applications are communicating.

I created the images for the applications and configured those images with the`docker-compose`.

For this, I used a series of commands from the`docker`with different levels of complexity.

# Mandatory project requirements

## docker commands

### 1. Create a container in interactive mode, without running it, naming it as`01container`and using the image`alpine`in the version`3.12`

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command01.dc`.

#### Technical remarks

-   O container**must not be initialized**, only created;
-   The container must be prepared for interactive access.

#### Tips

-   Take a look at the command[`create`](https://docs.docker.com/engine/reference/commandline/create/). 😉
-   Remember that a parameter is not necessarily applicable to just one command;
-   Consult whenever possible the[Official Documentation](https://docs.docker.com/engine/reference/commandline/docker/)about basic commands;
-   Remember that the overwhelming part of docker commands takes parameters (options) like[in this example](https://docs.docker.com/engine/reference/commandline/logs/#options).

#### what will be tested

-   O`nome`of the container must be`01container`;
-   The container must use the image`alpine`in the version`3.12`;
-   O`status`of the container must be`created`;
-   O container**should not**be running after it was created.

</details>

### 2. Start the container`01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command02.dc`.

#### Technical remarks

-   O container`01container`, which has just been created and is stopped, must be started;
-   If the container was started interactively, it must remain active when you start it.

#### what will be tested

-   The evaluator will check if the container is stopped;
-   The evaluator will run the command created in this requirement;
-   O container**he must**be running.

</details>

### 3. List containers by filtering by name`01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command03.dc`.

#### Tips

-   Virtually every listing command in Docker has a form of filtering.

#### what will be tested

-   The command should return a list containing information**only**do`01container`.

</details>

### 4. Run the command`cat /etc/os-release`no container`01container`without attaching to it

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command04.dc`.

#### Technical remarks

-   The container must be running and you must be able to**run a command**in that container.

#### Tips

-   Is it possible to do this without using the command`attach`.

#### what will be tested

-   That the command will return the correct data from the`distro`no container:
    -   `NAME="Alpine Linux"`
    -   `ID=alpine`
    -   `VERSION_ID=3.12`

</details>

### 5. Remove the container`01container`

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the commands in the files`command05.dc`e`command03.dc`.

#### what will be tested

-   The evaluator will run command 5;
-   The evaluator will validate the process with command 3.

</details>

### 6. Download the image`nginx`with the version`1.21.3-alpine`without creating or running a container

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command06.dc`.

#### what will be tested

-   That the correct image has been downloaded;
-   That no container has been started for this.

</details>

### 7. Run a new container with the image`nginx`with the version`1.21.3-alpine`in the background naming it as`02images`and mapping your default access port to port`3000`of the host system

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command07.dc`.

#### what will be tested

-   That the container was started correctly;
-   That it is possible to have access to the container by the address`localhost:3000`;
-   That the page returns the expected value.

</details>

### 8. Pare o container`02images`which is in progress

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command08.dc`.

#### what will be tested

-   That there is no active container after your command.

</details>

## Dockerfile

**⚠️ The following applications have a \[**README.md**](./docker/todo-app/README.md) which should be used as a reference when creating scripts!**

### 9. Generate a build from the Dockerfile of`back-end`do`todo-app`naming the image to`todobackend`

write to file`command09.dc`a command that will do the`build`([command documentation](https://docs.docker.com/engine/reference/commandline/build/)) of an image from the file`./docker/todo-app/back-end/Dockerfile`, this image must have the name`todobackend`.

In the file`./docker/todo-app/back-end/Dockerfile`write the commands that will make the image:

-   run from the image of`node`in version 14;
-   expose port 3001;
-   add the file`node_modules.tar.gz`the image;
-   copy all files from folder`back-end`for the image. (you can use the relative path, remembering that the`Dockerfile`it's at`./docker/todo-app/back-end/Dockerfile`);
-   start the application with the command`npm start`.

<details>
  <summary>➕ Informações adicionais</summary><br />

-   In this context, you must create a file[`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format)that pasta`./docker/todo-app/back-end/`, which will be used with the command required in the requirement;
-   This file should seek to reproduce the steps of`back-end`contained in the[`README.md`](docker/todo-app/README.md)and_pseudo-application_(they are also described in the section`O que será testado`, of the requirement) so that it runs correctly;
-   The evaluator will run the command in the file`command09.dc`.

#### Tips

-   O[command`ADD`](https://docs.docker.com/engine/reference/builder/#add)from the Dockerfile, it can also be used to unzip files inside the container.
    -   Understand the difference between the command`ADD`e`COPY`[in this article](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).

#### what will be tested

-   If there is a file`Dockerfile`em`./docker/todo-app/back-end/`:
    -   The Dockerfile must run an image`node`using the version`14`;
        -   The use of the variant is recommended`-alpine`, as it is optimized for performance;
        -   Remember to consult the README of`todo-app`to validate application requirements.
    -   Must be with the door`3001`exposed;
    -   must add the file`node_modules.tar.gz`the image;
    -   Must copy all files from folder`back-end`for the image;
    -   When starting the image, run the command`npm start`.
-   if at_buildar_the Dockerfile the name of the generated image is equal to`todobackend`.

</details>

### 10. Generate a build from the Dockerfile of`front-end`do`todo-app`naming the image to`todofrontend`

write to file`command10.dc`a command that will do the`build`([command documentation](https://docs.docker.com/engine/reference/commandline/build/)) of an image from the file`./docker/todo-app/front-end/Dockerfile`, this image must have the name`todofrontend`.

In the file`./docker/todo-app/front-end/Dockerfile`write the commands that will make the image:

-   run from the image of`node`in version 14;
-   expose port 3000;
-   add the file`node_modules.tar.gz`the image;
-   copy all files from folder`front-end`for the image. (you can use the relative path, remembering that the`Dockerfile`it's at`./docker/todo-app/front-end/Dockerfile`);
-   start the application with the command`npm start`.

<details>
  <summary>➕ Informações adicionais</summary><br />

-   In this context, you must create a file[`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format)that pasta`./docker/todo-app/back-end/`, which will be used with the command required in the requirement;
-   This file should seek to reproduce the steps of`front-end`contained in the[`README.md`](docker/todo-app/README.md)and_pseudo-application_(they are also described in the section`O que será testado`, of the requirement) so that it runs correctly;
-   The evaluator will run the command in the file`command10.dc`.

#### Tips

-   O[command`ADD`](https://docs.docker.com/engine/reference/builder/#add)from the Dockerfile, it can also be used to unzip files inside the container.
    -   Understand the difference between the command`ADD`e`COPY`[in this article](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).

#### what will be tested

-   If there is a file`Dockerfile`em`./docker/todo-app/front-end/`:
    -   O`Dockerfile`can rotate an image`node`using the version`14`;
        -   The use of the variant is recommended`-alpine`, as it is optimized for performance;
        -   Remember to consult the README of`todo-app`to validate application requirements.
    -   Must be with the door`3000`exposed;
    -   must add the file`node_modules.tar.gz`the image, so that it is extracted into the`container`;
    -   Must copy all files from folder`front-end`for the image;
    -   When starting the image, run the command`npm start`;
-   if at_buildar_o`Dockerfile`the name of the generated image is equal to`todofrontend`.

</details>

### 11. Generate a build from the Dockerfile of`testes`do`todo-app`naming the image to`todotests`

write to file`command11.dc`a command that will do the`build`([command documentation](https://docs.docker.com/engine/reference/commandline/build/)) of an image from the file`./docker/todo-app/tests/Dockerfile`, this image must have the name`todotests`.

In the file`./docker/todo-app/tests/Dockerfile`write the commands that will make the image:

-   run from the image of`mjgargani/puppeteer:trybe1.0`;
-   add the file`node_modules.tar.gz`the image;
-   copy all files from folder`tests`for the image. (you can use the relative path, remembering that the`Dockerfile`it's at`./docker/todo-app/tests/Dockerfile`);
-   start the tests with the command`npm test`.

<details>
  <summary>➕ Informações adicionais</summary><br />

-   In this context, you must create a file[`Dockerfile`](https://docs.docker.com/engine/reference/builder/#format)that pasta`./docker/todo-app/back-end/`, which will be used with the command required in the requirement;
-   This file should seek to reproduce the steps of`testes`contained in the[`README.md`](docker/todo-app/README.md)and_pseudo-application_(they are also described in the section`O que será testado`, of the requirement) so that it runs correctly;
-   The evaluator will run the command in the file`command11.dc`.

#### Tips

-   O[command`ADD`](https://docs.docker.com/engine/reference/builder/#add)from the Dockerfile, it can also be used to unzip files inside the container.
    -   Understand the difference between the command`ADD`e`COPY`[in this article](https://coderarena.com.br/posts/docker-tips-01-qual-e-a-diferenca-entre-add-e-copy/).

#### Technical remarks

-   The app`todotests`it only works correctly if it is dockerized and inside a properly configured docker network.

#### what will be tested

-   If there is a file`Dockerfile`em`./docker/todo-app/tests/`:
    -   The Dockerfile should run the image`mjgargani/puppeteer:trybe1.0`for the tests to work;
    -   must add the file`node_modules.tar.gz`the image;
    -   Must copy all files from folder`tests`for the image;
    -   When starting the image, run the command`npm test`;
-   if at_buildar_the Dockerfile the name of the generated image is equal to`todotests`.

</details>

# Project Bonus Requirement

## Docker-compose

### 12. Upload a background orchestration with docker-compose so that`backend`,`frontend`e`tests`manage to communicate

<details>
  <summary>➕ Informações adicionais</summary><br />

The evaluator will run the command in the file`command12.dc`. This command assumes the existence of the file`./docker/docker-compose.yml`.

O`docker-compose`must run on version 3 or higher.

#### Tips

-   Use the images now**"built"**that were performed in requirements 9, 10 and 11 for creating compose;
-   See the documentation at`./docker/todo-app/README.md`;
-   It is possible to add and extract files`.tar.gz`no`Dockerfile`with just one command.

#### what will be tested

##### tests

-   the container of`todotests`must have containers as a dependency`frontend`e`backend`;
-   The name of_service_shall be`todotests`;
-   Must have an environment variable`FRONT_HOST`which receives as value the name of the container of the`frontend`
    -   Remembering that, within a docker network, the host of a container is identified by its name.

##### front-end

-   the container of`todofrontend`must run on the door`3000`;
-   The name of_service_shall be`todofront`;
-   It must have the container as a dependency`backend`;
-   Must have an environment variable`REACT_APP_API_HOST`which receives as value the name of the container of the`backend`.
    -   Remembering that, within a docker network, the host of a container is identified by its name.

##### back-end

-   the container of`todobackend`must run on the door`3001`;
-   The name of_service_shall be`todoback`;

</details>

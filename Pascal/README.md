# Pascal Development Environment

This Directory serves as the source code for a Docker image which is hosted on [Docker Hub](https://hub.docker.com/r/dgisolfi/pascal_dev/) and can be pulled, run and used as a development environment for Pascal. The base image has the FreePascal compiler installed, this allows a user to develop programs in an independent environment which avoids complicated downloads and installations on other operating systems. In addition, this keeps your devices hard drive free of compilers that may not be used after the Theory of Programming Languages class is complete.

# Docker Deployment

*Note: If you need assistance with installing Docker, a quick guide can be found [here](https://github.com/dgisolfi/LanguageDevEnvironments)*

To run an instance of the pascal_dev container on your own machine first pull the image by running the following in a terminal:

```bash
docker pull dgisolfi/pascal_dev
```

Next to run an instance of the image as a container run the following:

```bash
docker run -it dgisolfi/pascal_dev bash
```

*Note: If you would like to mount a directory in order to test run the following command instead and replace "/Path/to/Pascal/files" with the path to your files*

```bash
docker run -it -v/Path/to/Pascal/files:/DEV/PascalFiles dgisolfi/pascal_dev bash
```

The result should be command line access as the root user to the now running Docker container. You should be located in the DEV directory within the container. If you chose to Volume mount any files first run `ls` which will list all directories and files, then `cd` into the directory "PascalFiles", anything changed within the mounted directory will be reflected accross both host and container. Due to how volumes work in Docker you have the advantage of the files being shared between the container and your host machine, meaning you may now open the directory up in an IDE and begin to program, any changes in the directory on your host will be reflected in the container.

## Compiling

As an example program, there is an included file "helloworld.pas" located in the "DEV" directory, use this to test the compiler. To compile the file run the following:

```bash
fpc helloworld.pas
```

This will create an executable with the name of the program, in this case, "helloworld" in the directory. Run `./helloworld` to execute the program.

To run your own programs alter the command to use the following format:

`fpc file_name.bas`

**Note: data inside a Docker container is nonpersistent. Only files that exist inside a volume mounted directory will remain after the container is exited** 

With your programs written and mounted you may now use the compiler to test and run them.

## IDE

As an added bonus the FreePascal IDE comes pre-installed in the image, to launch it simply run `fp`.
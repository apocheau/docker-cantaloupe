## Docker Container for Cantaloupe IIIF server ##

Rudimentary containerization of the [Cantaloupe server](https://medusa-project.github.io/cantaloupe), which bakes in a local filesystem 'resolver' (the means by which requested images are found) to a Docker data volume.

### Create the image ###

    docker build -t cantaloupe .

This invocation will download the 2.2 (current at time of writing) release of the software. To override for
newer (or older) versions:

    docker build --build_arg ctl_ver=<desired version> -t cantaloupe .

### Run the container ###

    docker run -d -p 8182:8182 --name melon -v /path/to/images:/imageroot cantaloupe

will run the container in the background until _docker stop_ is called, looking in specified
directory for image files.

Base Docker images 
==================

Docker images and support for base images. They provide basic operating system facilities,
plus all that's needed to run either VNC or Web applications.

We build images by combining parts:

1. A base docker file (a plain ubuntu with some personalized additions), found under `base_images`
2. Boilerplate that just sets up the basics of the infrastructure (e.g. vnc), found under `wrappers`

The composition is done by copying and deploying the first two together in a base image+wrapper
and then use docker building facilities to generate the image. Note that Dockerfile
files are properly generated and merged together.

Automation of the above points is provided in the `scripts` directory in repository
``simphony-remote-docker``.

Docker image names
------------------

1. ``simphonyproject/ubuntu-<ubuntu-version>-<wrapper>:{version}``
         Ubuntu of a given version, together with the given wrapper.
         Example ``simphonyproject/ubuntu-14.04-webapp:v0.3.0``


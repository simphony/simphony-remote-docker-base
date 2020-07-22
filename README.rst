Base Docker images
------------------

Docker images and support for base images. They provide basic operating system facilities,
plus all that's needed to run either VNC or Web applications.

We build images by combining parts:

1. A base docker file (a plain Ubuntu with some personalized additions), found under ``base_images``
2. Boilerplate that just sets up the basics of the infrastructure (e.g. VNC), found under ``wrappers``

The composition is done by copying and deploying the first two together in a base image + wrapper
and then use docker building facilities to generate the image. Note that ``Dockerfile``
files are properly generated and merged together.

If you are unable to build your application on Ubuntu-18.04, then please feel free to contribute
additional ``Dockerfile`` scripts to provide other Linux OS bases. However, please note that it is
not necessary to for both Simphony-Remote and the application to be built on the same OS.

Wrappers
~~~~~~~~

Wrappers are a set of files and applications that are used to support
the final application. At the moment we have two types of wrapper:

    - ``vncapp`` : support X11 applications. The wrapper exports them on a
                   running X11 desktop exported to the web via noVNC.
    - ``webapp``: support for web-based applications (e.g. browsepy, jupyter).
                  The wrapper runs the script ``wrappers/webapp.sh``. Individual docker
                  images are supposed to personalise this script to start
                  the appropriate web application.

They are combined (copied) with the ``base_image`` to provide the final Docker
image that is usable for our application needs.

Individual application images must then choose the appropriate base image.
For example, an application relying on VNC to work must use e.g.
``ubuntu-18.04-vncapp`` as base image.

Docker image names
~~~~~~~~~~~~~~~~~~

These produce docker images following the naming convention::

    simphonyproject/ubuntu-<ubuntu-version>-<wrapper>:{version}

Possible examples include:

1. ``simphonyproject/ubuntu-18.04-vncapp``
2. ``simphonyproject/ubuntu-18.04-webapp:0.3.0``

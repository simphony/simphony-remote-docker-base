FROM ubuntu:18.04

MAINTAINER SimPhoNy Team

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root

RUN apt-get update \
    && apt-get install -y --force-yes --no-install-recommends supervisor \
        openssh-server pwgen sudo vim-tiny nano git\
        net-tools \
        lxde x11vnc xvfb \
        gtk2-engines-murrine ttf-ubuntu-font-family \
	wget \
        python-pip python-dev build-essential \
        mesa-utils libgl1-mesa-dri libglu1\
        gettext \
	nginx \
    && apt-get autoclean \
    && apt-get autoremove 

# Do not add --platform=linux/blabla since this is intended for multiplatform builds
# Not using osrf/ros:humble-desktop-full because it's mono-arch and we want multi-arch
FROM tomnotch/ros-base:humble AS base
ENV HOME_FOLDER=/root
WORKDIR $HOME_FOLDER/

# Fix apt-get install stuck problem
ENV DEBIAN_FRONTEND=noninteractive
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

# update all obsolete packages to latest, install sudo, and cleanup
RUN apt-get update -o Acquire::Check-Valid-Until=false -o Acquire::AllowInsecureRepositories=true -o Acquire::AllowDowngradeToInsecureRepositories=true && \
    apt-get full-upgrade -y && \
    apt-get install -y sudo ca-certificates && \
    apt-get autoremove -y && \
    apt-get autoclean -y

RUN apt-get install -y libusb-dev ros-humble-desktop-full ros-humble-tf-transformations ros-humble-joy python3-colcon-common-extensions python-is-python3 python3-pip git

RUN pip install transforms3d pyyaml

# end of sudo apt-get installs
RUN apt-get full-upgrade -y && \
    apt-get autoremove -y && \
    apt-get autoclean -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/*

# Set the default shell to zsh
SHELL [ "/bin/zsh", "-c" ]

# # move fixuid config
# RUN mv $HOME_FOLDER/fixuid-config.yml /etc/fixuid/config.yml

# Entrypoint command
# ENTRYPOINT [ "/bin/sh" , "-c", "fixuid; /bin/zsh" ]
ENTRYPOINT [ "/bin/zsh" ]

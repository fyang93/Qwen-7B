FROM pytorch/pytorch:2.0.1-cuda11.7-cudnn8-devel

ARG USERNAME
ARG USER_UID
ARG USER_GID=$USER_UID

ENV HOME /home/$USERNAME
ENV SHELL /bin/bash

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get upgrade --no-install-recommends -y \
    && apt-get install --no-install-recommends -y sudo curl wget git tmux libglib2.0-0 libsm6 libxrender1 libxext6 libgl1-mesa-dev \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

USER $USERNAME
WORKDIR $HOME
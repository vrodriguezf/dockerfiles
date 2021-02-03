FROM nvidia/cuda:11.0-runtime-ubuntu20.04

USER root

# Ubuntu packages
RUN apt-get update
RUN apt install -y python3
RUN apt install -y python3-pip
RUN python3 -m pip install --upgrade pip
RUN apt-get update
RUN apt-get install -y python3-dev
RUN apt-get install -y git
RUN apt-get update
RUN apt-get -y install curl
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash
RUN apt-get install -y nodejs

# git global configuration
RUN git config --global pull.rebase true
RUN git config --global rebase.autoStash true 

RUN pip install jupyter
RUN pip install jupyterlab
RUN pip install jupyter_contrib_nbextensions
RUN jupyter contrib nbextension install --user
RUN jupyter nbextensions_configurator enable --user
RUN jupyter nbextension enable collapsible_headings/main --user

RUN pip install --upgrade jupyterlab-git
RUN pip install --upgrade jupyterlab-quickopen
RUN jupyter labextension install @parente/jupyterlab-quickopen
# Update to 2.31
RUN jupyter labextension install @aquirdturtle/collapsible_headings
RUN jupyter lab build

# Environmental variables for wandb
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# TODO: remove this
ENV foo=3

# General pip packages
RUN pip install --upgrade twine keyrings.alt pynvml fastgpu

# Add the user settings. These should be copied by child images to the user folders
ADD .jupyter/lab/user-settings /.jupyter/lab/user-settings

EXPOSE 8888
WORKDIR /
CMD ["jupyter","lab","--ip=0.0.0.0","--port=8888","--no-browser","--allow-root","--ContentsManager.allow_hidden=True"]

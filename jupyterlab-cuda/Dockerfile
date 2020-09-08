FROM nvidia/cuda:10.0-cudnn7-runtime-ubuntu18.04

USER root

RUN apt-get update
RUN apt install -y python3
RUN apt install -y python3-pip
RUN pip3 install --upgrade pip
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
RUN jupyter labextension install @aquirdturtle/collapsible_headings
RUN jupyter lab build

#ARG USER_ID=1000
#ARG GROUP_ID=1000

#RUN addgroup --gid $GROUP_ID user
#RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID user
#USER user

WORKDIR /
EXPOSE 8888
CMD ["jupyter","lab","--ip=0.0.0.0","--port=8888","--no-browser","--allow-root","--ContentsManager.allow_hidden=True"]

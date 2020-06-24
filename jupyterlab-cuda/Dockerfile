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

RUN pip install jupyter
RUN pip install jupyterlab
RUN pip install jupyter_contrib_nbextensions
RUN jupyter contrib nbextension install --user
RUN jupyter nbextensions_configurator enable --user
RUN jupyter nbextension enable collapsible_headings/main --user

ARG user_id=1000
|1 user_id=1000 /bin/sh -c useradd -ms /bin/bash user
|1 user_id=1000 /bin/sh -c usermod -u $user_id user
|1 user_id=1000 /bin/sh -c groupmod -g $user_id user
|1 user_id=1000 /bin/sh -c pip install --upgrade jupyterlab-git
|1 user_id=1000 /bin/sh -c pip install --upgrade jupyterlab-quickopen
|1 user_id=1000 /bin/sh -c jupyter labextension install @jupyter-voila/jupyterlab-preview
|1 user_id=1000 /bin/sh -c jupyter labextension install @parente/jupyterlab-quickopen
|1 user_id=1000 /bin/sh -c jupyter labextension install @ijmbarr/jupyterlab_spellchecker
|1 user_id=1000 /bin/sh -c jupyter labextension install @krassowski/jupyterlab_go_to_definition
|1 user_id=1000 /bin/sh -c jupyter labextension install @aquirdturtle/collapsible_headings
|1 user_id=1000 /bin/sh -c jupyter labextension install @ryantam626/jupyterlab_code_formatter
|1 user_id=1000 /bin/sh -c pip install jupyterlab_code_formatter
|1 user_id=1000 /bin/sh -c jupyter serverextension enable --py jupyterlab_code_formatter
|1 user_id=1000 /bin/sh -c jupyter lab build
USER root
WORKDIR /home/user
EXPOSE 8888
CMD ["jupyter" "lab" "--ip=0.0.0.0" "--port=8888" "--no-browser" "--allow-root" "--ContentsManager.allow_hidden=True"]

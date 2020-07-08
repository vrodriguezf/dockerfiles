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

# Install from local requirements.txt located in the same folder as the Dockerfile
COPY ./requirements.txt /
RUN pip install -r /requirements.txt

ARG USER_ID=1000
ARG GROUP_ID=1000

RUN addgroup --gid $GROUP_ID user
RUN adduser --disabled-password --gecos '' --uid $USER_ID --gid $GROUP_ID user

#ARG user_id=1000
#RUN useradd -ms /bin/bash user
#RUN usermod -u $user_id user
#RUN groupmod -g $user_id user
RUN pip install --upgrade jupyterlab-git
RUN pip install --upgrade jupyterlab-quickopen
RUN jupyter labextension install @jupyter-voila/jupyterlab-preview
RUN jupyter labextension install @parente/jupyterlab-quickopen
RUN jupyter labextension install @ijmbarr/jupyterlab_spellchecker
RUN jupyter labextension install @krassowski/jupyterlab_go_to_definition
RUN jupyter labextension install @aquirdturtle/collapsible_headings
RUN jupyter labextension install @ryantam626/jupyterlab_code_formatter
RUN pip install jupyterlab_code_formatter
RUN jupyter serverextension enable --py jupyterlab_code_formatter
RUN jupyter lab build

#USER root
USER user
WORKDIR /home/user
EXPOSE 8888
CMD ["jupyter","lab","--ip=0.0.0.0","--port=8888","--no-browser","--allow-root","--ContentsManager.allow_hidden=True"]

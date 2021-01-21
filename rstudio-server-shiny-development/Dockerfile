FROM rocker/tidyverse:latest

RUN R -e "install.packages(c('shiny', 'reticulate'))"
ARG RETICULATE_MINICONDA_PATH=/usr/local/share/r-miniconda
RUN R -e "reticulate::install_miniconda(path = '${RETICULATE_MINICONDA_PATH}')"
RUN echo "RETICULATE_MINICONDA_PATH=${RETICULATE_MINICONDA_PATH}" >> /${R_HOME}/etc/Renviron.site

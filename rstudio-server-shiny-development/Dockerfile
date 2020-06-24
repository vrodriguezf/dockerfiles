FROM rocker/tidyverse:latest

RUN R -e "install.packages(c('shiny', 'reticulate'))"
RUN R -e "reticulate::install_miniconda()"

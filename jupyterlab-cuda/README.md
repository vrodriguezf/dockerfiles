There are two images:

- `Dockerfile`: builds the image with pip-based dependencies. It can be run without docker-compose
- `Dockerfile-conda`: builds the image with conda-based dependencies. Needs to be run with `docker-compose` in the compose folder

Both files need the folder `.jupyterlab-settings`.

using

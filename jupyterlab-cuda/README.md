There are two images to choose:
- `Dockerfile-pip`: builds the image with full pip-based dependencies. Dependencies must be added to the Dockerfile, not in a separate file.
- `Dockerfile-conda`: builds the image with conda-based dependencies (also allows pip dependencies). Dependencies are added in separate files to the dockerfile, both for `conda` based dependencies (in `compose/environment.yml`) and for `pip` (in `compose/requirements.txt`)

Both files need to be copied into the root of your project, along with the `compose` folder. The `docker-compose.yml` inside the `compose` folder file uses by default `Dockerfile-conda`. If you want to use `Dockerfile-pip`, change the build attributes in that compose file.

Once you have copied the files into your project, go to the compose folder and edit the `.env` file. The variables needed in are listed in the README of the root of this repository. Then, open a terminal in the compose folder and run:
```
docker compose up -d
```

Finally, open a browser and go to `localhost:${JUPYTER_PORT}` to access the jupyterlab server (replace localhost with IP of your server in case you are working remotely).

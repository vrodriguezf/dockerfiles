## jupyterlab-cuda

There are two images to choose:
- `Dockerfile-pip`: builds the image with full pip-based dependencies. Dependencies must be added to the Dockerfile, not in a separate file.
- `Dockerfile-conda`: builds the image with conda-based dependencies (also allows pip dependencies). Dependencies are added in separate files to the dockerfile, both for `conda` based dependencies (in `compose/environment.yml`) and for `pip` (in `compose/requirements.txt`)

Both files need to be copied into the root of your project, along with the `compose` folder. The `docker-compose.yml` inside the `compose` folder file uses by default `Dockerfile-conda`. If you want to use `Dockerfile-pip`, change the build attributes in that compose file.

Once you have copied the files into your project, go to the compose folder and edit the `.env` file with the following configuration.
```
# The name of the docker-compose project
COMPOSE_PROJECT_NAME=your_project_name
# The user ID you are using to run docker-compose
USER_ID=your_numeric_id
# The group ID you are using to run docker-compose (you can get it with id -g in a terminal)
GROUP_ID=your_numeric_id
# The user name assigned to the user id
USER_NAME=your_user_name
# The port from which you want to access Jupyter lab
JUPYTER_PORT=XXXX
# The path to your data files to train/test the models
LOCAL_DATA_PATH=/path/to/your/data
# The W&B entity
WANDB_ENTITY=
# The W&B project
WANDB_PROJECT=
# The W&B personal API key (see https://wandb.ai/authorize)
WANDB_API_KEY=your_wandb_api_key
# List of comma separated GPU indices that will be available in the container (by default only 0, the first one)
CUDA_VISIBLE_DEVICES=0
# Github PAT (see https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and>
GH_TOKEN=your_github_pat
```

> Note: Only `USER_ID`, `GROUP_ID`, `USER_NAME` and `JUPYTER_PORT` are mandatory.

Then, open a terminal in the compose folder and run:
```
docker compose up -d
```

Finally, open a browser and go to `localhost:${JUPYTER_PORT}` to access the jupyterlab server (replace localhost with IP of your server in case you are working remotely).

> Note: This image is meant to be built in a system with at least one GPU.

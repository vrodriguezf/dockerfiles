# dockerfiles
Dockerfiles for my most frequent development environments

To use the jupyterlab container, it is recommended to use the file `docker-compose.yml`, along with an `.env` file with the following configuration
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

Note: This is meant to be deployed in a system with at least one GPU. If your system does not have any, you'll have to change the previous docker-compose command to: docker-compose -f docker-compose-cpu.yml up -d --build


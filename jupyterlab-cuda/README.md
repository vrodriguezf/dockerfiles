There are two images to choose:
- `Dockerfile-pip`: builds the image with pip-based dependencies. 
- `Dockerfile-conda`: builds the image with conda-based dependencies. 

Both files need to be copied into the root of your project, along with the `compose` folder. The `docker-compose.yml` file uses by default `Dockerfile-conda. If you want a full pip-based environment, chang the build attributes in that compose file

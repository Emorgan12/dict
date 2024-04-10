# Pink Dict

A custom themed version of the likes-gay/dict that has been recoloured in pink and orange by Emorgan12

It is quickly deployable in a [Docker contianer](https://ghcr.io/emorgan12/dict)

## About

### Frontend

* Written in TypeScript 
* Compiled using the first job in the [GitHub Action](https://github.com/Emorgan12/dict/blob/main/.github/workflows/compile.yml)

### Backend

* Written in Python
* [FastAPI](https://fastapi.tiangolo.com/) used to run the API and serve static files
* [TinyDB](https://tinydb.readthedocs.io/en/latest/) used to store the words

### GitHub Actions

* Compiles the TypeScript
* Compiles Docker Image
* Pushes to [Docker Hub](https://hub.docker.com/r/likesgay/dict)

## How to run

### Production

The easiest and most secure way to run this is using our [offcial Docker image](https://ghcr.io/emorgan12/dict).

* **Make sure to replace the SECRET_KEY in the command**
* The default port it runs on is 8000. Change the first port to change the host port.
* The volume sets where the database file should be stored, so it persits. This defaults to the directory the command is run in.
* The detach argument runs the container in the background.
* The name argument sets the name

```shell
docker run -e SECRET_KEY="SET_SECRET_KEY_HERE" --publish 5800:8000 --volume $(pwd)/pink-dict-data:/backend/dict-data --detach --restart always --name Pink-Dict ghcr.io/emorgan12/dict
```
The Docker container can automatically be updated to the latest image using [Watchtower](https://containrrr.dev/watchtower/).

### Dev

1. Run `npm run build:dev` in [`frontend`](https://github.com/Emorgan12/dict/tree/main/frontend)
2. Run `uvicorn main:app --reload` in [`backend`](https://github.com/Emorgan12/dict/tree/main/backend)

We also have a [dev branch](https://github.com/Emorgan12/dict/tree/dev).

And [`dev_run.sh`](https://github.com/Emorgan12/dict/blob/main/dev_run.sh) installs all the dependencies and runs those commands.
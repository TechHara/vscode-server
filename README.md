This repo contains a `Dockerfile` from which you can build a container running VSCode-Server. For detailed instruction, refer to [here]()

# Server

## Requirement
- docker
- Github or Microsoft account

## Build image
```bash
docker build -t vscode-sever .
```

## Run
You can choose one of the two options below.

### Option 1
```bash
# directly mount the host's filesystem
docker run --rm -d -v /path/to/dev/folder/on/server:/home/dev/Repo vscode-server code tunnel
```

### Option 2
```bash
# create a docker volume
docker volume create dev
# mount the docker volume
docker run --rm -d -v dev:/home/dev/Repo vscode-server code tunnel
```

## Link account
```bash
# note the container id running vscode-server image
docker container ls
# print out container log and follow instruction to authenticate
docker logs CONTAINER_ID
```

# Client
## Web browser
Visit [vscode.dev](https://vscode.dev) and select `Connect to Tunnels`, authenticate, and select the instance. 

## VSCode app
Install [remote-tunnels](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-server) extension. Connect to the server from `Remote Explorer` tab on the left.
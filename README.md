# MII Kerndatensatz Modul Onkologie

## Profiling

For profiling or local evaluation of the current state the dev containers feature from Visual Studio Code can be used.

Prerequisites:

- WSL 2
- Docker Desktop with WSL 2 backend
- Visual Studio Code
  - Extension: Dev Containers (`ms-vscode-remote.remote-containers`)

If VS Code does not automatically prompt to re-open this project in a dev container, you can do by clicking in the bottom-left corner and select the corresponding entry.

First time opening this solution in a dev container will cause the Docker image to be built. This may take some minutes but will not be needed when opening the container again.

### Tooling

This container comes with FSH Sushi and dependencies pre-installed. Execute sushi from the command line by calling `sushi`.

### IG Publisher

At first, the latest version of the publisher needs to be downloaded. You can either use the script from the repository (`_updatePublisher.sh`) or use the version shipped with the container itself (`../_updatePublisher.sh`).

The IG Publisher is started using the script `_genonce.sh`. This first internally calls sushi and generates the pages using the pre-installed tool _Jekyll_. The generated HTML files are placed in the `output/` folder.

### Website

The HTML files can directly be opened using a browser or by hosting using _nginx_.

A simple way is to use the official Docker image. Start the container from `output/` using the WSL command line. Docker is not available from inside dev containers.

```bash
docker run --rm --name nginx -v $(pwd):/usr/share/nginx/html:ro -p 8080:80 nginx
```

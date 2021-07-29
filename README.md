# Development Container for Building the Intake24 (v3)
## Install & Usage
- Install and configure [Docker](https://www.docker.com/get-started) for your operating system.
- Install [Visual Studio Code](https://code.visualstudio.com/)
- Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).
- Pull this repository
- [Spin-up the Dev container](https://vscode-eastus.azurewebsites.net/docs/remote/containers-tutorial)
- pull the Intake24 deployment [repository](https://github.com/intake24/deployment).
- In case of AWS copy your aws *.pem file to the workspace
- run chmod 600 on the key file
- Follow instruction in Intake24(v3) deployment repository.

## Additional nites: 
- Docker will need to have at least few gigabyte of space available 
- Docker swap at least 2 GB
- Docker Memory - at least 6GB
- for a survey-frontend build need to have at least 4 CPU :(
**(esiest way yo configure is  through Docker Dashboard)**
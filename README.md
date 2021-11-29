# Development Container for Building the Intake24 (v3)
## Installation & Usage

### Building
- Install and configure [Docker](https://www.docker.com/get-started) for your operating system.
- Install [Visual Studio Code](https://code.visualstudio.com/)
- Install the [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack).
- Pull this repository
- Run `cd intake24_v3` from the root of this repository.
- Pull the Intake24 deployment [repository](https://github.com/intake24/deployment) and all other neccessary repositories in `intake24_v3` folder
- [Spin-up the Dev container](https://vscode-eastus.azurewebsites.net/docs/remote/containers-tutorial)
- In the case of AWS copy your aws *.pem file to the workspace
- Run chmod 600 on the key file
- Follow instructions in Intake24(v3) deployment repository.

### Pulling container image
- To be specified
## Remarks: 
### Docker configuration
- Docker will need to have at least few gigabyte of space available 
- Docker swap at least 2 GB
- Docker Memory - at least 6GB
- for a survey-frontend build need to have at least 4 CPU :(
**(esiest way to configure is  through Docker Dashboard)**

### Taking DB snapshots (pg_dump)

- System DB:

**Schema only**
```
sudo -u <OS_USER_WITH_SUDO> pg_dump -U <POSTGRES_USER> --verbose --quote-all-identifiers --schema-only --encoding UTF8 -Fc intake24_system >  path/to/output/folder/intake24_system_schema.pgcustom
``` 
**Data only**
```
sudo -u <OS_USER_WITH_SUDO> pg_dump -U <POSTGRES_USER> --verbose --quote-all-identifiers --data-only --encoding UTF8 -Fc intake24_system > path/to/output/folder/intake24_system_data.pgcustom
```

**Data excluded**.

Excluding data from the deployment specific tables. Use it for DB snapshot distribution or for the deployment of the new instance.
```
sudo -u <OS_USER_WITH_SUDO> pg_dump -U <POSTGRES_USER> --verbose --quote-all-identifiers --data-only --encoding UTF8 -Fc intake24_system --exclude-table-data 'public.user*'  --exclude-table-data 'public.ux*'  --exclude-table-data 'public.tool*'  --exclude-table-data 'public.survey*'  --exclude-table-data 'public.signin_log'  --exclude-table-data 'public.pairwise*'  --exclude-table-data 'public.gen_user_counters'  --exclude-table-data 'public.data*'  --exclude-table-data 'public.client*' > path/to/output/folder/intake24_system_data_excluded.pgcustom
```

- Foods DB

```
sudo -u <OS_USER_WITH_SUDO> pg_dump -U <POSTGRES_USER> --verbose --quote-all-identifiers --encoding UTF8 -Fc intake24_foods > path/to/output/folder/intake24_foods.pgcustom
```
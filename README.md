# Edge-Connector

`Edge-Connector` is a small server running on your local system to provide the following services:
- Ensure that your input data are correctly provided in the KIT format.
- Automate cumbersome interactions with the dataspace for you.

## Getting Started

**python 3.12** is used.

### Build the docker container image

Create the docker image:
```bash
docker build -t edge-connector .
```

### Locate the certificate files

1. Go to [https://vision-x-dataspace.base-x-ecosystem.org/](https://vision-x-dataspace.base-x-ecosystem.org/) and login.
2. Download the certificate files (*tls.crt* and *tls.key* files)
3. Put these files in the directory where this repository is pulled (e.g., where `main.py` is located).

### Modify the .env file

1. Go to [https://vision-x-dataspace.base-x-ecosystem.org/](https://vision-x-dataspace.base-x-ecosystem.org/) and login.
2. Create the connector, if you did not. Remember your connector name.
3. Open the `.env` file in this project folder. Write your *CONNECTOR_NAME*.

### Run the app

```bash
docker run --rm -it \
  -p 8001:8001 \
  -v "$(pwd):/app" \
  edge-connector
```

### Check everything is running

- Access `http://localhost:8001/` to see a welcome message.
- Access `http://localhost:8001/livecheck` to see if the dataspace access is working fine.
    - If not working, follow the DLR dataspace setup in the below section.
    - If not working, follow the T-System dataspace setup in the below section.
- You can also check `http://localhost:8001/docs` for API references.

# Resources

- See the DLR dataspace API documentation at [here](https://docs.adsel.space/home/)
- DLR dataspace UI at [here](https://vision-x-dataspace.base-x-ecosystem.org/)
- Tractus-X EDC API at [here](https://eclipse-tractusx.github.io/tractusx-edc/openapi/control-plane-api/#/)





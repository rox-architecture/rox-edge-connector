# Edge-Connector

`Edge-Connector` is a small server running on your local system to provide the following services:
- Ensure that your input data are correctly provided in the KIT format.
- Automate cumbersome interactions with the dataspace for you.

## Docker setup

For DLR dataspace, get the certificates first before setting up the docker image. 

Create the docker image:
```bash
docker build -t edge-connector .
```

Run:
```bash
docker run --rm -it \
  -p 8001:8001 \
  -v "$(pwd):/app" \
  edge-connector
```

**python 3.12** is used.

### Notes:
- Access `http://localhost:8001/` to see a welcome message.
- Access `http://localhost:8001/livecheck` to see if the dataspace access is working fine.
    - If not working, follow the DLR dataspace setup in the below section.
    - If not working, follow the T-System dataspace setup in the below section.
- You can also check `http://localhost:8001/docs` for API references.

## DLR dataspace

To access DLR dataspace, certificate files are needed.

1. Go to [https://vision-x-dataspace.base-x-ecosystem.org/](https://vision-x-dataspace.base-x-ecosystem.org/) and login.

2. Download the certificate files (*tls.crt* and *tls.key* files) and locate them in the edge-connector root location (e.g., where `main.py` is located).

3. Check that in the `.env` file, *CONNECTOR_NAME* is set correctly with your connector name.

4. Access http://localhost:8001/livecheck to see if you can access DLR dataspace (you should see a token)

## T-System dataspace

# Resources

- See the DLR dataspace API documentation at [here](https://docs.adsel.space/home/)
- DLR dataspace UI at [here](https://vision-x-dataspace.base-x-ecosystem.org/)
- Tractus-X EDC API at [here](https://eclipse-tractusx.github.io/tractusx-edc/openapi/control-plane-api/#/)




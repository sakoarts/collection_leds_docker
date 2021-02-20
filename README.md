# Collection LEDs Docker
Make sure to clone and/or pull this repro including submodules
```
git pull --recurse-submodules
```


## Installation
First install docker and docker compose. For Rasbian:
https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl

## Running
### Building
docker-compose up -d --build
### Removing
docker-compose down -v
### View logs
docker-compose logs -f

## NORA
Request a NORA toke at:
https://node-red-google-home.herokuapp.com/

Go to services/node_red and rename the flows_cred_example.json to flows_cred.json and open it. There replace the string secret after "token" with the key you just obtained from NORA
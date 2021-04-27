# Collection LEDs Docker
This repro is meant as a super-project on my Collection LEDs project which is also a submodule of this project:
https://github.com/sakoarts/collection_leds

The goal of this project is to provide a docker-compose environment to run the Collection LEDs project. It provides the follwing functionalities ontop of said project:
* Running the Flask server via a WSGI webserver instead of the non-production ready native Flask webserver using Gunicorn.
* An Nginx server that runs ontop of said WSGI server and exposes it on port 80
* A Node Red application server equiped with NORA and some prepared flows which allow you to control the led server via Google Home (when NORA credentials are provided)

You are ofcourse free to drop the Nginx and Node Red service and only use this project to host the LEDs Collection application server on port 5000.

Since this project is has a submodele as a core element you will have to clone and/or pull this repro including submodules. Pulling is done as follows:
`git pull --recurse-submodules`

## Settings
After cloning this project including the submodules there are two settings you would want to change. 
* **LED Collection config** This settings file is meant to customize the LED control on your specific setup. This file can be found in services/led_collection/config/settings.json. Further instuctions on chaging these can be found in the README.md of the submodule. 
* **NORA credentials** When you would like to use the google home intergration via NORA you will need to create a NORA account and provide the credentials in flows_cred.json. Futher instuctions can be found in the NORA section. 

## Installation
First install docker and docker-compose. For Raspbian:
https://dev.to/rohansawant/installing-docker-and-docker-compose-on-the-raspberry-pi-in-5-simple-steps-3mgl

## Running
### Building
`docker-compose up -d --build`
### Removing
`docker-compose down -v`
### View logs
`docker-compose logs -f`

## Smart NORA
As mentioned, NORA is module for the Node Red home automation flow editor that allows for intergration with Google Home. When launching this docker-compose with a NORA token as instucted below, a node red instance will be running with some basic flows. These will already enable you to control some of the animations, basic colors and picker control via google home. The Node Red flow editor can be reached on port 1880 via the IP address of the device you are running the dockers on. When you change the flows and would like to keep them on a new docker deployment. Simply use the Node Red UI to export all the flows and replace the flows.json file in the services/node_red with your newly exported file. 

### Obtaining and providing token
Request a NORA token at:
https://smart-nora.eu/

Go to services/node_red, rename the flows_cred_example.json to flows_cred.json and open it. There replace the email and password values with the credentials of the account you just created.

netatmo-api-python, recurring image capture & timelapser
========================================================
Built with help from the [netatmo-api-python](https://github.com/philippelt/netatmo-api-python) repo

### Authentication ###

Make sure to create an accessible app from [Netamo's own developer platform](https://dev.netatmo.com/apps/createanapp), to receieve a clientId, and clientSecret to access their API. Fill in the necessary information in the lnetamo.py file.


### Usecase ###

* Add client_id, client_secret, username and password of your Netamo account to the environment variables
* If running the docker file in terminal make sure to run it with the following command 

      docker run -e CLIENT_ID={$ client_id} -e CLIENT_SECRET={$ client_secret} -e USERNAME={$ username} -e PASSWORD={$ password} -e  SLEEPTIME={$ amount of seconds interval} -t -v {$ absolute path for pictures}:/pictures tordar/timelapser

* Including `:/pictures` at the end of the absolute path is crucial to allow Docker to mount a volume outside of itself 

* If running this in a seperate docker container, [pull the image](https://hub.docker.com/r/tordar/timelapser) from Docker Hub with following command:

      docker pull tordar/timelapser
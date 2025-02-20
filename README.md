netatmo-api-python, recurring image capture & timelapser
========================================================
This repo was built and forked, based on the [netatmo-api-python](https://github.com/philippelt/netatmo-api-python) repo

### Authentication ###

Make sure to create an accessible app from [Netamo's own developer platform](https://dev.netatmo.com/apps/createanapp), to receieve a clientId, and clientSecret to access their API. Fill in the necessary information in the lnetamo.py file.


### Usecase ###

* Add client_id, client_secret, camera name, sleeptime, username and password of your Netamo account to the environment variables
* If running the docker file in terminal make sure to run it with the following command 

      docker run -e CLIENT_ID={$ client_id} -e CLIENT_SECRET={$ client_secret} -e MY_CAMERA={$ netatmo camera} -e USERNAME={$ username} -e PASSWORD={$ password} -e  SLEEPTIME={$ amount of seconds interval} -t -v {$ absolute path for pictures}:/pictures tordar/timelapser

* Including `:/pictures` at the end of the absolute path is crucial to allow Docker to mount a volume outside of itself 

* If running this in a seperate docker container, [pull the image](https://hub.docker.com/r/tordar/timelapser) from Docker Hub with following command:

      docker pull tordar/timelapser

### Update 23.01.2023 ###

* Trying to update the image on Docker Hub, there was an issue when trying to run the container on different platform than where it was created (Built on Arm, attempted to run on AMD). The solution for this was to build a [multiplatform image](https://docs.docker.com/build/building/multi-platform/).
# MQTT Broker Commands
 
We'll need to create the docker container with the instruction below. If the ```eclipse-mosquitto``` image is not present in your docker system, this instruction will install the image onto the device.
```
docker run -d --restart unless-stopped -p 1883:1883 -p 9001:9001 -v mosquitto:/mosquitto eclipse-mosquitto
```


```docker run```: The standard run command for creating and running docker containers.

```-d```: Detached mode, which allows for you to run the container without running on the terminal. The alternative to this would be the interactive flag ```-it```. 

```--restart unless-stopped``` allows the container to run automatically on boot up unless the user has stopped the container before power cycle.

```-p```: Port flag, which tells the container to run on a specific port within the local host. This example has the container pointing to multiple ports. An alternative would be allowing the container to decide the port using ```--network=host```. (More info here: https://docs.docker.com/network/host/)

```-v```: The volume flag, which houses the location of persistent data tied to the container. In this case, we call the volume ```mosquitto```, which is an alias that points to the containers internal file structure...also called ```mosquitto```.

Once we've entered the run command, check to see if the container is running with ```docker ps -a```. This commmand will give you a list of all containers within the device (whether running or not) as well as the status on the container.

If you need to view just the running containers on the system, then use ```docker container ls```.

Once the container has been created, we can view the volumes and see the ```mosquitto``` file has been created. Going into the ```/_data``` directory, you'll also be able to see the ```config```, ```data```, and ```log``` directories.

```cd /home/docker/volumes/mosquitto/_data/```


```ls```
 
![image](https://user-images.githubusercontent.com/42245728/227012865-4a77abac-13e6-45b3-9a62-57cb18ac9ab5.png)


 

# Command line Explanations
 
We'll need to create the docker container with the instruction below. If the 'eclipse-mosquitto' image is not present in your docker system, this instruction will install the image onto the device.
```
docker run -d -p 1883:1883 -p 9001:9001 -v mosquitto:/mosquitto eclipse-mosquitto
```


```docker run```: The standard run command for creating and running docker containers.

```-d```: Detached mode, which allows for you to run the container without having the terminal 

docker exec –it <container> /bin/sh

cd mosquitto/config

ls

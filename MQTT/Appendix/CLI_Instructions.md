# MQTT Broker Commands
 
We'll need to create the docker container with the instruction below. If the ```eclipse-mosquitto``` image is not present in your docker system, this instruction will install the image onto the device.
```
docker run -d -p 1883:1883 --restart=unless-stopped  -v mosquitto:/mosquitto  eclipse-mosquitto:1.5

```


```docker run```: The standard run command for creating and running docker containers.

```-d```: Detached mode, which allows for you to run the container without running on the terminal. The alternative to this would be the interactive flag ```-it```. 

```--restart unless-stopped``` allows the container to run automatically on boot up unless the user has stopped the container before power cycle.

```-p```: Port flag, which tells the container to run on a specific port within the local host. An alternative would be allowing the container to decide the port using ```--network=host```. (More info here: https://docs.docker.com/network/host/)

```-v```: The volume flag, which houses the location of persistent data tied to the container.

Once we've entered the run command, check to see if the container is running with ```docker ps -a```. This commmand will give you a list of all containers within the device (whether running or not) as well as the status on the container.

If you need to view just the running containers on the system, then use ```docker container ls```.

Once the container has been created, we can view the volumes and see the ```mosquitto``` file has been created. Going into the ```/_data``` directory, you'll also be able to see the ```config```, ```data```, and ```log``` directories.

```cd /home/docker/volumes/mosquitto/_data/```


```ls```
 
![image](https://user-images.githubusercontent.com/42245728/227012865-4a77abac-13e6-45b3-9a62-57cb18ac9ab5.png)

# Encryption
## Changing to encrypted port
 When encrypting the MQTT message, you must use the secure port 8883 for communication. This is done by establishing the secure port in the run command as well as changing the default port in the config file within the volume.
 
```
 docker run -d -p 8883:8883 --restart=unless-stopped  -v mosquitto:/mosquitto  eclipse-mosquitto:1.5
```
Access the mosquitto.conf file, which houses all broker settings and set the default port to port 8883. Use the following command to access and edit the conf file:

```
nano /home/docker/volumes/mosquitto/_data/config/mosquitto.conf
```

Under ```Default Listener``` change the instruction from ```#port 1883``` to ```port 8883```. Using ```ctrl-x``` to exit the nano editor, press ```y``` to save the changes to the file.

![image](https://user-images.githubusercontent.com/42245728/228904171-00d4b4df-b28a-49a1-9932-c2b266a9a41c.png)

Then restart the container with:
```
docker restart <container_ID>
```
## Creating and using certificates

In order to create certficates we'll use the openssl command which will create the keys and certs within the root directory. Once the credentials are created, we must store them within the mosquitto volume and reference their location in the ```mosquitto.conf``` file.

To create the credentials use the following commands:

```
openssl genrsa -des3 -out ca.key 2048
````
```
openssl req -new -x509 -days 1826 -key ca.key -out ca.crt
```
```
openssl genrsa -out server.key 2048
```
```
openssl req -new -out server.csr -key server.key
```
```
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -CAcreateserial -out server.crt -days 360
```

You'll note that there are several new credential files in your root directory. The ones that we will route to the broker are the ```ca.crt server.key server.crt``` files. In order to push those files into the mosquitto broker we'll use the follow docker copy commands:

```
docker cp ca.crt <container_ID>:/mosquitto/
```
```
docker cp server.key <container_ID>:/mosquitto/
```
```
docker cp server.crt <container_ID>:/mosquitto/
```

Change the ```mosquitto.conf```  in the ```Certificated based SSL/TLS support```

![image](https://user-images.githubusercontent.com/42245728/229165929-64137313-146a-4c14-bbff-baaa968e41d8.png)

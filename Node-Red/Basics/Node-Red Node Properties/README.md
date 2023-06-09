# Node-Red Node message properties

When discussing the message properties of a node in Node-Red, there are three main aspects to be aware of: The Payload, the Node-ID, and the Topic. All of these properties are part of the message output of the node itself. As a result, they are referanced as ```msg.payload```, ```msg.topic```, and ```msg._msgid```.

The full timestamp node output with a topic I named ```Time``` is as follows:

![image](https://user-images.githubusercontent.com/42245728/236523948-69c3b137-72a6-4c08-9de0-be619081f009.png)


## msg.payload

The ```msg.payload``` property is the main output of the node that other downstream nodes deal with. The payload can be nearly any datatype and carry multiple structured values.

### Simple payload

![image](https://user-images.githubusercontent.com/42245728/236526112-667540ab-2abc-46dc-8214-df23e50f70b8.png)


![image](https://user-images.githubusercontent.com/42245728/236526076-43d758e3-9e71-4463-bfcf-5db46538e13c.png)


### Complex payload

![image](https://user-images.githubusercontent.com/42245728/236526176-496e1dd0-24b0-4aec-ae3b-c89f8096a26a.png)

![image](https://user-images.githubusercontent.com/42245728/236525895-1adf874b-8194-48ca-a2aa-eb45574ee770.png)

Note: Don't Worry about functions yet!

## msg.topic

The ```msg.topic``` property is used as the an identifier to establish the source of the message. It's also a good way to increase the debugging capability of Node-Red. 

![image](https://user-images.githubusercontent.com/42245728/236540168-00456950-7875-497c-99c5-5f0cbad00911.png)

![image](https://user-images.githubusercontent.com/42245728/236540096-c8e83e61-48db-47f0-bb51-1c503c37bd71.png)

Depending on how you write your code, you can use the topic within your logic.

![image](https://user-images.githubusercontent.com/42245728/236540891-b747bdee-f00b-4278-a842-215f6cf854af.png)

![image](https://user-images.githubusercontent.com/42245728/236540966-9f37ed41-9636-4676-95a0-138977ab1569.png)

## msg._msgid

The ```msg._msgid``` is the unique ID from the **STARTING** Node. The below example shows the ```_msgid```  across several nodes with the same starting node, all showing the same ID.

![image](https://user-images.githubusercontent.com/42245728/236533736-95dc9bc4-f4f3-4751-98f3-1e8947a6cd29.png)

![image](https://user-images.githubusercontent.com/42245728/236533816-484e7a6a-5551-460e-bb52-c02732403ff2.png)




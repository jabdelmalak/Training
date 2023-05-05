# Standard Nodes

Here we will discuss the functionality of several common place nodes within Node-Red.

## Switch Node

The Switch Node is similar to the standard switch statement in programming. The operating ideas is that you can set 
multiple inputs for the switch node. Then depending on the specific input, you can trigger the switch nodes output and pass that input.

![image](https://user-images.githubusercontent.com/42245728/236550025-e3815ae1-5af7-4a9b-a6d8-0d81d56dba88.png)



Within the switch node, you can set input conditions corresponding to the number output.

![image](https://user-images.githubusercontent.com/42245728/236549393-955ec805-4eff-44dc-b7fd-599da67a9866.png)


Here, we see that I've set output 1 to pass the argument only when the input is equal to ```first```. I've done the same for output 2 and 3 being linked to strings ```second``` and ```third``` respectively. If the input of the switch node is none of these conditions, then the input will be transferred to output 4.

![image](https://user-images.githubusercontent.com/42245728/236550183-13d78c8c-a72f-4250-a5d9-ec19117103fe.png)


## Change

In order of us to fully discuss the ```change``` node accurately, we'll need to discuss what a ```context``` is in Node-Red. For now, let's just say that the ```change``` node allows you to set, delete, move, or change variables. 

### Set
For instance, when receiving any input, you can publish a hardcoded string message.

![image](https://user-images.githubusercontent.com/42245728/236551862-c815fe50-b626-4aa5-a965-a5e4ce58d0da.png)

![image](https://user-images.githubusercontent.com/42245728/236551922-dafeae56-5f7b-402b-bb17-d67df8247c56.png)

![image](https://user-images.githubusercontent.com/42245728/236552162-96b76578-a476-4dcd-9bae-8ba317b849e8.png)

### Change

The change setting within the change node (I know, confusing), can convert a specific variable to your variable of choice. Here I decided to set up a change node to look for the ```Joe``` input string and replace with ```Handsome Joe```. If the node doesn't find the variable, then it simply passes the input through.

![image](https://user-images.githubusercontent.com/42245728/236553196-f0967199-0622-4410-9f21-ea79aa48c6d9.png)

![image](https://user-images.githubusercontent.com/42245728/236553252-84eba0c7-cbd2-4da9-93d5-9586496d9639.png)

![image](https://user-images.githubusercontent.com/42245728/236553314-b8832d2a-2532-4e18-a9e2-021ef6b0c08c.png)

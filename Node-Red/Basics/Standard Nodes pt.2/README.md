# Standard Nodes pt.2
A Continuation of examining some of the standard nodes within Node-Red

## Range
The range function is used to scale the incoming message scale to an outgoing message scale. 
This function will only work with numbers.

![image](https://github.com/jabdelmalak/Training/assets/42245728/55376096-53c9-4541-af5d-da4f8e7fb54b)

Within the ```range``` function, there are 3 actions that are possible. Scaling the message, Scaling and limiting the output, and
scaling and wrapping the output.

![image](https://github.com/jabdelmalak/Training/assets/42245728/4d25337e-acb8-466d-9dc3-02fac1abb81a)

With an input range of 0-100, these are the following outputs for each action respectively.

![image](https://github.com/jabdelmalak/Training/assets/42245728/235781f8-2b82-46a0-bf65-fb3cca0b7f5b)


You can see that the ```limit``` action treats a higher value than the input as the maximum of the scale. While for
the ```wrap``` action goes back to zero and rescales based on the input difference.

## Template Node


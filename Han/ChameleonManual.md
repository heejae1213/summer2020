# How to use Chameleon

This step-by-step instruction will guide you on how to use Chameleon.\
This document covers from creating Chameleon account to logging into Chameleon using Floating IP allocated to your instance.\
It also includes a number of screenshots to help you get on Chameleon as easy and fast as possible.\
For more detailed information, you can refer to https://chameleoncloud.readthedocs.io/. <br/>
If you would like to know how to use Chameleon with docker images, refer to https://github.com/sagecontinuum/chameleon-client/.

## Getting started

Go to [ChameleonHome]https://www.chameleoncloud.org/ and sign up. Then, ask PI to get you added on the proper project.\
If you are added to the project, you will be able to access the Chameleon Dashboard. <br/>
Clicking ```CHI@UC``` or ```CHI@TACC``` will lead you to the Dashboard.<br/>

<p align="center">
<img src="images/dashboard.png" width="600" height="300" title="dashboard">
</p>

Go to the Dashboard and either Create a key pair or Import your SSH public key.\
If you have already generated your own SSH key pair, your public key could be found in ```~/.ssh/id_rsa.pub```. 
<br/>

<p align="center">
<img src="images/sshkey.png" title="sshkey">
</p>

This key pair will be used when you attempt to run your docker image on Chameleon directly by using CLI.\
For more info on docker and Chameleon, please refer to https://github.com/sagecontinuum/chameleon-client/. \
Otherwise, for native use of Chameleon, follow the instruction below.

## Create an instance

### Reserve a Node <br/>
Go to the Dashboard again and click *Lease* under *Reservation* from the sidebar. <br/>
Click on *Create Lease* then the wizard will be loaded. <br/>

<p align="center">
<img src="images/reserveNode.png" title="reserveNode">
</p>

<br/>Name your lease and decide the lease length. Maximum lease length is 7 days. <br/>

<p align="center">
<img src="images/reserveNode2.png" width="500" height="500" title="reserveNode2">
</p>

<br/>
Then find *Resource Properties* section and choose proper property for your use. <br/>
For AI/ML related uses, you might want to choose *node_type* = *gpu_rtx_6000*. <br/>
Lastly, indicate the number of Floating IP addresses needed for your use. <br/>

<p align="center">
<img src="images/reserveNode3.png" width="500" height="500" title="reserveNode3">
</p>

### Launch an Instance <br/>
Once your reservation gets ACTIVE, launch a bare-metal instance on the node you have reserved. \
Click *instances* under *Compute* from the sidebar, and click *Launch Instance*, then the wizard will be loaded. <br/>

<p align="center">
<img src="images/instanceLaunch.png" title="instanceLaunch">
</p>

<br/>
Name your instance and associate it with your node (reservation). <br/>

<p align="center">
<img src="images/instanceNode.png" width="500" height="500" title="instanceNode">
</p>


Then click *Source* in sidebar and choose OS image. If you want an image with CUDA installed, search for it. <br/>
For AI/ML related uses, ```CC-Ubuntu18.04-CUDA10``` is highly recommended. <br/>

<p align="center">
<img src="images/instanceImage.png" width="500" height="500" title="instanceImage">
</p>

<br/>

<p align="center">
<img src="images/instanceImage2.png" width="500" height="500" title="instanceImage2">
</p>

<br/>
Then, click *Flavor* from the sidebar and check if it is correctly selected as *baremetal* flavor.<br/>

<p align="center">
<img src="images/instanceFlavor.png" width="500" height="500" title="instanceFlavor">
</p>

<br/>
Then, click *Key Pair* from the sidebar and either Create a Pair or Import a Pair. <br/>
In my case, I just allocated the key the I have registered previously. <br/>

<p align="center">
<img src="images/instancekey.png" width="500" height="500" title="instancekey">
</p>

<br/>
If you have come so far, you now have basic configuration for your instance! <br/>
Press *Lauch Instance* button on the bottom. 

### Associate Floating IP addresses <br/>
Now you will be able to see your instance created as below.
![instanceCreated](images/instanceCreated.png)
Next step you have to take is associating *Floating IP addresses* with your instance.
Click *Floating IPs* under *Network* from the sidebar. Then you will see an IP address not associated with any other instances. Click the *Associate* button to allocate that IP address to your instance.
![IpAssociate](images/IpAssociate.png)
Then the wizard will be loaded. Select your instance port for *Port to be associated*.
![IpAssociate2](images/IpAssociate2.png)
Now if you go back to *instances* under *Compute* again, you will see your instance created there with the Floating IP you have allocated. <br/><br/>
<img src="images/sshLogin.png" width="500" height="300" title="sshLogin">


## Accessing your instance <br/>
Once your instance has launched with an associated Floating IP address. <br/>
You can log in to your Chameleon instance via SSH using the **cc user account and your floating IP address**. <br/>
If your floating IP address was 192.5.87.31, you should use the command: ```ssh cc@192.5.87.31```. <br/>


<img style="max-width: 100px; height: auto; " src="images/sshLogin.png" title="sshLogin"/>

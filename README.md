This repository contains instructions for doing some common commands, configurations and guides for Phoenix Contact related items. These are referenced by other READMEs in different repositories.

# Windows
With Windows and the fact that changes are made often with different releases, I will try and provide steps that will work on multiple releases with the least number of steps.
## Changing IP Address
Changing the IP address on a Windows computer is a common requirement for connecting to PLCs and other devices.
### Determining IP Address to change your PC to
Again, there are multiple solutions to this but I will provide the most common way this is achieved. If you know someone that knows the network, or how to connect to the PLC, ask them "What should I make my IP address on my computer" or "What IP address is free that I can change my PC to?". This is usually the quickest way.

A couple of things with this. We hit a bit of a paradox: you can only connect to the PLC when your PC has an IP address on the network but you can't have two IP addresses the same on the same network. This is where the above step is much easier for finding an IP address. If that is not going to work, sometimes it is trial and error, 
sometimes there is only a couple of devices that are potential conflicts.

I am assuming, like most, that the network has a subnet of `255.255.255.0` - it is a pretty good assumption if you are unsure. (If it is not this, you probably know how to set up your PC already and you aren't reading this).

If the PLC (device) is 192.168.1.10 and that is the only device plugged into your the ethernet port of the PC, then it is simple, you can change your IP address to be 192.168.1.11 or any number between 192.168.1.1 to 192.168.1.254 __but not 192.168.1.10__. (You will also likely not need to worry about a default gateway, if you do, you probably are not reading this. But if for some reason you do, it is the address of the device that can connect you to other networks or commonly - the internet.)
### Configuring your PC settings
1. Press WIN-R to bring up the _Run_ Window. Alternativaly you can search for _Run_ in the start menu.

![Windows Run](https://github.com/user-attachments/assets/acc73218-2f87-4992-bd30-809487185ed0)

2. Type in `ncpa.cpl` and press _OK_

![image](https://github.com/user-attachments/assets/4c8cb07c-1023-4a8b-b0fa-bc75c275c2ed)

3. You will see multiple adapters as shown above. You can plug and unplug the device (PLC) from your PC to determine which one is correct
4. Right click on the adapter you want to change and press _Properties_.
5. Double click on _Internet Protocol Version 4 (TCP/IPv4)_

![image](https://github.com/user-attachments/assets/9d3a5c20-24c4-4f41-b7c6-b65361724fda)

6. Change the address accordingly

![image](https://github.com/user-attachments/assets/135ab923-0d8c-4568-b571-57561278d3f7)

### Confirm connection to PLC
1. Open up command prompt by entering `cmd` into your start menu
2. type in `ping <ip-address>`. Going off the example above it would be `ping 192.168.1.10`.

![image](https://github.com/user-attachments/assets/c2b5424c-5860-46af-8f37-b2738765bf6b)

If you don't get a response, like shown below, 

![image](https://github.com/user-attachments/assets/b7d2d0da-b6a9-4812-9e12-7016660567a9)

1. Check the cable is connected properly,
2. Check you have typed in the correct IP address for the PLC
3. Type in `ipconfig` into command prompt (and press enter). Check that you can see the configuration you entered. Commonly, if you can't see this, it is because the pop-up windows are not closed to prompt the PC to 'save' the configuration. _Note: there will likely be mutliple, so double check the configuration you look at matches the adapter you changed._

![image](https://github.com/user-attachments/assets/6ceda48d-e55c-4107-8318-9fade3c4cad7)

If something wasn't correct, retry the `ping` command as before. (You can press the up-arrow as needed to save you retyping it.)

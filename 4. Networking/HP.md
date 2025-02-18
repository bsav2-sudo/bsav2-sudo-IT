# 4. Networking - HP ProCurve Hardware

![Logo - need to edit](https://github.com/user-attachments/assets/f630c5bf-169d-4b5c-b841-fa4162da1fc6)

### Skills Utilised

<code>HP Procurve Hardware</code> <code>Networking</code> <code>CLI Tools</code> <code>Switch Configuration</code> <code>PuTTY</code> <code>Switch Management</code>

## Overview

For a while in starting my job as an IT Technician - my first significant interest was in the world on Networking and how everything on such as large fabric talks to each other and also talks to the wider internet - this led me to complete my CCST and introduce new subject areas of interest such as Cybersecurity. There was only one problem with doing my CCST, every switch management task I did was through Packet Tracer and not on a switch. While this isn't a bad thing the one thing I love is being able to get hands on with equipment and try every little thing I can with it. So when there was an unused switch that was due to be scrapped - I took the oppourtunity to ask if it was okay with me to wipe and use as a homelab - and my work said of course! So this is where this blog comes in...

In this blog, I want to look at the process and also the management of a switch by actually getting hands on with a <code>HP ProCurve Switch</code> and start to get to grips with some key commands for the HP hardware. Now obviously Cisco is the dominant force in Networking Equipment so maybe in the future I might have to invest in a small Cisco Switch to experience the management on one of those - but hey, this is a really good starting place. So without further ado - lets get started!

## Blog Entry - 11/02/25

## HP Procurve - Collecting the Tools

Before I can even think about getting the switch and plugging into it - there's two bits of equipment I'm going to need to be able to access it. Now beacause the switch has been fully reset - I am going to have a guess and say that the web management feature is going to be **disabled** so I'm going to need to access the switch by its console port. Now the switch I'm using is the one just below:

![Switch](https://github.com/user-attachments/assets/4afe5896-fd8c-458f-b44b-45327caeb138)

Now the console port on this switch is an RJ45 connection so I need to get myself a cable to go from USB C (seeing as though my laptop has three of them!) to RJ45 with the RS-232 chip inside of it - this will allow me to successfuly connect to the switch as the RS-232 allows the communication between the laptop and the switch. A quick shop to Amazon and I pick up one of these cables which are actually a good price and always a good thing to have in my toolkit incase I need to access the CLI of a switch:

![71Wv6uQa1lL _SX522_](https://github.com/user-attachments/assets/8445522d-8fa2-4877-9850-6254bb68e9a3)

Cool, the last piece I need is PuTTY. PuTTY will allow me to open a session with the switch and enable the communication over the serial cable - really nice tool and easy to use so let me get it downloaded.

And now I have it downloaded its time to connect to the switch and get started.

## Basic Commands

To start the session with the switch - the first thing I do is open PuTTY and connect to the switch via the serial port which my cable is connected to (for me this is COM3). Pressing enter on the screen gets us into the switch and...

<img width="1439" alt="Putty Session - Open" src="https://github.com/user-attachments/assets/577d05df-40c9-453e-8586-c95fcb108197" />

There we go we now have our laptop connected to the switch and we can see I have a ProCurve 2610-24. Awesome - now it is time to get into the tasty bit and start running some commands.

Firstly, I want to know more about this switch - for me currently it is just a plain switch that has been handed to me - so let me find out some information about it.

### SHOW

As the name suggests - SHOW looks at information from the switch such as device information and configurations - so lets start issuing some show commands to see what information I can get.

<img width="1434" alt="SHOW - config " src="https://github.com/user-attachments/assets/4652a335-741f-45fe-bde9-388bbedeaa41" />

> <code>show config</code> - shows the running configuration on the switch.

<img width="1438" alt="SHOW - flash" src="https://github.com/user-attachments/assets/77a6d558-2fbb-43a5-b386-6c4d81a45b9c" />

> <code>show flash</code> - shows the current firmware version running on the switch.

<img width="477" alt="SHOW - int custom" src="https://github.com/user-attachments/assets/b486ee71-c3e4-4591-9dd6-b929c88a8b6d" />

> <code>show int custom</code> - shows port information such as Rx and Tx statistics as well as Link status and Name of port.

<img width="1439" alt="SHOW - interface" src="https://github.com/user-attachments/assets/913c98ee-d159-4b33-b3d3-68f96ad0ed07" />

> <code>show interface</code> - shows port statuses and counters for ports (Tx and Rx Packet statistics).

<img width="1439" alt="SHOW  rate-limit all" src="https://github.com/user-attachments/assets/91ec1006-d822-4ab0-9b31-702506b89137" />

> <code>show rate-limit all</code> - shows if there is any rate limiting applied to a port and if there is any override in place for said port (good to know as part of being able to load balance).

<img width="632" alt="SHOW - system information" src="https://github.com/user-attachments/assets/24d70772-3246-4323-894c-18fcb13b947b" />

> <code>show system information</code> - shows information about the switch such as MAC Address, Up Time, Memory free and more.

Cool - that's all the show commands I want to show (no pun intended I promise) - so now lets look at some useful commands that can be used for the switch.

### USEFUL

These commands are some of the useful ones that I have found when doing my lab - they look mostly at the management of the switch such as setting passwords and enabling services such as web management and SSH/Telnet. Down below are the commands:

<img width="625" alt="CONFIG" src="https://github.com/user-attachments/assets/83e0902d-bd36-4fcf-92d5-eec92001247e" />

> <code>conf</code> - puts the CLI into configuration mode.

<img width="1439" alt="LOG - Most Recent Events" src="https://github.com/user-attachments/assets/f9ac4886-0e79-450b-aa73-d1c48bb6bd86" />

> <code>log</code> - shows the most recent logs from the switch.

<img width="1436" alt="NO - web management" src="https://github.com/user-attachments/assets/60ceaee4-7d95-427c-9611-093696c1940e" />

> <code>no telnet-server / web-management</code> - disables web management and/or telnet services for the switch - to re-enable it is a case of typing the service in conf to open it again.

<img width="1439" alt="IP - enable ssh" src="https://github.com/user-attachments/assets/e8394480-3a30-44f1-9a5a-c035b6c7bbf3" />

> <code>ip ssh</code> - enables SSH service on the switch - to disable command would be <code>no ip ssh</code>.

<img width="1191" alt="SET - manager password" src="https://github.com/user-attachments/assets/6e0892c5-9d5f-4783-9469-05256fd2bdbb" />

> <code>set password manager</code> - sets the password for manager - replacing manager with operator will set a password for operator - used when logging into switch.

### Vlan's

The last bit of the lab for today I want to do is VLAN's - seeing as though they are a major part in making network more organised and logically group devices on the Ethernet Layer (Layer 2 on the OSI model), I want to see how I can create a VLAN and also "tag" it to some ports - this is where the HP Procurves differ from the Cisco switches as the naming for putting VLAN's on a port on a HP switch is called "tagging" and "untagging" where as Cisco calls it "add" - wish they could be the same but hey ho. Lets get started.

<img width="1439" alt="VLAN - show" src="https://github.com/user-attachments/assets/bc0c135f-06f7-4fc8-9e47-91f49ce209ec" />

> <code>show vlan</code> - currently shows what VLAN's are on the switch - as you can see there is only one which is the default VLAN.

Now that I can see what VLAN's are already on the switch its time to make one and add it to some ports - below is a screenshot of how I made a new VLAN and added it to some ports.

<img width="1151" alt="VLAN - creation process" src="https://github.com/user-attachments/assets/8a64187f-f401-44ad-bd3c-26af303e9ff3" />

The process for creating it goes like this:

1. Enter into config mode (already did this but didn't realise until error came up!)
2. Create a new VLAN with an ID number
3. Name the VLAN
4. Tag the VLAN to Port 1
5. Untag the VLAN to Port Ranges 10-20
6. Exit the VLAN configuration
7. Exit the Configuration Mode
8. Run the Show VLAN command to see that the process has worked correctly - which it has!

Obviously the tagging and untagging of ports can come later on but it's good to see it in action

<img width="1085" alt="VLAN - info about VLAN" src="https://github.com/user-attachments/assets/9a034f48-d9a4-48b5-9cc0-df1ff928c12e" />

From the screenshot above as well I can see information about VLAN 23 and see that it is tagged to Port 1 and Untagged on Ports 10-20, amazing - that's all for today - I want to make sure what I have learnt today has been retained so will be worth going over the commands again to refresh!

## Blog Entry - 12/02/25

Okay time to refresh the commands I learnt yesterday - one of the ones I forgot to mention was the locate light which can be enabled on the switch - the command <code>chassislocate blink *</code> will flash the locate button on the switch for however many minutes specified (using the * as the argument). Nice handy feature in case I need to show someone which switch to be looking at.

Now to refresh these commands - I'm going to run them and provide the screenshots to show if I remembered them correctly or not...

<img width="817" alt="SHOW - port information" src="https://github.com/user-attachments/assets/35f87db2-7870-4e7b-8245-289c0ddbb44f" />

> <code>Showing the Port Information for Port 5</code>

<img width="848" alt="Test - Assigning VLAN" src="https://github.com/user-attachments/assets/8a278e2a-5026-47e8-98ad-fe5d21e40073" />

> <code>Making a new VLAN and tagging it to a Port</code>

<img width="1334" alt="Test - Delete VLAN" src="https://github.com/user-attachments/assets/f3c79cb8-042a-4da0-ab4b-fbf6a30fd855" />

> <code>Deleting a VLAN</code>

<img width="1439" alt="Test - Management Methods" src="https://github.com/user-attachments/assets/507ed3c6-2da5-4299-8545-a3cef22763c0" />

> <code>Managing the services running on the switch</code>

Awesome I remembered them - obviosuly I'm going to need to keep practicing them but in time it should come to mind fairly easily - in the next blog I hope to start looking at some more commands for the switch looking more into the features. Thnaks for reading and see you on the next one!

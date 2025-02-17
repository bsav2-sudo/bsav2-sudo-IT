# 4. Networking - HP ProCurve Hardware

![Logo - need to edit](https://github.com/user-attachments/assets/f630c5bf-169d-4b5c-b841-fa4162da1fc6)

### Skills Utilised

<code>HP Procurve Hardware</code> <code>Networking</code> <code>CLI Tools</code> <code>Switch Configuration</code> <code>PuTTY</code> <code>Switch Management</code>

## Overview

For a while in starting my job as an IT Technician - my first significant interest was in the world on Networking and how everything on such as large fabric talks to each other and also talks to the wider internet - this led me to complete my CCST and introduce new subject areas of interest such as Cybersecurity. There was only one problem with doing my CCST, every switch management task I did was through Packet Tracer and not on a switch. While this isn't a bad thing the one thing I love is being able to get hands on with equipment and try every little thing I can with it. So when there was an unused switch that was due to be scrapped - I took the oppourtunity to ask if it was okay with me to wipe and use as a homelab - and my work said of course! So this is where this blog comes in...

In this blog, I want to look at the process and also the management of a switch by actually getting hands on with a <code>HP ProCurve Switch</code> and start to get to grips with some key commands for the HP hardware. Now obviously Cisco is the dominant force in Networking Equipment so maybe in the future I might have to invest in a small Cisco Switch to experience the management on one of those - but hey, this is a really good starting place. So without further ado - lets get started!

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

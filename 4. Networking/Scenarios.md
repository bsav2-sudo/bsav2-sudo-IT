# 4. Networking - Scenarios

![bigstock-Man-connecting-network-cables-32461088](https://github.com/user-attachments/assets/758e3f9e-ef65-4b8e-9b26-b7ecdc2c3ead)


### Skills Utilised

<code>Troubleshooting</code> <code>Networking</code> <code>Real Life Scenarios</code> <code>Buisness Needs</code> <code>SLA and Agreements</code> <code>Network Troubleshooting</code> <code>Communication and Problem Solving</code>

## Overview

While being in my role as an IT/AV Technician - there has been many times in which I have had to deal with some networking real life scenarios - putting what I have learnt in my home labs and certifications in networking into real life scenarios where buisness needs and downtime play an important part in being able to get the issue resolved. I feel like in my portfolio this is something that is really good to have as it showcases my experience in networking and IT being able to communicate with colleagues effectively during a difficult time.

This blog is going to cover these scenarios and my perspective on the events that unfolded from them - these include some simple ones to more complex scenarios that have really pushed my knowledge and abilities to my limits. So hope you enjoy these blogs as much as I did trying to resolve them!

## Blog Entry - 02/03/25

This entry is from the 28th of February - however there has been so much since this incident that now is the only time I can actually sit down and do a write up of what happened.

### Brief Overview of Incident

The incident in this blog was a fault that occured with the Wireless Access Points on the residencies site - it was reported to myself at 8am in the morning that some users were having difficulties connecting to the internet from the WIFI - you could get a connection to the Access Points but not to the wider internet. 

### How It Began

The day started with me arriving into the main building on site at around 8am to start my day as usual with some basic tasks that I needed to do during the day. However as I walked into the building I spoke to the Security team who were on the front desk who stated they had reports from some users saying they couldn't access this internet this morning and could only connect to it in one building. At first when the Security team communicated this to me my first thought was this was an isolated incident as there was only one report of it - so I just asked the Security team to put in a ticket as an incident for it and I would go over an investigate it at some point in the day. 

However, I went into my office and then recieved a phone call from the estates site manager who is based in the other building - in which he said he couldn't get a connection at all and after doing a quick survey in the morning he found that all areas of the building had lost internet connection over WIFI. As soon as I got this phone call I knew this was a larger incident and was going to impact **all** the users who are based at the other building (approximately 100 people). So I asked the Estates Manager to put a ticket in for this so that the other incidents could be collated and made my way over to the other site with the Security Team who luckily drove me over with them (the two sites are a 10 min car journey apart). 

In terms of equipment I always carry some spare Cat 5e cables, my handy NetAlly Link Runner network tester and also my laptop so I can at least do some basic networking commands from my command prompt. As this is a WIFI issue I knew I would only be able to do some basic network troubleshooting on site as the WIFI infastructure is maintained by an external company meaning I could only perform limited troubleshooting to begin with. While travelling over my thoughts were going to be what to expect when I arrived, is this going to be something such as a damaged uplink cable between switches, has any updates or configs been pushed to the AP's or switches recently as the WIFI was working fine overnight, looking for anything out of the normal in terms of LED incidcators or error messages. All of this was just to prepare myself for what I was going to see on site of course - it could literally be anything of course.

I then arrived to site and immediately went to the central comms rack which houses the network switches and fibre uplinks between all the buildings - when looking at the network switches I could see that the ports were behaving as normal all showing a green link and green flashing for activity on the ports - all the fibre uplinks looked fine as these go to a master switch which is housed in the comms rack and this was showing green port links and activity indicators. So initial signs were it is not going to be something to do with the switch - the next step then was to look at the AP's which there are 67 of on site across 4 buildings. Luckily one of them is in the office so I could just get a set of ladders and have a look up at them. 

Now this is where the first indication of something being up was showing. The AP's that are used are the <code>NETGEAR WAX625</code> Access points. These AP's are cloud managed through the Netgear Management portal which because these are from an external company are also managed by said external company - on these AP's there are some indiicator lights which are listed below:

<img width="543" alt="WAX625 Indicators " src="https://github.com/user-attachments/assets/3a27d79e-9ed0-4ca7-8cdc-1ab660213506" />

Now when I looked at the one in the office - I noticed that the cloud indicator was rotating between blue, orange and green. Looking at the documentation this indicated that the access point is acting as a node and the mesh setup is in progress. So my first insinct was to go and check the other AP's in the buildings to see what they were doing - and sure enough they were all displaying the same indicator colors on the cloud indicator. So as the wired network was unaffected I could still contact the supplier via the IP phones in the office - when on the phone to the supplier he advised that he had emails from this morning that the AP's had gone down and highlighted that these messages started from **3am** when a **firmware update had been pushed to the AP's through the NETGEAR management system**. He said he had been investigating since 8am this morning and just wanted to try some basic troubleshooting first just to see if it made a difference or not.

The first basic step was to reboot the switches in each building - as the architecture for the site is one main building that then fibre link between three other buildings and have a dedicated POE switch for the AP's in each building. So I went around each building and rebooted the switches for the AP's just to see what effect it had - after around 5 mins I found that this just resulted in the same indicator appearing on all the access points so that didn't work - back on the phone to the supplier it was.





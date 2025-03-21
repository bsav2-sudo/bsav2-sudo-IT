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

Now when I looked at the one in the office - I noticed that the cloud indicator was rotating between blue, orange and green. Looking at the documentation this indicated that the access point is acting as a node and the mesh setup is in progress. So my first insinct was to go and check the other AP's in the buildings to see what they were doing - and sure enough they were all displaying the same indicator colors on the cloud indicator. So as the wired network was unaffected I could still contact the supplier via the IP phones in the office - when on the phone to the supplier he advised that he had emails from this morning that the AP's had gone down and highlighted that these messages started from **3am** when a **firmware update had been pushed to the AP's through the NETGEAR management system**. He said he had been investigating since 8am this morning and just wanted to try some basic troubleshooting first just to see if it made a difference or not. Now when I heard that there had been a firmware update pushed out to the AP's in the morning - my first thoughts were could this be the cause - I mean I had never had experiences of a firmware update bugging out a whole network to make it go down - however it isn't uncommon, I mean take the Crowdstike incident where an update caused widespread outages at major airports and more. But for now I just wanted to try the basic troubleshooting first without getting too ahead of myself - but something to keep in mind.

The first basic step was to reboot the switches in each building - as the architecture for the site is one main building that then fibre link between three other buildings and have a dedicated POE switch for the AP's in each building. So I went around each building and rebooted the switches for the AP's just to see what effect it had - after around 5 mins I found that this just resulted in the same indicator appearing on all the access points so that didn't work - back on the phone to the supplier it was.

Next basic troubleshooting step - after speaking to the supplier again we just wanted to check that nothing had been updated on our firewall which could be blocking any traffic going between the switches and the AP's - so afte infomring my colleagues at the main site that they would see the connection between the sites drop for around 2 minutes, I went over to our firewall and just unpluuged the link between the AP switch and the fireguard - this had no effective result as I was still getting the same issue. From my perspective it was just the best to try all the basic troubleshooting before it went any further. By this point the incident ticket that had been raised by the Estates Manager had been upgraded from a Low Impact and Urgency to a High - thus making it a Major Incident and comms being sent out across all the buisnesses sites to inform users. 

Final troubleshooting stewp before going any deeper - rebooting the router just in case there was any faults - this would be unlikely as the wired service was still running but it was best to check it anyways - again informed my colleagues they would lose pings from the site and rebooted the router in the main commms - this didn't have any affect but did keep the wired services online.

I let the supplier know at the other end and it was time to see if he could remote into the switches to see any of the issues - however he reported to me he couldn't get into any of the switches via the Web GUI, he did report he had 2 minutes where he could get very basic access before the connection would drop and he wouldn't be able to access any of the other switches. This was a similar pattern to what was happening with the AP's when rebotting as you would get 2 mins access to the internet before the connection would drop. At this point we both decided because the supplier had access to the necessary troubleshooting tools (i.e admin access to router and switches) that he would need to travel up and come to site so we could investigate together what was going on. As we are on a remote site it would take the supplier 2 hours 30 mins to get to site which would bring the time to around 1pm, we decided though this needed to happen and he started to travel his way up.

As the incident was now at a stage were it was declared a Major Incident - I was part of the major incident team to respond and give communication to senior engineers and heads of IT on what was going on and where I was at within the troubleshooting process. We had service bridge meetings when needed and had one to discuss the situation in which I told them where I was up to with the supplier regarding troubleshooting - they were happy with the progress that was being made and decided the next update should be given an hour after the supplier was on site so it would give a better picture of where we are. This is part of the problem with having equipment from an external company - it makes it that much harder in order to control and if there is any issues you are reliant on them while your users and buisness are without WIFI capabilities. Nonetheless, in the situation I was in I knew I would have to work to my best to try to reduce downtime as much as possible.

### 10:30am onwards 🕥

From this time onwards I was in a predicement in what I was able to do in terms of the wireless network - but I knew there was other things I could do such as making users aware and stakeholders aware of what was going on at the site - so firstly I co-ordinated with the residencies team on site to get communication out to the residents explainng the situation and trying to give estimated time ranges as to when it could be resolved. The main aim from my point was to at least get some level of service back or full service back which at this point in time I did see as being feasible so long as there wasn't a bigger issue going on. While doing this I also communicated what was going on with wider stakeholders who have an interest in the residencies site also making them aware of the situation and giving time frames.

Of course being able to give timeframes when I was not 100% confident on what the issue was, it was very hard to commmunicate across but I tried to re-assure that the issue would get resolved to some sort of level. I think coming from my background in live events - you have a certain mentality that you keep pushing and pushing until the problem gets solved no matter what time it is (which happened quite a lot) so to me to stay on the job until some level or a full service was resumed was not a problem for me and just came as an instinct.

My final thing to do before trying to think of possible issues happening was to update the service platform (we use ServiceNow) with the latest updates including work notes so if the major incident gets taken down - there is clear notes on the events that took place so they can be mitiagted into the future.

If you are still reading at this point then fair enough because this is basically my whole thought process during the incident. 

Now between the time of putting the work notes up on ServiceNow and the supplier turning up - my thinking was just to inspect the equipment again and look back at the notes already made just to see if there was anything that might spring to mind. And sure enough looking at the notes from before the **firmware update** came back to mind - is it possible that the firmware update would have caused a fault between the switch and the AP themselves - I was thinking to myself surely not but there is always a possibility. Researching the firmware version online there was no reports of any faults with the firmware that Netgear or any other users had reported. Strange. Okay is there a configuraiton issue at play? I would only know now when the supplier got to site. Reboots aren't working so it has got to be something else that is persistent when ever the equipment is turned on. Now I know the PoE switches had recently been upgraded but that was to be able to deliver a higher version of PoE going from PoE+ to PoE++ so that the AP's would be able to work better with a better supply. Something to think about though, for now I can keep looking until the supplier arrives...

### 13:30pm Supplier arrives 🕜

The time is now 13:30pm and the supplier has arrived onto site and we start to troubleshoot what could be going on. At this point it was good to have the supplier as I could actually see the logs that he was recieiving as well as working with another person to try and resolve the issue. The weird issue that we had was there was no logs for anything like a brute-force attack or any sort of flood taking place that would cause the switch to crash after 2 minutes. For the next few hours we just tried to rule out everything it could be such as any network loopback taking place on the network - this of course would only take place on the WIFI as the Ethernet was still working on site - this meant we tried to ping the Switch and restart the AP's to see if we got any logs of a network loop taking place. When we conducted this test - we tried it 3 times and still got the same result in which we would lose any ICMP pings to the switch two minutes after the AP's restarted.

### 16:30pm Start to get serious 🕟

By this time all the troubleshooting we had completed pointed to nothing that was taking place - which now meant we had to isolate exactly what was happening and the best we way decided to do that was to start from scratch. Because the topology is quite simple for the site - we decided to disconnect uplinks to the three other blocks and isolate one of the blocks so we can't get any interference from any of the other AP's on site and focus on one specific area.

To go further as well we unplugged all the AP's in the block going to the switch and decided to go one by one to see when exactly the switch would crash AP by AP. It sounds like a tedious process and trust me it was but this is the only way we could pinpoint what changes were being made on the network to cause the crash. So first we plugged in the first AP and had a ping test to the switch running in the background to note when the switch would crash - and within two minutes we started to get dropped ICMP packets to the switch and noted the switch had crashed. Now this was with just one AP being plugged into the switch which we decided could only point to one thing - the firmware update had caused something to go wrong. First time I have ever experienced this and I must say it is an eye opener - the only time I have seen this ever is with the [Crowdstrike Patch](https://www.techtarget.com/whatis/feature/Explaining-the-largest-IT-outage-in-history-and-whats-next) in which major infastructure went down as part of a routine update - but obviously we were dealing with it on a smaller scale.

So off to the NETGEAR website we went - every single forum has anyone else got the same issue that we are having - is there a known bug in the firmware? The short answer after 30 minutes of research - no. Nobody in the world has resported their being an issue and the only bugs fixes that had been reported were only to do with everything but our issue [Netgear Firmware Release Notes](https://kb.netgear.com/000066571/WAX625-Firmware-version-10-8-12-7). Great. So for now we are on our own on this one.

### 17:45pm Time to try and get a level of service 🕠

Now it was getting close to staff leaving and stakeholders arriving back on site coming back to no WIFI service at all - this was a major problem and we needed to do something about it and find a workaround quick until we could contact NETGEAR and let them know about the issue - againt time as well as we started to get report after report of people not being able to get access to WIFI. This is where we both had a brain wave - the only issue we could see was when we plugged into the POE++ switch with the WAX625 AP's - but these POE++ Switches were only added as part of an upgrade to able to provide 60W to each AP - before that they were running on a POE+ switch which delivers 30W per port and the POE+ switches are still in place in the blocks as they were never removed. So we decided to grab one of the accessible AP's from the main block and take it to the other blocks that has the POE+ switch in the cabinet with the uplinks back in place. After 10 mins and getting the AP on - we had no crashes from the switch and the AP stayed online 😐. I didn't want to get my hopes just yet but it was the first positive sign I had seen in 10 hours on site - but other issues may come for us such as POE issues - but we added 5 x more AP's in the building and see what happened. And guess what - after 15 mins of stability testing they stayed online and the POE+ Switch didn't crash! 

Now we were getting somewhere - we decided to go around each block and plug all AP's into the POE+ switches in the cabinets - and after 20 mins the three blocks were online and stable! It's a temporary fix but it was working apart from one small issue - there is one block that doesn't have the POE+ switch. Not good - and I couldn't source a POE+ switch in such short notice to get it back online tonight and would require intervention from the main base to send one up on Monday - to resolve the issue I made sure all staff members were on Ethernet connections so they can at least access their work computers and work in the meantime. 

The time is now 18:36 and it was time to leave site - we raised the incident with Netgear and tried to get it raised as an urgent incident - I updated my team in main base on the situation and they were happy with the level of service we were able to get back and thankful for me staying that long on site.

![Nick Thanks](https://github.com/user-attachments/assets/cfa6f0b6-8d94-4cf8-a7ac-20b30cb8d07f)

![Gareth Thanks](https://github.com/user-attachments/assets/a6ae1e70-43bd-4f84-a3dc-d27a03ed5312)

![All Thanks](https://github.com/user-attachments/assets/6b43000e-8ad8-4b0b-91da-637c47e4457d)

From here - it is time to let Netgear investigate the issue and come up with either a temporary or complete fix. The biggest lesson I've learnt on this day - expect the unexpected...

## Update - 17/3/25

It is now two weeks later and a lot of things have happened - the first thing is the WIFI is now at full service across each block in the site. NETGEAR are still investigating the fimrware issue but issued a temporary fix to put all the AP's back on the POE++ switches which worked and was implemented on 13/3/25. NETGEAR escalated the incident to their Level 4 tier and was dealt with as a major incident - even in their labs it took them around 2 weeks to replicate the issue and in the end altered their firmware slightly to push back to all AP's.

The whole situation took two weeks to resolve which isn't ideal however I was relying on external sources 90% of the time to configure something their end on top of dealing with my BAU tasks on site keeping this state as a Major Incident. The firmware is still under investigation but a user in USA reported the same issue W.C. 10th March 25 - glad to know it wasn't just us having the issue - a learning curve and a half for me :)

Thanks for reading!

## Blog Entry - 18/03/25

In this scenario, I was tasked to look at the CCTV for one of our sites - omore specifically 3 of the IP cameras were failing to come online within the DVR system. The 3 camera's are on a different part of the site and travel through the network while the other camera's are connected directly to the DVR. The call out originally came from a user reporting a faulty device which then developed when the fault occured. Again this system is managed by an external company so I have no acess to admin accounts, systems etc. Luckily there was an engineer from the company on site so I could ask him to  ake any chnages that needed to be made.

My first thoughts when seeing this situation was - what is the network situation on this CCTV? When I asked the engineer to use the SDAP tool, we foound that the 7 cameras plugged directly into the DVR came up with an IP range of 192.168.2.0/24 with the DVR being seen on the network but with no set IP address and no DG. Strange. On the site we don't use the 192.168.2/24 range - instead we use the Class A private range of 10.0.0.0/24. So the fact the DVR didn't have an IP and all the direct cameras were on a different range was what I should say as being different.

The only thing that came to my mind was that the DVR was acting as a DHCP server for the cameras directly in. I don't have much experience in CCTV but it is the only logical thing I could think of. So we need to get the DVR on the same network as the 3 external cameras and then get the camera switch onto the network. So to test that this would work - we plugged the engineers laptop into the uplink of the switch and run a ipconfig to see that we would get an IP address in the 10. range. 

When we run this test - sure enough we got the 10. address. So the plan of attack:

- Change the DVR patch from the switch to the router where it would gain a 10. address
- Allocate the DVR a 10. address using DHCP
- Plug the camera switch into the uplink on the switch in the other building
- Run SDAP and see the results.

This excellent drawing should display what we were trying to achieve 

![Epic Diagram that makes sense to me](https://github.com/user-attachments/assets/e127196d-9b77-4a5a-8fb4-51bdb1bdc7cc)

And sure enough after we did this and run the SDAP - we then seen the three camera's appear - but with a few little issues:

- Once came on staright away
- Two of them came on SDAP but with 192.168.2/24 IP's

Okay, so lets get them onto a 10. IP address. When going onto the CCTV console - these camera's have been saved to have a 10. address anyways so I just needed to match them up on the camera themselves. One of them changed IP address, Subnet Mask and Default Gateway with no problems however the last one kept rejecting the changes. Now we thought there was an IP conflict but after investogation we found the last camera just needed a reset - and then we had all 3 cameras back!

The lesson from this one - check the basics first before going too far in. Check IP ranges, Check Manufcturers website, Run ping tests. 😄

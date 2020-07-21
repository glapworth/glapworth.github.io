---
title: "TVHeadend and my Raspberry Pi 3b"
categories:
  - Linux
tags:
  - tv
  - linux
---
I recently had a problem with my chimney - a pigeon flew down the hole and decided to nest in the cavity approximately 10 inches
from the vent in the wall next to my head when I sleep.  The problem occoured because a few years ago during a storm, the cowl on 
the chimney blew off.  Being proactive I considered fixing it after the winter had died down somewhat.  My roof is slate, and it'd 
be dangerous for me to go up there whilst it was slippery.  Well, life happened and I promptly forgot about the cowl, that is until I 
heard the not so soothing coo of my new lodger.

I considered replacing the cowl by myself, but I didn't have the ladders on hand to do the job, so I went off to Google looking for 
a roofer to help me out.  Well it turns out that roofers don't come cheap.  The cowl itself was only £20 from Amazon, but the roofer
would have cost me an arm and a leg since it was in the middle of lock-down in my area.  I spent a few hours considering my options when
I realised that I don't have an arial on the roof.  We've been here for over 10 years, and never needed an arial for the TV - we stream 
most things, but have recently considered moving and not having an arial might put some people off. I went searching again for an arial installation company to help - and if I'm cheeky - whilst you're up there, could you
pop this cowl on the chimney for me?  I found a lovely company local to me that installed the arial, and the cowl for £100. 

So now I have a cowl, and I have an arial.  But other than plug the arial in it into the TV, what else can I do, I thought.  
I found a Raspberry Pi 3b I had lying around and bought a Pi TV HAT for £6.  Installed Ubuntu 20.04 and with snap (I don't like it either, but that is a conversation for another day.)
installed TVHeadEnd.  Now theoretically I can stream tv to any device in the house.  Fantastic.  No more wresting with iPlayer, ITV Player, Channel 4 Player and so 
on.  

I've a few comments about FireTV sticks, Chromecasts and watching the TV stream which is slow and difficult to navigate - but for now it works. 

If you're like me, and wanted to run Ubuntu Server on the RPI with TVHeadend and found that it isn't able to find the tuner card then
the reason is because of AppArmor which is stopping you from accessing the `/dev/dvb/*` device.  The simple answer is:

`sudo snap connect tvheadend:dvb`

I don't like this snap thing.  Call me a fuddy-duddy.

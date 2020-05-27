# Dell-U2711-Monitor
The 'fix' 'How To' 'Solve' for resolution problems with the Dell U2711 and others of it's ilk.

So you're here and you've found this repo. Probably because you have had unfathomable frustration with the video settigns on your monitor and you've probably plugged it into a mac or tried to use the HDMI and found it's displaying HD/1080p/1920x1080 rather than the 2560x1440 the panel is capable of.

### Yup, I've been there and it's a bit of a 'mare.

So here's the deal. Having owned this panel from around 2012 from new, I've had my challenges too.
On the Mac it has an annoying issue of not talking to the display port if your system sleeps or you switch inputs, and then there is the issues of connecting to the DVI ports or the HDMI where you get 1080p but nothing higher.

### Let's unpack a few things.

* DVI-D This is true DVI-D dual link rather than the DVI-I that is also available, which is single link. DVI-D Single link is not a thing, it is DVI-I mislabeled. Which is frustrating as many DVI-I cables are labeled DVI-D when they are not. It is misleading marketing and bloody frustrating.
* I've used DVI-D and display port (DP) on this monitor for years and it's generally been very very good. Except for the DP sleeping bit. I have run this on a range of systems, mainly Mac's and had full resolution on this too.
* Anything using HDMI is a pain int he arse, either as the source from yoru machine or as the receiver on the monitor, and this has everythign to do with the EDID configuration on the monitor.

## The tricks:
### DVI-D
#### The Adapter - If Needed
If you don't have a DVI-D native output on your system/video card you're going to need an adapter, and this is where it get's tricky.
* Not all DVI adapters are DVI-D, so you need to source one that is DVI-D capable. Often a physical sign is they don't have the second group of pins for the second or dual signal path, but that isn't always the case. So you need to ensure that you have a dual link capable adapter. I found the Apple Thunderport 2 to DVI adapter was the only one I could locate, which will also be in short supply as a discontinued interface. 
* This is the Apple one that I would expect would work https://www.apple.com/nz/shop/product/MB570Z/B/mini-displayport-to-dvi-adapter
* This is a link to one I would not expect to work, it's indicated as 1080p not the full spec required. https://www.pbtech.co.nz/product/CABSTT690287/StarTech-MDP2DVIMM3B-Mini-DisplayPort-DP-to-DVI
#### The Cable - Definitely Needed
The second bit is the more obvious bit, you need a DVI-D dual link cable. 
* This one local for me I would expect to work, being it is listed as a dual link DVI-D https://www.pbtech.co.nz/product/ITPAK621N/Dynamix-2M-DVI-D-Male-to-DVI-D-Male-Digital-Dual-L
* This is a cable that won't work, Listed as HDMI (Which I'll come to soon) - DVI-D though to their credit they do state single link https://www.pbtech.co.nz/product/CABDNX1542/Dynamix-C-HDMIDVI-1-1M-HDMI-Male-to-DVI-D-Male-181
* This is a good example of mislabelling, the incomplete pins in the plug give away the lack of dual channel. https://www.pbtech.co.nz/product/CABSTT1583045/StarTech-DVIMM6-6-ft-DVI-D-Single-Link-Cable---Mal

### Ok that's DVI-D, what about Display Port (DP)
#### The Adapter - If Needed
Again like the DVI-D, if you don't have a native port on your machine, you'll need an adapter. This a little simpler on than DVI-D as the Display Port protocol is much higher in bandwidth as a result.
* So pretty much any suitable adapter is going to do the job here. The display port solution is my preferred approach, though going from HDMI to DP is a problem, but Thunderbolt/Mini DP to DP is pretty solid.
* With this solution you may have to turn off system sleep, as you need to keep the video card alive for the DP conntion to not drop out. Power off screen save is ok, that's a blanking signal, suspend your system and it doesn't play noce when it comes back. 
* Also too, if you need to switch sources regularly, then avoid DP as the choice of connection.
* If you wish to use the PBP, picture by picture I think, settign then DP is off the cards too, it's not included. HDMI, Composite, and Component are the only options
#### The Cable
* Grab any cable, they should all work.

### VGA
Yes, it's there, but why bother, it is analogue and not really up to the task of high res monitor tasks. Ok to get by for a bit, but find a different solution.

### HDMI
#### This is where it gets difficult
For some unknown reason Dell decided not to include all resolutions in the baked in EDID data file on the monitor. Which is where this all comes to grief and whay you are reading this epistle.
* An EDID file is an identifer file or data that the monitor spit at your system when connected to explain the HDMI capabilities of the monitor, so your system knows how to talk to it.
* By default Dell have not included the panel's native 2560x1440 in the EDID data assuming that you'd only use it on HDMI if using somethign other than a computer to connect to it.
* This lengthy discussion on the issue covers it all in a lot more detail, adn it's confusing https://forums.whirlpool.net.au/thread/9lm2vrq3
* In basic terms you need to 'update' the EDID file in the system, on the monitor or your computer, to get it to recognise the right resolution settings so you can go from there.

#### Why the Git Hub Repo 
Both for my learning and so you can shortcut some of the pain and get to the point.
* Yes this is a long read, as you need the background and things influence your choices, if you have alternative port options, that's the easy approach, if you only havd HDMI, then you're here reading this.

On the Mac, as the forum link above covers Linux and Windows quite well, we need to do a few things that aren't the easiest to do and updates like Catalina have made it harder.
* First off, this post by Michael Civitillo is the best approach to date I have found. https://michaelcivitillo.com/overriding-edid-on-osx-for-external-monitors/ I have included a copy/paste of the page in the repo incase it disappears, like some of the forum links above have.
* Since Michael's 2017 post Apple has released Catalina, and this has made the / or root directory of the system read only. 

So the way around that is to run {sudo mount -uw /} before you attmpt to copy anything into the system area.  





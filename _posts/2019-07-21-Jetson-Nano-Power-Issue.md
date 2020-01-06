---
title: "NVIDIA Jetson Nano: Power Issues"
published: False
---

# Preface
This blog is written specifically for self-initiated projects in engineering academy. I have voluntarily signed up for a project that requires me to upgrade one of my hackathon projects. The aim is to create an AGV that can apply edge detection.

The first thing that came to my mind is the Jetson Nano. This is a very powerful board with the ARM A-52 Quad Core Processor, 4GB DDR4 Memory, and 128CUDA cores Maxwell Architecture GPU. And it only costs USD99! For a form factor that is this small, with dedicated graphics, this development board is truly a steal. After shipping and custom taxes, the overall cost bumped up to SGD200+, pretty hefty but I was excited as this is the first time I've interacted with a board that is this prestige and powerful.
#### To do: put image here!

# The Problem Part 1
The NVIDIA Jetson Nano, due to it's powerful components, sadly consumes more power than say a Raspberry pi. I first received this board 19th June 2019, and was pleased with all the powering options I had. There was a micro USB on board, a barrel slot which supported 5V 4A, and 2 power input pins, each taking up to a maximum of 3A at 5V. 

#### To do: put image here

Yep, I really think that this blog is important to document just power delivery due to how much time and effort I have wasted on this. 

I followed the Jetson Nano's getting started guide, burnt the jetson Nano image with Etcher, plugged it in the SD card slot, powered it up, and it shuts down again by itself. I went on to troubleshoot the image but due to my lack of knowledge in this regard, to no avail. Later, I requested help from a (friend of mine)[codingIndex.xyz], and believe it or not, the Jetson Nano booted without any problems at all. This made me very confused, as if this problem really didn't exist, then what happened? How do I replicate it? Sure enough, I went back home, powered the Jetson Nano, and it booted without any issues! Go figure!

# The Problem Part 2
After almost a month's time of shoving the Jetson Nano into the racks due to my inability to replicate the problem, I decided that if the problem is not replicable, it could be just a faulty board and maybe everything works fine now. So I booted it and to my surprise, the problem presented itself again, I booted it, saw the LED indicator light up, then it dimmed down again.

#### Todo: show the reboot flow (video)

Seeing this made me really think what the board is doing. I remember encountering this in a previous school project, whereby my MP3 player kept on restarting itself, upon digging around and looing at the max current, I found out that the MP3 player is drawing more current than I expected, exceeding the power limits of the microcontroller itself, causing what is called a "Brown-out". However, the Jetson Nano didn't restart itself, but I do suspect that it is drawing more current than the rated 5V 2A from the micro USB. Sure enough, just by supplying a little more current from the GPIO pins, common grounding the 2 supplies, the Jetson Nano reache a new screen, but then shuts down again, most probably due to the high current draw.

# Ghetto Solution: Dual power supply?
With this suspicion in mind, I decided to supply just more current to it. I have this multi-USB socket plug, rated to support up to 4.4A autoMax, meaning it can supply a total of 4.4A total to the 4 USB sockets. Sadly, it couldn't have a maximum of 4.4A at only one socket but hey it's better than nothing. Hence, my solution is to plug 2 USB, one of them will still be a general micro USB, while the other will be just connected to input GPIO pins. I will definitely be looking in to more permanent solutions in the future.

Below are the tools I used: 
- 2x MicroUSB cables
- Neccessary tools

I have procured the items at Pit Money in JCube.

This solution will be posted to instructables. 

#### To do: actually do it, then put image here

#
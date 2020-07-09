---
title: "NVIDIA Jetson Nano: Power Issues"
published: true
---

# Preface
In today's day and age, there is a lot of untapped potential for robots, such as wayguiding, security patrol, greeting customers etc. These applications make use of Machine Learning, particularly using it for Edge Detection due to low latency, carrying out tasks such as facial recognition, NLP, navigation in unfamiliar places etc. I looked at a lot of options, one that really stuck to me was creating an AGV using the Jetson Nano.

The Jetson Nano is a very powerful board with the ARM A-52 Quad Core Processor, 4GB DDR4 Memory, and 128CUDA cores Maxwell Architecture GPU. And it only costs USD99! For a form factor that is this small, with dedicated graphics, this development board is truly a steal. After shipping and custom taxes, the overall cost bumped up to SGD200+ (<i> ouch </i>). Just when I thought development can commence immediately, the true battle for <i>Power</i> was just about to happen (pun intended).

<img src="/images/JetsonNano.jpg"/>

# The Problem Part 1
The NVIDIA Jetson Nano, due to it's powerful components, sadly consumes more power than say a Raspberry pi. I first received this board 19th June 2019, and was pleased with all the powering options I had. There was a micro USB on board, a barrel slot which supported 5V 4A, and 2 power input pins, each taking up to a maximum of 3A at 5V. 

I followed the Jetson Nano's getting started guide, flashed the jetson Nano image with Etcher, plugged it in the SD card slot, powered it up, and it shuts down again by itself. I went on to troubleshoot the image but due to my lack of knowledge in this regard, to no avail. Later, I requested help from a (friend of mine)[codingIndex.xyz] to troubleshoot with me, and believe it or not, the Jetson Nano did not show signs of failed botting, but instead booted without any problems at all. This made me very confused, as it seems that this problem really didn't exist at all. How do I replicate it? I went back home, powered the Jetson Nano, and it booted without any issues agian! Go figure!

# The Problem Part 2
After almost a month's time of shoving the Jetson Nano into the racks due school and other commitments, I decided to revisit it and start on creating the AGV. So I booted it and to my surprise, the problem presented itself again. I plugged in the micro-USB cable, saw the LED indicator light up, then it dimmed down again. There are videos documenting this exact process on youtube, so I was sure this isn't a one-off event.

<iframe width="100%" src="https://www.youtube.com/watch?v=hV6Znadax-Q" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Seeing this made me really think what the board is doing. I remember encountering this in a previous school project, whereby an MP3 player kept on restarting itself in a specific section of the MP3 file. I dug around and looked at the max current of MP3 player and microcontrollers used, I found out that the MP3 player is drawing more current than I expected, exceeding the rated output of the microcontroller itself, causing what is called a "Brown-out" of the microcontroller. Similarly, I suspect the Jetson Nano took more than 5V2A, albeit the Jetson Nano didn't restart itself, possibly due to safety reasons. Sure enough, just by supplying a little more current directly to the GPIO pins, common grounding the 2 supplies, I finally saw the Jetson Nano Boot Screen.

# Ghetto Solution: Dual power supply?
With this suspicion in mind, I decided to supply just more current to it. I have this multi-USB socket plug, rated to support up to 4.4A autoMax, meaning it can supply a total of 4.4A total to the 4 USB sockets. Sadly, it couldn't have a maximum of 4.4A at only one socket but hey it's better than nothing. Hence, my solution is to plug 2 USB, one of them will still be a general micro USB, while the other will be just connected to input GPIO pins. I will definitely be looking in to more permanent solutions in the future.

Below are the tools I used: 
- 2x MicroUSB cables
- electrical tape
- Male-To-Female Jumpers

I have procured the items at Pit Money in JCube, Singapore. This is a pretty simple modification of the MicroUSB cable, just cut off the MircoUSB side, find the power cables (usually red and black), then solder on the jumpers, insulate the cables individually, verify the terminals have a 5V potential difference, finally tidy it up.

<img src="/images/WireFull.jpg">
<img src="/images/WireJoints.jpg">

After the modifications, the Jetson Nano is able to boot consistently! Cheers!

# Permanent Solution: Power Mode

Following the consistent boot of Jetson Nano, I decided to end this madness once and for all, by setting the power mode to consume less power. (We can't have a robot stuck by the wall right? That's called a <i>computer</i>!) By default, the Jetson Nano draws a nominal 10W. It is possible to change it to consume 5W instead, allowing us to power it using a normal usb cable.

<i> "But Bryan, that limits the capability of the Jetson Nano!" </i>

Ok ok, that's true, but its better than having it sit there and do nothing. Also, I think during the development phases, it is ok to switch between the different power modes. For now, I want to do some setup through the image's GUI, so attaching my peripherals will definitely cause it to shutdown due to a lack of power. I followed [this](https://www.jetsonhacks.com/2019/04/10/jetson-nano-use-more-power/) guide and successfully changed it.

<i> "But Bryan, you can get a 5V3A powerbank!" </i>

<s>Shh... No one talk about that.</s> I'll upgrade the powerbank to a 5V3A one when I make full use of the Jetson Nano's capabilities. It also takes some modifications to use a barrel jack instead of a MircoUSB.

And with that, my problem was solved! Now I can power my Jetson Nano from a 5V2A powerbank. Stay tuned for more updates on Jetson Nano!
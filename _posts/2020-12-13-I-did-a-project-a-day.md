---
title: "I did a project a day, this is what I got"
published: true
---

# Preface
The saying goes, "curiousity kills the cat". What if the cat wanted to stay alive forever, and never dared to make the first step, killing its curiousity forever? Thinking about this question, it made me really wonder whether the path I have chosen is a good fit for me.

Hi, I am Bryan, a graduate of Singapore Polytechnic, and a current student in NUS majoring in Computer Science. Within the span of less than 6 months, I have met bright individuals that are leaps and bounds beyond me, some younger than me and some just about my age. It got me thinking, what did they do differently that allowed them to be who they are today? If so, how much potential have I actually missed out, thinking that I was already at my peak? 

I tried to study really hard, but touch wood I think I barely passed for some modules. I reflected on how I studied, my patterns and my behaviours. If I could turn back time, I'd do the same about of deep thinking, work vs study, soft-skills vs technical skills etc; and getting distracted by all the possible projects that I could do, but didn't have enough time. Was I just not cut out for studying?

A small voice in me said <i>"Not enough time?!?! Tis so easy I can code it in 10 minutes!"</i> At the time, I did have a few mini projects in mind that are easy to complete. But there were some that had to take longer than usual as well!

# Inspiration
I came across this youtube channel by (Zack Freedman)[https://www.youtube.com/user/ZackFreedman?app=desktop], and was inspired by his Among us IRL video, where he made various among us props within the span of a week. Sure, they were not perfect, but they were completed and function as per intended!

Also, the channel Unus Annus really hit me when they actually deleted a channel with millions of subscribers. Check out (Markiplier)[https://www.youtube.com/watch?v=jm7ZAMAsPxI] channel for his thoughts on Unus Annus. I could relate to the experience when I left my high school, but never to the fullest extent due to me having so much regrets.

I wanted a change.

Since I was in my winter break, I thought why not do a project a day and challenge my boundaries?

You can see my Journey on Instagram: [https://www.instagram.com/modelconverge/]

## Day 1, 27th November 2020
I focused on getting my old Jetson Nano tank up and running again. I didn't make a blog post about it as it was too infantile to be called a masterpiece (which I still plan to make it my magnum opus). However, too big of a project will just be a white elephant. So I started to get it running. For some reason, the tank tracks were catching on the battery holder, which I still didn't know what is causing it till this day.

## Day 2, 28th November 2020
I copied a pan-tilt camera on Thingiverse, and flashed the ESP32-cam demo code. Next, I took the PCA9685 PWM servo driver to control the pan tilt camera through the GPIO pins on the Jetson Nano from a Jupyter Notebook. I met some permisssion problems with the keyboard library so I had to export the notebook as a `.py` file and ran it from the command line instead.

## Day 3, 29th November 2020
I assembled a joystick, initially with an Arduino Pro micro, and then with an ESP8266. The goal was to send the message out, and I wanted to ensure the logic of my code was correct. I used MQTT to send, and it turned out fine. I tried using the Arduino Pro Micro with an ESP01 to send messages, but I didn't have a logic shifter module nor enough resistors to make a resitor based level shifter circuit.

## Day 4, 30th November 2020
I revisited my part-time code maintainence work. There was a weird double click event which seems to be common on older ionic versions. I could not replicate it consistently, but many times enought to have a buggy experience. I can't disclose too much, but it essentially involves reading the error logs online, and trying to replicate them.

## Day 5, 1st December 2020
I scavanged for any ESP32 in my stash, and I found one I got in Singapore Polytechnic that was in unknown condition. Lucky for me, I could program it with the ESP32 Wrover settings, changing only the Baud Rate to `115200`. I replaced the ESP8266 of my joystick and linked the joystick to the movement of the pan-tilt camera. I also met some problems when sending MQTT messages parsing, as the messages received seem to contain info from other topics.

## Day 6, 2nd December 2020
I captured the ESP32 camera stream following a guide online. Initially I hoped to just use opencv to do so, but it turns out opencv couldn't capture images in batches. Therefore, I had to read the ESP32 cam code as well as the mJPEG specifications to properly capture the stream and generate an image. In my spare time I also created a script to control the movement of the tank using the joystick.

## Day 7, 3rd December 2020
I revisited my mining rig and my other systems, where me and 2 friends were about to start a business on selling computers, now just sitting in my dorm collecting dust. Out of curiousity, I wanted to see if some of the parts still worked, and whether I could change out my mining power supply. Believe it or not that took nearly a day. Also, I found out that my TV screen is still in working condition! The hdmi signal seems to require boosting now, and that's why my laptop cannot connect to it but my desktop had no problems doing so. 

# Post Mortem
It's true, some of the projects seem small and may not be called a "project" by its own right. Initially, I thought I would do something grandiose each day. But looking back, I completed essentially 5 things

1. Got my Jetson Nano tank ready
2. Setup a Pan-Tilt camera for the Jetson Nano
3. Learnt how to capture the ESP32-cam stream
4. Created a joystick to control the Jetson Nano tank as well as the Camera 
5. Upgraded my server to something more reasonable

That was 4 things more than when I had a break between the end of my internship and the begining of my university life!

The exhiliarating feeling that rushes as the clock is ticking to midnight, that was reminiscent of my hackathon days with my pals. I soon knew what it all meant. The feeling that one day things will end, and whatever we did was who we were, and lastly to feel the mortality is to give it your all, until you won't have any regrets. Although at times I could complete the project way before the time finished ticking, I find myself quickly jumping to the next project (of which I did not include here), those projects deserve a blog of their own. I felt how precious time was, and wanted to continue feeling that way.

That was a pretty fun week!

Why was this blogpost so late? Well, cuz I am still doing projects even till this day!

Thanks for reading! Have a great day ahead!
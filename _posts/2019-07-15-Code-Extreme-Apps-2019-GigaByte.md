---
title: "Code Extreme Apps 2019: My Experience in Leading"
published: True
---
# Preface

I am Bryan Tee Pak Hong from Singapore Polytechnic. Today, I would like to share my experience in Code Extreme Apps 2019(CXA 2019). The an annual hackathon co-organized by IMDA and iTSC in Singapore. My team consisted of me, Silviana(https://github.com/silvianaho), and Lee Weijuin(https://github.com/weijuinlee). The topic for this year is Digital Transformation (DX).

This is the first time I have broken off from my original team (Team Sudo Coders) whose blogs can be found [here](https://codingIndex.xyz) and [here](https://geekfile.xyz), and is the first time I had to officially "lead" a team (more into why I quote this).

The whole event is split into a few categories:
- Pre Hackathon
- During Hackathon
- Before Pitching
- After Pitching
- Debrief Session

# Pre Hackathon

## A few months before hackathon

When I first heard of the annual event, I was very enthusiastic in participating this event. However, I have synonymously agreed with one of my previous teammate that it is best we had some leadership experience, hence our original dream team had to be split. I was then requried to recruit my own "dream team". I have identified that I lacked someone to do the backend of a product and someone to perform some "cool features" to the product. This was when I thought of Silviana, whom I have met during a programming class. Although she was new to not only the programming world, but also Singapore and Hackathons, I find that she has some characteristics in being a backend developer. Next, I needed someone to do cool features. Usually these only take a line or two to be "claimed" the feature exist so it should be relatively easy. I needed someone that can explain the concepts in the english-est way possible (I become a robot when I need to explain these things at times), which I then identified WeiJuin, who is a great and outspoken person for this task. Hence my team was formed. I am aware that saying people in this regard may be itemizing them, but this is my most honest thought process and I wish whoever reading this can also be as objective when choosing a teammate, cruel or not. It wasn't my intention to do so however, as I just want a baalnced team that can leverage on each others' strengths and compliment each others' weaknesses.

Lucky enough, we managed to brainstorm a few cool ideas with my previous teammate, and validated it among ourselves. I will keep the ideas confidential as we may end up using them in future projects. 

## A few weeks before hackathon

The idea that was validated amongst ourselves was bested by an action going around in Singapore called <i>"Belanja A Meal"</i>, which we find to be much more meaningful to digitize/digitalize. This action basically allows anyone to donate to supported coffee shops using a pay-forward concept to anyone who needs it. For a lack of a better word, you are giving people in need food before they even request it. The current method is very labourous, using magnets to represent how much food is left for a particular store. You can read more about it [here](https://mothership.sg/2018/01/bukit-batok-coffee-shop-belanja-a-meal-project/).

However, the moment we decided on this topic was T minus one week to hackathon and all of us were panicking at that point.

This was my first miscalculation: Despite having the traits of a backend person, Silviana loved designing, making her a perfect candidate for front-end development, while WeiJuin due to his heavy workload (something I can relate to), is more comfortable doing things that he had experience in, somehow it was front-end(?). 

This destroyed my ideal dynamic, but not all hope was lost. I told myself if anyone would have the strength to do the backend of a system, it would be me, as our solution can be "hardware-less", something I have been doing again and again. So I started learning node.JS at this point of time, attempting to link the webpages together and handle simple data storage, while I allowed two person to handle the front-end of a product, completely discarding fancy features our web application could have. I simply cannot find any justification to hop on to a previous idea which had way fancier features as practically speaking it would be too much work on the team. Meanwhile, this project due to its simplistic nature shouldn't have fancy features to confuse needy people, and we really didn't know where to add any special features.

I stayed up a few nights without sleeping in order to get the basics up and running, and before the hackathon, the server was working as per intended and I felt at ease. All that was left was styling everything, which can be done within 24 hours (imo at least).

# During hackathon

## T-24 hours
During the hackathon day, we prepared a lot of snacks to keep us awake, while bringing some hardware just in case we had time to prepare any sort of hardware to boost our chances of winning. At the day itself, a twist, features that was not included in the previous briefings and not taken into consideration during brainstorming session, was introduced. Luckily for us, we mananged to decide which to integrate -- Gamifying it. We later distributed the workload pretty well and it was a considerably smooth ride. The front-end was done very well, better than what I hoped for, the backend was working as per intended, what is left is actually displaying the data from the Database to the web interface. The process was harder than expected as this is basically my first time touching JS, but was doable in a couple of hours. 

## T-16 hours
It wasn't until 12 hours into our hackathon we met with our first major problem, the web page for restaurants seem to not make any sense, as they might not even be interested in exploring who or what did something, while we forgotten to have a user profile page. At this point, Silviana was too stressed out to create another profile page, which made sense due to the short notice, while WeiJuin decided to help out adding fancy features using hardware, something that I never had thought of. Hence, we had a page linking overhaul here.

At this point, the stress starts creeping up on me, as the time left is less and less and our current progress is lacking a lot more than what I have planned and provisioned for. This means I had to cut corners in our product in some way. We decided to make the restaurant dashboard into the user profile page and implement a proof-of-concept login and sign up page. A neccessary evil indeed for the benefit of the team.

## T-12 hours

At this point, me and Silviana had been awake for more than 24 hours (a few restless nights and early classes on hackathon day), while WeiJuin had been taking a nap to sharpen his sword early, ensuring a tip-top performance early in the morning. We were around 75% done with the web-app and decided to take a quick breakfast break. This was when both of us sort of broke down as we not only feel the fatigue due to the aftermath of **coffee**, but also the stress on our shoulders. We decided to extend this break to 3 hours just to catch our breath. A good idea in hindsight to improve performance later on.

## T-9 hours

Back to work, time is ticking! All of us are awake at this point for the better or for the worse. Although the planning was to finish it by this time, I feel like our product can be completed within the time limit. All of us just needed a different working environment, so we decided to sneak into emptier rooms. It worked out well for us as we were more focused and less stress.

## T-3 hours

Goodness gracious, our work was complete. We started to discuss a little bit on the pitch.

Lucky for us, the hardware was working! Me and Weijuin worked on sending HTTP POST request to the server and it worked as per expected!

Hang on a second, is that a non-operational button! GGWP. I went back to work. Silviana helped me styled somethings as well so we had no choice but to let WeiJuin handle the presentation powerpoints. I still felt very bad as we could easily chose to not show this particular feature as after the last 3 hours, the button still couldn't work. A little bit of detail, the button was dynamically generated and allowed a person to choose between 2 options, donating at a normal rate and donating at a discounted rate, the selection of the radio button, which was also dynamically generated, was then appended to another dynamically generated invisible form, which is sent to the server as a POST request. What I should've done is to make multiple forms that was supposed to be dynamically generated static instead, so that I have one less level of dynamic elements checking to generate the moment the button is pressed.

With that being said, everything else was working well and we have a 95% completed checkpoint, one that is good enough for pitching.

Below is a demonstration of the web interface:
<iframe width="560" height="315" src="https://www.youtube.com/embed/ym8EqnRknBY" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Before pitching

**Critical** : Something that we didn't do was rehearse how the web page was supposed to flow, and generating a script individually for the inexperienced Silviana was too much work for her. Me and WeiJuin decided to always go back to the basics and core of our product: Save food by pre-emptively reserving food to those in need, while being altruistic with our product. The pitch went as expected and we not only answered the Q&A flawlessly, we managed to get our ideas to the judges and they were quite impressed!

# After pitching

As we were one of the first teams to present, we decided to exit the venue, do a quick debrief, then re-enter the venue. We came to a consensus that we have conveyed most, if not all of our core ideas and demonstrated the user interaction with web application, as well as its functionality aspect quite well. Then, we re-entered the room to listen what other teams had come up with. Two other teams actually had a way longer interview with the judges compared to us, both teams are however from SP, and we were genuinely happy for them!

Of course, we thought to ourselves, we have done our best, we already stand the most chance in winning given the effort we have put in over the past few days/weeks. In my opinion, we stand a high chance in being one of the 10-11 finalist for CXA 2019.

# Debrief Session

After the promised results date, sadly we did not receive any announcement on us being selected as a finalist. Even though we did really did our best, luck just wasn't on our side. An official debrief session with the team has not been made but I do have some ideas what happened in the process:

- Our idea was not focused enough in solving food waste, we focused on helping the needy individuals instead of solving food waste
- My planning and scouting for teammates was a flop, assigning unsuitable roles for both of my valuable teammates
- Overhauling of idea induced way too much stress, handling of it was not well done.
- Insufficient preparation time due to a last minute change in idea

with just the 4 problems above, the team has failed in being selected, despite the miraculous comeback nearing the end of the hackathon.

# Conclusion

All in all, I feel like there is still a lot of room for improvement in my leadership skills as I not only have failed to identify strengths in individuals early on, but also failed to identify the fundemental flaw in our idea early on, which if I had, we would've tried to fix it before the hackathon. However, setting timelines and deadlines, saying at what point is a good enough point to show our target audience, and picking up from where I have fail, I have really tried my best and I am pleased with how the team as a whole performed as a whole. 

Code Extreme Apps 2019 was a really fun experience. Rumor has it that it shall be shut down forever, never to see the light of day ever again. Will it be revamp? Who knows. Nevertheless, congratulations to all the finalists and winners and keep fighting, and all the best for those who participated and put in as much, if not more effort, than our team!

However, in the future, I hope to work in a team where I like to call a "Self directed team", a team that understands what the product is and is willing to take up roles automatically and solve problems on their own. In a sense, everyone is a leader in their own domain, where little to no inteference between parties is involved, and everyone is clear what is required to complete the project, automatically complementing each others' strengths and weaknesses.

That's it for today, thanks for taking your time to read this extremely long article. If You read until here you are amazing. Do snoop around my articles and repositories for other fun stuff!
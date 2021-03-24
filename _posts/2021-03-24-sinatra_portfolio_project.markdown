---
layout: post
title:      "Sinatra Portfolio Project "
date:       2021-03-24 20:24:51 +0000
permalink:  sinatra_portfolio_project
---

## Meditation Tracker



Mindfulness is a concept that has gained some popularity in the last few years. The term encompasses knowing where we are - or being in the moment - and also keeping an awareness of where we have been before (reflection). A meditation tracker can help supplement these areas of awareness. While I'm not an expert on the matter, it is a topic I have great interest in and mindful meditation is something I try to practice for its mental and emotional benefits. 

I used Sinatra to create a way to quickly and easily log when meditation was practiced as well documenting the person's mood right after that session. It has two models: the user. and the meditation session, with the latter belonging to the former. A user is able to log multiple sessions once authenticated.

The user begins by either signing up if they do not have an account, or logging in if they do. 
If they're signing up, they're required to correctly fill in all fields in the sign up form or they will get an error message. The user's password is made secure using the bcrypt gem. Setting up the sign up and log in functions was fairly straightforward thanks to this gem streamlining the process. 

Once the user signs up they will be directed to the main menu:
![](https://i.ibb.co/BGvsRYR/Screen-Shot-2021-03-24-at-3-53-39-PM.png)

If they choose to log a new meditation session they will be guided to where a new session can be created. This form asks for three things from the user. The first is an estimate of how many minutes they were able to practice meditation for that session. The second is a quick rating of their mood right after. Incorporating images into this radio input type took a little bit of research but was ultimately very worth it for the aesthetic. 

![](https://i.ibb.co/Qfqjyy2/Screen-Shot-2021-03-24-at-3-58-13-PM.png)

The third question was a stretch goal when planning out this application. It inquires about the types of meditation used during that particular session, with a small descriptor of each type. Initially these were going to be radio inputs as well but given that multiple types can be utilized during meditation practice, the input type is checkboxes. 
Once the user submits the session they will be redirected to the show page for that particular session. This can only be accessed if the session ID matches the user ID of that session, which prevents users from viewing sessions that are not theirs. Once on the view page they have the option to edit it, delete it, go back to the main view or log out. 

This project was an invaluable learning experience. I gained a better understanding of the CSS and HTML components in particular, given the initial difficulty of incorporating interactable images. It also greatly helped my grasp of user authentication, data validation and the overall MVC structure.





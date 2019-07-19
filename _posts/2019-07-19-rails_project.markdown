---
layout: post
title:      "Rails Project"
date:       2019-07-19 15:17:16 -0400
permalink:  rails_project
---


For my Rails Project, I created a simple travel app called TravelUsa.  This app allows users to sign up for an account, create attractions within the USA that they have visited, and it allows users to leave comments on states.  Users can also browse attractions by state, and the associated comments.  Users can sign into their account via an email and password, or they can sign in via github.  

Users must have an email address and a password to sign in.  When creating an attraction, users must also provide a name, a location, and must select a state from a drop down list.  As users create attractions, or select attractions through browsing through the states' attraction list, the attractions are presented as a list on the user's attraction list.  

The app has two join tables: a comment table which belongs to a state and a user, and an attractions table which belongs to a state and a user.  The class scope method used is for most_comments for a state.  Users can see the state with the most comments.  Comments are also counted for each state on the state page.  

The biggest difficulty I had with this project was be far the omniauth setup.  After consulting several different resources, trying facebook, github and google, and going through what appeared to be some blockages due to internet and internet security settings, I was finally able to get it to work with github.  Really, omniauth is not that difficult to set up.  However, when it doesn't work, it really doesn't work, and there soon become a lot of factors that could be hindering the process.  My advice: try to set up omniauth early.  This will allow you to have time to continue to tinker with it as you build out your app.  Also, be sure to consult the live build videos which have updated omniauth setups.  And of course, google as much as possible for a solution to your issue.  

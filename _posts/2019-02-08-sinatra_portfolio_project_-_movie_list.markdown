---
layout: post
title:      "Sinatra Portfolio Project - Movie List"
date:       2019-02-09 02:05:22 +0000
permalink:  sinatra_portfolio_project_-_movie_list
---


MY APP:
For my portfolio project, I made a simple app that keeps track of movies that users want to watch.  The app does follow CRUD: it allows users to create a list of movie entries, view their entries, edit their entries, and delete entries from their list.  Users can signup by entering their email address, creating a username and password. When they log in, they can view their list, and add and edit their list.  For now, movies have a title and  a release date.   It is a very simple app at this point that can only get better!  

THE PROCESS: 
The app has two tables: Create Movie, and Create User.  A movie entry belongs to a user, and a user has many movies.  It has three controllers: Application, User, and Movie. I started out making the app a little more complicated than it needed to be.  Initially, I had a director table and a genre table (join table) which wasn't exactly cooperating with me, so I decided to start again and keep it as simple as possible.  I found the recorded video series for the journal live build exteremely helpful!  I followed along as closely as I could to help ensure that I have the basics down.  I am still facing some bugs that I can't quite sort out at this point,  but I think it is at least a good start.  

FUTURE GOALS FOR THIS PROJECT 
There are a number of bugs that still exist.  First of all, I want the list to show the movie title and the release date.  However, the release date is currently not showing.  I have a show page which that gives users the option of seeing their list or logging out.  I want to combine the show page with the list page so that users immediately see their list when they sign in.  Additionally, the sign in feature kicks you back to the welcome page instead of loading the user list.  Once you then log in, the new user is then sent to their user list.  Not too sure why it is doing that.  

FUTURE GOALS FOR ME
In edition to cleaning up the functionality, and understanding some of these errors, one habbit that I really need to adopt is troubleshooting along the way instead of waiting for the breaks.  I need to rely on pry and tux along the way to really see if the app is doing what I want it to do.  

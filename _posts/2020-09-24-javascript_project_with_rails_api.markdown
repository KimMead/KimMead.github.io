---
layout: post
title:      "Javascript Project with Rails API"
date:       2020-09-25 01:24:42 +0000
permalink:  javascript_project_with_rails_api
---


For my Javascript and Rails API project, I created a simple app called Quote Tracker.  This app allows users to create and display quotes with a categorical attribute of motivational, inspirational, or from a friend.  Users also have the ability to delete their quotes. 

BACKEND
This app uses the fast_jsonapi gem.  There is a Quote class that belongs to a category, and a Category class that has many quotes.  The CategorySerializer has the atttribute of name, and the QuoteSerlializer has the attributes of content, category_id, and category.  The CategoriesController has index only, while the QuotesController has index, create, and destroy.   

FRONTEND
The frontend folder has html file using bootstrap.  The javascript code is split between two js files: index and quote.  The index file holds the DOMContentLoaded declaration.  It is also where the fetch calls are housed: getQuotes, postFetch (post quotes), and deleteQuotes.  The quote js file houses the quote constructor and the render quote card.  

FUTURE GOALS
I would like to add a user sign on functionality.  It wasn't necessary for this project, and I decided not to make it more difficult than I need to this time around.  I might also add an attribute of source to be able to add the name of the person associated with the quote.  I also really want to get the edit functionality to work.  I couldn't get it to work initially, but I think I have a good starting point for the code.  






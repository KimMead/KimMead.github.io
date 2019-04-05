---
layout: post
title:      "HTTP Request Verbs and the Request Cycle "
date:       2019-04-05 21:34:53 +0000
permalink:  http_request_verbs_and_the_request_cycle
---


For my Sinatra Project, I created a Movie List app that allows users to create a stored list of movies that they want to see.  Users can add to their list, edit their list, and delete movies from their list.  Below is a description of the HTTP request verbs and routes used in this app and the request cycle.  


**HTTP REQUEST VERBS**

**GET:** Loads a view.  If a user is logged in, they will be able to see their list of movies through the *get* request in the matching ‘/movies’ route in the MoviesController.  The *get* action will run the block of code and will load/render the list view. 

get ‘/movies’ do 

	if !logged_in?
		redirect to ‘/’
	else 
		@movie=Movie.all
		@user = current_user 
		
		erb :’movies/list’
		
	end 
end 



**POST:** Performs an action (such as creates/saves a new movie), and then redirects the user somewhere else (such as the movie show page for the newly created movie).

post ‘/movies’ do 

		if !logged_in?
			redirect to '/'
		end

			if params[:title] != ""
				@movie = Movie.create(title: params[:title], release_date: params[:release_date], user_id: current_user.id)


				redirect "/movies/#{@movie.id}"
			else
				redirect to '/movies/new'
				
			end
		end



**PATCH:** Acts like a POST request.  This action modifies or updates an existing entry and then redirects to somewhere else.  If a user realizes that they entered the wrong release date for a movie on their list, they can make that change which will then trigger the patch action which saves the edit, and then redirects to the movie show page with the updated information.  

patch ‘/movies/:id’ do 

@movie = Movie.find(params[:id])

	    if logged_in?
	      if @movie.user == current_user
	    @movie.update(title: params[:title], release_date: params[:release_date])
	    redirect to "/movies/#{@movie.id}"
	      else
	        redirect "/users/#{current_user.id}"
	      end
				
	    else
	    redirect '/'
			
	    end
	  end


**DELETE:** Acts like a POST request.  This action deletes an entry and then redirects to somewhere else.  If a user wants to delete a movie that they have either seen or don’t want to see, they can submit the delete request which triggers the delete action.  The movie is removed from the database, and then the user is redirected to the GET ‘/movies route which renders the updated movie list view.

delete ‘/movies/:id’ do 

@movie = Movie.find(params[:id])
	    if authorized_to_edit?(@movie)
	      @movie.destroy
	      redirect to '/movies'
	    else
	      redirect to '/movies'
				
	  end
	end

For the Movie List app, let’s say that a user wants to create a new movie to add to their list.  From their user page, the user submits a request to “add to list” by clicking the submit button.  This request matches the GET ‘/movies/new’ route which displays the create movie form.  

	get ‘/movies/new’ do 
		if !logged_in? 
			redirect to ‘/’
		else
		
			erb: ‘movies/new’
			
		end
	end 

When a user enters the movie information on the form and then submits the form, it matches the POST action route that creates the new movie (saves it to the database), and then redirects the user to the  movie show page.  


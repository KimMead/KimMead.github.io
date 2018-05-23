---
layout: post
title:      "My Pets Lab - So far...."
date:       2018-05-23 00:38:35 +0000
permalink:  my_pets_lab_-_so_far
---


I am currently working on the My Pets Lab.  I am down to 2 tests that are not passing, but I feel good about eventually getting them to pass.  Here is what I have completed so far.

CLASS Cat, Dog, Fish

There is a reason the lab points out that some attributes are only readable or writable.  For each pet class, their mood is readable and writable (can change), whereas their name attribute is readable only (can't change).  It took me a bit to make this distinction and figure it out.   Each pet class will be initialized with a name, and initialized with a mood set to "nervous."  This is the same for each pet class.  This became quite straight forward once I realized how to set up the attributes.  

class Cat
  attr_accessor :mood
  attr_reader :name

  def initialize(name)
    @name = name
    @mood = "nervous"
  end
end

CLASS Owner

This class becomes quite complicated.  Since the name and types of pets will change, these attributes are readable and writable.  The species attribute, however, is not changeable.  Furthermore, we need to keep track of all owners by creating an array.

class Owner
  attr_accessor :name, :pets
  attr_reader :species
  @@all = []
	
	For the initialize method, it is important to read the tests.  You need to create a nested hash for the different pets:
	
	def initialize(species)
    @species = species
    @@all << self
    @pets = {:fishes => [], :dogs => [], :cats => []}
  end
	
	For the buy_pet methods, these will all look the same.  The new pet will be pushed into the associated array in the nested hash:

def buy_fish(name_of_fish)
    @pets[:fishes] << Fish.new(name_of_fish)
  end
	
	As for the walk_dogs, play_with_cats, feed_fish methods, these will also look very similar.  I was running into some difficulty with figuring out exactly how to set this up, so I consulted github.  First, you must "collect" the particular species from the pet array.  Set up a conditional for each species, and change the mood to "happy."  
	
	def walk_dogs
    @pets.collect do |species, instances|
      if species == :dogs
        instances.each do |dog|
          dog.mood = "happy"
        end
      end
    end
  end
	
	I have a couple of methods to sort out, but I am confident that I can survive this lab :)  







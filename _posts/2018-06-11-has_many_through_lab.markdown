---
layout: post
title:      "Has many through lab "
date:       2018-06-12 01:39:24 +0000
permalink:  has_many_through_lab
---




I finally finished the *has many through lab* .  It seemed to take me a really long time to get through, along with several screen shares with the good people at Flatiron.  The biggest struggles that I had with this lab was really understanding the representation of *has many* and *has many through.*  I am still a little confused about these relationships, but hopefully it will make more sense as time goes by.  The second biggest issue was realizing that the order of the arguments is crucial!!!  



class Artist
  attr_accessor :name

 ...
 
  def new_song(name, genre)
    Song.new(name, self, genre)
  end
end

Be sure to check the specs to see what the order should be.  The tests will fail if not everything is sequenced correctly!!!  

I'm happy to have made it out of this lab alive.  On to the next challenge!


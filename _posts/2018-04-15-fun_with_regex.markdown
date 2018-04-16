---
layout: post
title:      "Fun with Regex!!! "
date:       2018-04-16 02:37:14 +0000
permalink:  fun_with_regex
---


Before I can leave Procedural Ruby and enter into the world of Object Oriented Ruby, I need to complete the Regex lab.  I am close, but not quite there yet.  Here are a few things I have learned so far during this lab:

1.  Use Rubular!!  Or some other site that does the same trick.  At first, I was making my way through the lab without it.  BUT, it is super helpul, and it provides you with a platform to test out your regex in real time.  

2.  Use Rubular, but remember that there might be some unexpected test fails.  I thought I needed to use parenthese in order to indicate that I wanted to capture everything within the parentheses.  In rubular, it was working just fine.  However, my test was still failing in IDE.  It was pointed out to me by that the parentheses were not necessary.  Once I removed the parentheses, test passed!  As you can see below, I removed the parentheses around un- and -ing.  That ended up doing the trick.  Not sure why, though:

def words_starting_with_un_and_ending_with_ing(text)
text.scan(/\bun+\S+ing\b/)
end

3.  In addition to Rubular, use the irb.  I have a bad habbit of not using irb.  However, it is also a helpul tool that I need to get into the habit of using regularly.  For example, I was going crazy trying to figure out how why my test was failing.  In irb, the method was returning an empty array.  Which is truthy!!  Hence, test fail.

4.  Read the test fails careully.  I made another rookie mistake by not reading the test fail carefully to see that I needed to return an array and not return true or false.  Oops :(  That took a little time to finally notice. 


I am down to one test fail, and then I am on my way.  Thank you to the helpul online support at Flatiron!!  I will be hitting you up for assistance again very soon I am sure :)  

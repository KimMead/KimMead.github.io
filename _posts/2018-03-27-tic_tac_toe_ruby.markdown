---
layout: post
title:      "Tic Tac Toe Ruby"
date:       2018-03-28 00:51:05 +0000
permalink:  tic_tac_toe_ruby
---


I thought I would revisit my Tic Tac Toe project after taking some time away from it.  I have officially completed the  project, but I thought I would go back through some of the first passes of my code, and the steps necessary for completing the game.  I’ve since refactored some of the code, but here is the initial attempt at this project. 

TIC TAC TOE RUBY 😊

Begin by creating an array of nine “empty” spaces.  The array spaces represent the Tic Tac Toe board spaces.  The array is simply called board:

board = [" ", " ", " ", " ", " ", " ", " ", " ", " "]

Next, we need to store the win combinations – the series of spaces that can be occupied by the same character that will win the game.  There are a finite set of these combinations based on a 3 x 3 board.  We can store these win combinations as a constant in a nested array:

WIN_COMBINATIONS = [
  [0, 1, 2],
  [3, 4, 5], 
  [6, 7, 8],
  [0, 3, 6],
  [1, 4, 7],
  [2, 5, 8],
  [0, 4, 8],
  [2, 4, 6]
  ]
Our arrays are ready, so now we need to create an actual Tic Tac Toe board that will print out. In this method, each space is referenced to a space in the array.  Therefore, we need to start counting at 0:
 
 def display_board(board)
  puts " #{board[0]} | #{board[1]} | #{board[2]} "
  puts "-----------"
  puts " #{board[3]} | #{board[4]} | #{board[5]} "
  puts "-----------"
  puts " #{board[6]} | #{board[7]} | #{board[8]} "
end

When a player provides input (enters a space number they want their token to occupy), the input will be referencing an array space.  Since the player will be entering their input based on spaces 1-9 (not 0-8), we need to create a method that will transform the input to the referenced array space.  This method will take an input argument:

def input_to_index(input)
  input.to_i - 1
end

The space that a player chooses will be filled by a player token.  The player token will either be an ‘X’ or an ‘O’.  We will need a method for this as well:

def player_token
  player_token = "X" || "O"
end

Now, things start to get interesting…and frustrating.  When I refactored my code for the @class lab later on, some of my methods had to be essentially rebuilt.  That might be another blog post.  This represents my first pass at it.  With that being said, here comes the #move method!  This method will take 3 arguments – board, index, and the player_token.  The player_token will equal the board[index] since that is where we want the token to “move”:

def move(board, index, player_token)
  board[index] = player_token
end

To prevent players from essentially taking over an already occupied spot, we need to define a method that will check to see if a position is taken on the board.  Again, this method will take board and index as arguments:

def position_taken?(board, index)
  if board[index] == "" || board[index] == " " || board[index] == nil 
    false 
  else 
    true 
  end
end

Our game will also have to determine whether the input from the player is in fact valid (referenced to the board array between 0-8).  It will also check whether the position is already taken:

def valid_move?(board, index)
  if index.between?(0, 8) && !position_taken?(board, index)
    true
  else
    false
  end
end

The #turn method relies on several methods.  This method prompts the player to select a space on the board, but then must rely on the #move method and #valid_move? method to ensure that players can enter a valid move, and that the board is turned over to the next player once a valid move is entered.  The #turn_count method then tracks the number of turns:

def turn(board)
  puts "Please enter 1-9:"
  i = gets.strip
  index = input_to_index(i)
  m = valid_move?(board, index)
  if m == true
    move(board, index, player_token)
  else m == false
    until m == true
    puts "Sorry, that was an invalid move.  Please enter 1-9:"
    i = gets.strip
    index = input_to_index(i)
    m = valid_move?(board, index)
    move(board, index, player_token)
  end
end
display_board(board)
end

def turn_count(board)
  counter = 0 
  board.each do |turn|
    if turn == "X" || turn == "O"
      counter += 1 
    end 
  end
  counter
end

There are 2 outcomes of the game: someone wins, or there is a draw.  To determine a winner, we need to refer to our win combinations.  The method must pass over each combination and return a winner:

def won?(board)
    WIN_COMBINATIONS.each do |win_combination|
      win_index_1 = win_combination[0]
      win_index_2 = win_combination[1]
      win_index_3 = win_combination[2]
      
      position_1 = board[win_index_1]
      position_2 = board[win_index_2]
      position_3 = board[win_index_3]
      
      if position_1 == "X" && position_2 == "X" && position_3 == "X" || position_1 == "O" && position_2 == "O" && position_3 == "O"
        return win_combination
      end
    end
    false
  end
  
We must also determine whether there is a draw (a full board with no winner).  

def full?(board)
    if board.all? {|i| i == "X" || i == "O"}
      return true
    end
  end
  
  def draw?(board)
    if !won?(board) && full?(board)
      return true
    end 
  end

Last but not least, we have the #play method.  This method also takes board as an argument, and calls on other methods.   This method will also congratulate the winner, or call a draw:

def play(board)
  play = 0
  input = gets
  until over?(board)
  turn(board)
end 
  if won?(board)
  winner(board) == "X" || winner(board) == "O"
    puts "Congratulations #{winner(board)}!"
  else draw?(board)
  puts "Cat's Game!"
end
end

I’m pretty proud of myself for making it this far.  It was not simple task, and even though there are still a lot of errors and refactoring needed, it feels good to have done this much!







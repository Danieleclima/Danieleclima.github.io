---
layout: post
title:      "My first AI algorithm"
date:       2020-03-14 18:17:32 +0000
permalink:  my_first_ai_algorithm
---

Before I joined the sofware engineering bootcamp, an algorithim to me only meant a rather extrange concept that only big companies the likes of Google or Facebook could afford to implement. This is why when I read the title of the Tic Tac Toe With AI lab, I thought that it was going to be something completely out of my league. On top of that, my Ruby skills were a bit rusty since I had just finished my final project so I had to refresh my memory given quite a few concepts were blury in my mind.

Luckily It just took me a couple days to warm up and get to my previous Ruby level, but once I was up to speed, I noticed that it was all on the back of my mind waiting to come back. I basically had to develop a CLI gem to be able to play Tic Tac Toe against the computer or versus another player, also the computer was supposed to be able to play again itself. I had to create a player module which contained two classes: Human and Computer. The Human model was relatively easy to set up however the Computer class needed to be capable to play on its own using some sort of strategy, this is when my algotrithm came in:

```
module Players
class Computer < Player
      
    def move(board)
        if !board.taken?(5)
        computer_move = 5
        else
        computer_move = rand(1..9)
        end

        if board.valid_move?(computer_move)
            computer_move.to_s
        else
            self.move(board)
        end
    end
    
end
end
```

The logic behind it is rather simple, the computer will always check if the middle position of the board is occupied and if empty it will always make a move to occupy that position which should make the game harder to play for its opponent, after that, all the subsequent moves are completely random. I know I could have complicated things way more but for my first AI project it felt right to implement this logic and leave it at that for now. Next time I develop an algorithim I will always remember how I developed my first AI lab!



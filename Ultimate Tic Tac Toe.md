From my perspective, this was a very important and rewarding exercise as I taught myself to do my first ever search algorithm: Minimax.

The game of choice was Ultimate Tic Tac Toe. Rules summarised here:


https://en.wikipedia.org/wiki/Ultimate_tic-tac-toe

Game found here:


https://www.codingame.com/ide/puzzle/tic-tac-toe

I didn't really know where to begin, so I began looking for tutorials on this sort of thing and found one on Kaggle which was perfect:


https://www.kaggle.com/learn/intro-to-game-ai-and-reinforcement-learning

This took me through the steps of what Minimax was and how it worked on a sufficiently similar game: connect four.

Once I understood and implemented Kaggle's boiler plate cut and stick to make it work style tutorial on connect four, I set about building the analogous code necessary for Tic Tac Toe.

I started by pasting over my connect four minimax and then changing things to make them fit, and intuitively it became clear when I'd need a new helper function specific to this game, and what a sensible heuristic scoring system would be and so on.

The hard part was getting the minimax to appropriately simulate future game states - my first shot at this had multiple bugs which took me a while to spot (when you've bashed out 300 lines of code guessing at how something you've never built before 'should work' this is inevitable I feel, and all part of the process. 'Good for the soul' is how my old mathematical methods lecturer would describe it.)

After a tremendous amount of staring at each line and finding around 5 absolutely massive bugs which revealed why my future game state simulation wasn't working properly, I believe it is now doing what I want it to do, executing a minimax search algorithm.

Python may not be the best language to do this in, and it's possible there remain some bugs. The current computational limits are that i seem to only be able to look 2 moves ahead (sometimes 1).

Fixing these bugs and having a working and accurate Minimax search algorithm took me to rank 10 of Silver. 

Sticking in Python, i then turned my attention to the heuristic function. I found some interesting sources, but this one gave a good outline of the type of heuristic function I could implement:

https://www.cse.huji.ac.il/~ai/projects/2013/UlitmateTic-Tac-Toe/

Having spiced up my heuristic function (which I had not paid any mind to until now, I was previously much more focused on getting the search to work!) - we tipped the balance and got into gold! Currently sat around rank 400 overall, the next step would be to tweak the heuristic function further.

For now I am happy with the fact I have taught myself a new skill and implemented it proving to myself I can do it. I was pleased looking back over my code at how eventually it looked absolutely nothing like the connect 4 code I wrote and took from Kaggle, which makes me feel like I have properly understood this search method and built something all of my own.

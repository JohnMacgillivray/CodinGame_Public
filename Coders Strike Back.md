This was my first time doing anything like this, writing a script for an AI to play a game against other AIs. The game I chose was 'Coders Strike Back' - a racing game. The overall premise is simple: You get told information about the game state, you take a 'turn' telling your pod or pods what to do in the next turn. Make it to the end of the race first or break your enemy's pods to win!

https://www.codingame.com/multiplayer/bot-programming/coders-strike-back

Here are a couple of clips of my script in action:

https://www.codingame.com/replay/454700221

https://www.codingame.com/replay/454699289

The difficulty and rules were built up in a very sensible way by the league system, breaking it down into manageable steps. Whilst there are a diverse range of effective solutions, for fun I wanted to see if I could make a good bot with heuristics alone. Whilst it will definitely be a good exercise at some point to implement all the algorithms that might work here, part of the challenge or fun for me was working out the physics of what would and wouldn't work, and then proving myself right (your code gets pitted against other people's code, I find this PVP element very entertaining).

I will note that the shield function and the boost function are quite naive and could probably be improved, I just built simple and intuitive functions and they worked, and any deviations from them were worse, so I kept them! Outside of these 5 key breakthroughs, there was also a lot of tweaking of parameters and scaling factors to find the sweet spots whilst I agonised over what the next insight would be that made me jump up in score instead of creep up.

The key insights were as follows, in order of discovery (I gained these by either thinking about the problem or by watching other bots and gaining glimmers of what they might be doing by observing their behaviour and inferring).

1)The cosine function relating Thrust and Angle. Pretty simple really, but at the time this was a big breakthrough - I initially didn't even know where to begin when considering this problem and this was the first time I managed to think of something that would be an improvement and how to implement it and it worked. Baby steps.

2)Offset the runner destination from the next checkpoint by a multiple of their current velocity

3)When the runner is close to the current checkpoint/goal, be forward-looking and start aiming for the subsequent checkpoint

4)I reached a point where I was in the top 10 of Gold, but still not able to consistently beat the best players in the league. It was at this point I decided to switch from having 2 runners to 1 runner and 1 blocker. This slightly infuriates me still, because the Gold Boss itself is a 2 runner script only with no blockers and clearly runs on heuristics, so it almost felt like admitting defeat that I couldn't write a 2 runner heuristic script that beat the Gold Boss!

5)The first part of a blocker was simple enough: Aim for the furthest ahead enemy unit, aim slightly ahead of them taking into account velocities of you and them etc.. What made this blocker so effective and allowed me to achieve legendary status was that when they are close to their next checkpoint, stop aiming for them and instead aim for their subsequent checkpoint after that one. This naturally meant that once they hit their checkpoint and their goal checkpoint moved on, they would be far enough away from their target checkpoint that the blocker would stop moving towards the subsequent checkpoint and aim back at the enemy pod, and when we did so, we would typically be either directly between them and their next destination leading to a head on collision, or at an interesting angle where we can shunt them and make them completely miss their next checkpoint.

So there you have it, the story so far. It is a great game, and I found it really interesting and rewarding to unlock secrets of how to write a good racer script and testing and checking things and gaining insight and thinking about the problem at hand, and then coming up with good ways to implement your insights in code.

Having reached legendary, even without having taken into account the new rules and uplifted thrust limit of 200 not 100, I was rank 595. By changing parameter values alone and without adding new functions, the script reached rank 361 (not bad given the total pool of players is ~97,000). This heuristic python3 implementation is relatively intuitive and is well under 100 lines of code with comments stripped out. In time, will see what the next step is and how far the heuristic model can go. I might also try a genetic algo.

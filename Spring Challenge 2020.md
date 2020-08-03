Game available to play here:
https://www.codingame.com/multiplayer/bot-programming/spring-challenge-2020
Final Ranking: 47 Legend
https://www.codingame.com/contests/spring-challenge-2020/leaderboard/global
Post Competition Forum
https://www.codingame.com/forum/t/spring-challenge-2020-feedback-strategy/184113/37
Post Competition Blog
https://www.codingame.com/blog/spring-challenge-2020/

This was my first ever competition of this type, having stumbled upon CodinGame about 3 weeks ago (since then I have obsessively built bots for some of the older competitions.) When I first started this competition I did well with a quick and lazy approach on the opening day, but over time as people started building better bots, my rank started slipping and I essentially lost motivation. I had some ideas of what I could do but not the confidence or willpower to try and get it to work and keep trying until it worked, and I couldn’t see exactly how to implement it, there were some gaps missing in my mental image of what I wanted to do. That all changed when my friend, Jarcan, joined the competition. He had some good ideas and I could see what I could do if i used some of his ideas, but it felt like my bot would simply be a cheap imitation of his bot. On wednesday night when I had pretty much given up the contest and was rank ~600, Jarcan encouraged me that my implementation would be sufficiently different, there was still time in the contest and there was still lots of room for improvement. Thursday morning idk what came over me but I built the bot. By 2am Saturday I was rank 30. It was a furious 2 days of bashing out code and theory crafting and trying things and failing and then sometimes improving. I couldn’t have done it without Jarcan - he connected dots for me I would not have otherwise seen and enabled me to have the additional insights I had that got me here. The strategy went like this:

Find the shortest paths between all points on the map and store them - this was what I had had a lot of trouble with on my own, finding a way to do this without timing out. Jarcan came up with a pruned floodfill approach using hashmaps which did the job nicely. This was the first big step.

Every turn, for each of your pacs, look through all available paths for that pac and score them with a heuristic function - this infact was not all possible paths but a pruned list of squares deemed worth re-visiting. This scoring function had several layers to it. The heuristic function had a lot of insight baked into it - but here is a brief summary:
a) don’t walk into enemy pacs that can kill you or go on same paths as allied pacs
b) eat pellets with 4 priority layers: super pellets, pellets you can see this turn, pellets you have recently seen, squares you have not yet visited and which might contain pellets. The weightings of these categories were scaled with how far into the path youre considering you are as well as having weights updated by game state dependent information each turn.

taking guaranteed kills - when you could see an enemy pac that was trapped and it had no cooldown to switch and you could definitely kill it, do so. this was done using our handy dandy path dictionary again.

switch in the shadows - the absence of information available to the enemy is a great weapon, they cannot help but bump into you or meet you at junctions from time to time, and they have no way of knowing what type your pacs are if you switch when they cannot see you. Further it would be very difficult to counter such a strategy, as you’d then get it wrong if you’re against someone who doesn’t switch in the shadows. In short - track enemy pac types and last seens, when they’re all the same type/2 types, there is an objectively strongest type your pacs should be - so switch to it. There was also some very basic switching logic for particular situations when it was likely a good idea to switch.

But there you have it - a heuristic bot which looks at paths available to each pac and picks the best one based on a scoring system, along with an override of some switching and going for kills here and there. 500 lines of code, but a lot of that is comments or now obsolete code, so this could probably be trimmed down to under 400 lines.

Thanks to CG for this fun challenge - and thanks for bringing me and my old friend together again - it felt like we were 18 again bouncing ideas off each other and discussing theories together.

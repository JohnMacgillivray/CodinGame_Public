Very Hard Puzzle: Music Scores

This is a high level explanation of the approach I took to solving the below problem:

https://www.codingame.com/training/expert/music-scores

I gained significant insight into how to solve this problem by carefully reading Cyber Lemonade's blog on how he solved this problem:

https://www.codingame.com/blog/puzzle-image-processing

There were to main elements I took from this blog: 

1) the key to unlocking all the various dimensions you need is to start with the leftmost black pixels as they are the stave, and everything else is unlocked from there

2) perform a sweep across the image from left to right processing 1 note at a time

Here is the 'from scratch' approach I took, step by step:

A) the image is given in Run-Length Encoding format

e.g. W 20 B 200 means if you were to begin reading off the colour of each pixel on the image from left to right and then going to the next line, the first 20 pixels are white and the next 200 pixels are black

First, I 'unpacked' this image data to generate a 2D array of 1s and 0s (1 for black, 0 for white) - as this meant I could manipulate and interact with the date much more easily

B) as Cyber Lemonade guided in their article, we can then get the following by looking at the left most black pixels in the image:

  i) stave bar 'thickness'
  
  ii) note height
  
  iii) the height of each stave line in pixel co-ord terms (this will be used later to identify the pitch of a given note)

C) Note width (from left to right):

  We can perform a search from left to right checking for each vertical column of pixels after the start of the stave to see whether they match an empty stave or not - we can then take these contiguous blocks of anomalous columns to be notes, which gives us not only the note widths, but the start and stop x co-ords of every note.
  This was annoying in the sense that you can't only look for anomalous vertical columns of pixels which differ from the default white space with 5 black bars - you have to take into account the fact that you can get the start of the low C black line - which isn't yet technically the note, so you have to add in a catch here to make sure the vertical column is different from both whitespace with 5 black bars AND whitespace with 6 black bars.

D) The pitch of each note

Now that for every note we have its starting and ending horizontal co-ordinate, to get the pitch we simply jump to the middle of the note in terms of x-coordinate, and very similar to the horizontal search method, establish the contiguous block of pixels in the vertical column where the centre of the note is where that pixel does not match an empty stave with 5 black lines. From here, we take the data from B)iii) and build a simple function to establish what the note's pitch is based on the vertical coordinate of the note's midpoint relative to the 5 black staves 
I will add that this actually had to be modified slightly to get around the 1 pixel high note lines edge case where you would miss the note entirely if you look directly down the middle of the note - so infact I deliberately looked just slightly off from the horizontal midpoint of the note when doing the vertical column scan to check for differences from the empty stave

E) The duration of the note

This was relatively straightforward given the simplified notation in the problem: we already have the central x,y coords of each note - so all we do is check what colour that pixel is: white means H, black means Q.

I really enjoyed this problem because it was a composite of lots of sub-problems: no individual step was particularly difficult, the difficulty was seeing what set of relatively simple steps/computations/manipulations to take. It's a different kind of difficulty from 'spot the pattern for this dynamic programming', it's about spotting a series of insights which all when put together get you where you want to go. 

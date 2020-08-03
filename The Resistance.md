Very Hard puzzle: The Resistance

This is a high level explanation of the approach I took to solving the below problem:

https://www.codingame.com/training/expert/the-resistance
    
This is a difficult problem. 

My first thought was that I have done a problem similar to this in the past, available here:

https://leetcode.com/problems/word-break-ii/
    
This is not exactly the same, as this required you to return the different combinations of words you could make, not the number of them.

However, what I recalled was that although I solved this slightly easier variant with recursion, I was aware of an alternative approach using dynamic programming.

Further, given we only need to find the number of different combinations, not keep track of the list of them, the dynamic programming approach was clearly the best approach here.

I will add that the final 'flurry' at the end to make this dynamic programming approach work in 'the-resistance' was to keep in mind that we have to use a dictionary of morse code to process the different English words before we begin looking at potential matches of substrings.

Further, it is vital to keep track, for each string of morse code present in our translated dictionary of english words, how many duplicates there are once you've translated them into morse code.

My approach was to initially process all the English words by translating them into morse, and then adding that morse string to a dictionary of lists:

the list it got added to was keyed by the length of that string. This all helps for setting up the dynamic programming later (you may be able to see where I am going with this already!).

From here, the wonderful pattern which breaks this problem is that for X many ways you can build a string of length N, for any word in your dictionary of lists, if that appended to the length N string would STILL match the morse string we were originally given up to N+K, where K is the length of the new word we've picked from our dictionary:

Then you have found a 'branch' of possible solutions up to length N+K, with X*Z different possible combinations (where Z equals the number of times the morse string of length K occurs in our dictionary).

In dynamic programming, you can loop through the length of the original morse string once and populate a dynamic programming array building up branches and combinations as you go.

Without trying to make it artificially short, this is around 20 lines of code, and it is simple, beautiful and elegant.

Credit to CodinGame and the creators for such an interesting problem, it felt very rewarding when it all clicked into place and I passed all the test cases!

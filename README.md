Task 1: finding similar words

Input:
`
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='weapons'
`

$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='weapons'
INFO:root:rank=0 pagerank=0.004571518860757351 url=www.lawfareblog.com/why-did-you-wait-moral-emptiness-and-drone-strikes
INFO:root:rank=1 pagerank=0.0031107424292713404 url=www.lawfareblog.com/dc-district-court-dismisses-journalists-drone-lawsuit
INFO:root:rank=2 pagerank=0.0020231129601597786 url=www.lawfareblog.com/revived-cia-drone-strike-program-comments-new-policy
INFO:root:rank=3 pagerank=0.0019667143933475018 url=www.lawfareblog.com/us-court-appeals-dc-circuit-dismisses-suit-over-us-drone-strike
INFO:root:rank=4 pagerank=0.001178761012852192 url=www.lawfareblog.com/iran-shoots-down-us-drone-domestic-and-international-legal-implications
INFO:root:rank=5 pagerank=0.0011619674041867256 url=www.lawfareblog.com/slaughterbots-and-other-anticipated-autonomous-weapons-problems
INFO:root:rank=6 pagerank=0.0011276121949777007 url=www.lawfareblog.com/german-courts-weigh-legal-responsibility-us-drone-strikes
INFO:root:rank=7 pagerank=0.0008373793680220842 url=www.lawfareblog.com/shift-jsoc-drone-strikes-does-not-mean-cia-has-been-sidelined
INFO:root:rank=8 pagerank=0.0007856971933506429 url=www.lawfareblog.com/waiving-imminent-threat-test-cia-drone-strikes-pakistan
INFO:root:rank=9 pagerank=0.0007412837585434318 url=www.lawfareblog.com/drone-strike-errors-and-hostage-tragedy-mapping-issues-newly-catalyzed-debate
Notice that most of these articles do not mention the word "weapons", but instead mention the word "drone".

NOTE:

Your numbers and order of results will likely be slightly different. That's okay as long as they're reasonable. For example, you should be returning some results that do not contain the search word, but contain related words.

HINT:

The easiest way to implement this task is to modify the url_satisfies_query function so that it calls gensim's most_similar function on each of the input query words, and returns True if any of those words are in the list. I recommend using only the 5 most similar words, as the words quickly become fairly unrelated.

Task 2: ranking with word importance
There are several problems with the method above for including similar words in our search results. For example:

Some words have lots of very similar words. Consider the most similar words for the search "biden":

>>> vectors.most_similar('biden')
[('hillary', 0.9419968128204346),
 ('christie', 0.9419272541999817), 
 ('romney', 0.9377604722976685), 
 ('potus', 0.9371991157531738), 
 ('reid', 0.9328151345252991), 
 ('boehner', 0.9311597347259521), 
 ('clinton', 0.9253027439117432), 
 ('clegg', 0.9072402119636536), 
 ('miliband', 0.9010352492332458), 
 ('zimmerman', 0.8950174450874329)
 ]
All of the results above are more similar to "biden" than any word is to "weapons". So if we are only looking at the top5 words for everything, then some words will get much better matches than others. It would be better to have an adaptive method that can automatically determine the top number of query results to use.

If someone is searching for "weapons", we should probably weight articles about weapons higher than articles about "drones", and we should rank articles about both "drones" and "weapons" the highest. Our previous method ranks all of these results equally.

One simple method for fixing both of these problems to define a query_score for each webpage in addition to the pagerank score pi. This query_score would be a real number that depends on both the query and the article's text, and would be high whenever the query and text are related to each other. Then the webpage's ranking would be defined by:

ranking = pi * query_score
Instead of only by the pagerank pi.

There are many possible ways to define the query score. For example, if we define the query_score to be 0 when url_satisfies_query returns False and 1 when it returns True, then this algorithm reduces to the previous algorithm.

A better method is to use the similarity scores using the following pseudocode:

score = 0
let S be the set of words similar to the query string
for each word in S:
    let n be the number of times word appears in document
    let word_similarity be the similarity score of word
    score += n * word_similarity**p
By adjusting the p hyperparameter, we can control how important the word similarities must be. A typical p value would be between 30-60, since this will result in scores roughly on a similar scale as the pagerank vectors. You should hard-code this value to something that you think gives reasonable results.

NOTE:

The optimal value for p will depend on the particular word embeddings you select. In real world search engines, the optimal value would be learned from the data. We would set up a classification problem where the output variable Y to be predicted is whether or not a user clicks on one of the links provided, and the input variable X would be the search term. The hypothesis class would be the pseudo-code you've written above with p as the only parameter to be learned. Then you can use gradient descent to solve for p.

You won't have to do this. It is hard to implement because this is a non-standard hypothesis class not found in libraries scikit-learn, and acquiring reasonable training data is difficult for companies not already operating large-scale search engines.

Google uses classification problems like this internally all over their search engine. When Google was first founded, it was common to hear people saying "Google uses machine learning the way Microsoft uses the if statement." Now all the major tech companies have machine learning problems like this internally that they are solving, so people don't say this anymore.

Task:

Implement the "better method" described above. You will have to modify the WebGraph.search function so that it implements the pseudocode described above, and orders documents according to the ranking score instead of according to pi.

Task 1: finding similar words

Input:
`
$ python3 pagerank.py --data=./lawfareblog.csv.gz --search_query='weapons'
`

Output:
```
INFO:gensim.models.keyedvectors:precomputing L2-norms of word weight vectors
INFO:root:rank=0 pagerank=0.004571518860757351 url=www.lawfareblog.com/why-did-you-wait-moral-emptiness-and-drone-strikes
INFO:root:rank=1 pagerank=0.0031107424292713404 url=www.lawfareblog.com/dc-district-court-dismisses-journalists-drone-lawsuit
INFO:root:rank=2 pagerank=0.0020231129601597786 url=www.lawfareblog.com/revived-cia-drone-strike-program-comments-new-policy
INFO:root:rank=3 pagerank=0.0017029385728102938 url=www.lawfareblog.com/donald-trump-and-politically-weaponized-executive-branch
INFO:root:rank=4 pagerank=0.001178761012852192 url=www.lawfareblog.com/iran-shoots-down-us-drone-domestic-and-international-legal-implications
INFO:root:rank=5 pagerank=0.0011619674041867256 url=www.lawfareblog.com/slaughterbots-and-other-anticipated-autonomous-weapons-problems
INFO:root:rank=6 pagerank=0.0011276121949777007 url=www.lawfareblog.com/german-courts-weigh-legal-responsibility-us-drone-strikes
INFO:root:rank=7 pagerank=0.0009182740192837191 url=www.lawfareblog.com/week-military-commissions-98-session-kangaroo-lapel-pin-edition
INFO:root:rank=8 pagerank=0.0007856971933506429 url=www.lawfareblog.com/waiving-imminent-threat-test-cia-drone-strikes-pakistan
INFO:root:rank=9 pagerank=0.0007412837585434318 url=www.lawfareblog.com/drone-strike-errors-and-hostage-tragedy-mapping-issues-newly-catalyzed-debate
```

Task 2: ranking with word importance

Input:
`
python3 pagerank.py --data=data/lawfareblog.csv.gz --search_query='weapons'
`

Output:
```
INFO:gensim.models.keyedvectors:precomputing L2-norms of word weight vectors
INFO:root:rank=0 pagerank=9.102928375628129e-09 url=www.lawfareblog.com/donald-trump-and-politically-weaponized-executive-branch
INFO:root:rank=1 pagerank=9.100283748275636e-09 url=www.lawfareblog.com/dc-district-court-dismisses-journalists-drone-lawsuit
INFO:root:rank=2 pagerank=8.284769709338576e-09 url=www.lawfareblog.com/update-military-commissions-big-september-911-case
INFO:root:rank=3 pagerank=7.019284727575627e-09 url=www.lawfareblog.com/slaughterbots-and-other-anticipated-autonomous-weapons-problems
INFO:root:rank=4 pagerank=6.486902929488576e-09 url=www.lawfareblog.com/why-did-you-wait-moral-emptiness-and-drone-strikes
INFO:root:rank=5 pagerank=6.103993857678298e-09 url=www.lawfareblog.com/week-military-commissions-98-session-kangaroo-lapel-pin-edition
INFO:root:rank=6 pagerank=6.394069381828495e-09 url=www.lawfareblog.com/revived-cia-drone-strike-program-comments-new-policy
INFO:root:rank=7 pagerank=6.049686728193848e-09 url=www.lawfareblog.com/court-military-commissions-review-upholds-life-sentence-al-bahlul
INFO:root:rank=8 pagerank=4.949629102938577e-09 url=www.lawfareblog.com/georgetown-laws-comprehensive-foreign-intelligence-law-collection
INFO:root:rank=9 pagerank=3.101746689102938e-09 url=www.lawfareblog.com/waiving-imminent-threat-test-cia-drone-strikes-pakistan
```

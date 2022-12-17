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
python3 pagerank.py --data=data/lawfareblog.csv.gz --search_query='biden' --s_weight=.01
`
Output:
```
INFO:gensim.models.keyedvectors:precomputing L2-norms of word weight vectors
INFO:root:rank=0 pagerank=0.02051282301545143 url=www.lawfareblog.com/new-obama-biden-campaign-bumper-sticker
INFO:root:rank=1 pagerank=0.0109577476978302 url=www.lawfareblog.com/trump-encourages-china-investigate-biden-family-clouding-trade-talks
INFO:root:rank=2 pagerank=0.010501262731850147 url=www.lawfareblog.com/live-brookings-host-vice-president-joe-biden
INFO:root:rank=3 pagerank=0.005239618942141533 url=www.lawfareblog.com/document-trump-revokes-obama-executive-order-counterterrorism-strike-casualty-reporting
INFO:root:rank=4 pagerank=0.00207848334684968 url=www.lawfareblog.com/obamas-term-end-thoughts-targeted-killing
INFO:root:rank=5 pagerank=0.0009015162941068411 url=www.lawfareblog.com/thoughts-about-obama-administrations-counterterrorism-paradigm-light-al-liby-and-ikrima-operations
INFO:root:rank=6 pagerank=0.000671088753733784 url=www.lawfareblog.com/president-obama-secures-final-senate-vote-necessary-defend-iran-deal
INFO:root:rank=7 pagerank=0.0006702161044813693 url=www.lawfareblog.com/obamas-moral-muse
INFO:root:rank=8 pagerank=0.0006524198688566685 url=www.lawfareblog.com/obamas-legacy-law-transparency-and-politics-anguish
INFO:root:rank=9 pagerank=0.0006270432495512068 url=www.lawfareblog.com/speaking-law-obama-administrations-addresses-national-security-law
```

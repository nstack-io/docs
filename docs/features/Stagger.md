---
currentMenu:  features-stagger
---

# Stagger
>#### Stagger has been removed and is no longer available in NStack!

(S)mart Tagger

New in 2.3.0

A feature to find a "tag" in a text (feedback / bug) via machine learning (NLP) 

**Use cases:**

Very handy to categorize big amounts of user feedback. Stagger is implemented in the "Feedback" module

**Usages**

Stagger takes a text as input 

* The tags are only for bug reports / feedbacks. So do not try to use it on other cases 
* The first call to Stagger will be slow (15-20s wait) while Lambda spins up. 

### Output

Stagger outputs 3 things:

1) Detected language

2) Translated text (to english)

3) Tag


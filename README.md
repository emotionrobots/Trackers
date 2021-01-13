# Trackers
`Tracker.py` is a generic object tracker; that means it can be used to track any Python objects.

Fundamentally, tracking is about matching and assigning newly encountered object instances to old object instances.  The user is responsible for providing the function `scoreFunc(a, b)` that scores how well object instance `a` and `b` matches.  Lower the score, better the match.  

The actual match is performed by `Matcher()`, implemented in `Matcher.py`.  The `Matcher.match()` function calls the user-supplied `scoreFunc()` and returns three values:  `matchedPair`, `unmatched_a`, and `unmatched_b`.

The class implements basically two public functions:
- match()
- scoreFunc()

User of the Tracker() class can override the scoreFunc()


## Inheritance
The included blobTracker.py shows how Tracker can be extended through class inheritance.

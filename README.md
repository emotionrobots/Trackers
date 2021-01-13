# Generic Object Tracker
This repository implements a generic object tracker. The tracker can be used to track any Python objects. Tracker maintains a time history for each object, therefore it can be used to track movement of targets.  

The repo implement three classes, each in a separate Python file.

`Matcher.py`     - implements `Matcher()`, a generic object matcher.
`Tracker.py`     - implements `Tracker()`, a generic tracker for tracking any given object
`blobTracker.py` - implements `BlobTracker()`` using `Tracker()`

## Matcher
Fundamentally, tracking is about matching and assigning newly encountered object instances to old object instances.  The user is responsible for providing the function `scoreFunc(a, b)` that scores how well object instance `a` and `b` matches.  Lower the score, better the match.  

The actual match is performed by `Matcher()`, implemented in `Matcher.py`.  The `match()` function calls the user-supplied `scoreFunc()` and returns three values:  `matchedPair`, `unmatched_a`, and `unmatched_b`.

`matchedPair` - a list of `(a, b)` that have been matched given `scoreFunc()`
`unmatched_a` - a list of remaining `a` that have not been matched
`unmatched_b` - a list of remaining `b` that have not been matched

## Tracking
User of the Tracker() class can override the scoreFunc()


## Inheritance
The included blobTracker.py shows how Tracker can be extended through class inheritance.

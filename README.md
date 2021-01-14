# Generic Object Tracker
This repository implements a generic object tracker. The tracker can be used to track any Python objects. Tracker maintains a time history for each target, therefore it can be used to track movements, or path.  

This repo contains three classes, each in a separate Python file.

* `Matcher.py`     - implements `Matcher()`, a generic object matcher.
* `Tracker.py`     - implements `Tracker()`, a generic tracker for tracking any given object
* `blobTracker.py` - implements `BlobTracker()`` using `Tracker()`

## Matcher
Fundamentally, tracking is about matching and assigning newly encountered object instances to old object instances.  The user is responsible for providing the function `scoreFunc(a, b)` that scores how well objects `a` and `b` match.  Lower the score, better the match.  

The actual match is performed by `Matcher()`, implemented in `Matcher.py`.  The `match()` function calls the user-supplied `scoreFunc()` and returns three lists:  `matchedPair`, `unmatched_a`, and `unmatched_b`.

* `matchedPair` - a list of matched pairs `(a, b)`
* `unmatched_a` - a list of unmatched `a`  
* `unmatched_b` - a list of unmatched `b`  

## Tracker
While `Matcher()` can match any two objects when given a `scoreFunc(a, b)` that knows how to score the match between two objects of the same type, it does not maintains a trace of past matches.  The `Tracker()` class does. The `Tracker()` class inherits from `Matcher()` but also maintains a trace of matches.  

There are three possible matching scenarios:

* Number of traces = number of objects --> Every object assigned to a trace
* Number of traces > number of objects --> Delete/clear unmatched trace
* Number of traces < number of objects --> Create new trace

These three cases are illustrated in the image below:

![alt text](https://github.com/emotionrobots/Trackers/blob/main/assets/matches.png)

## BlobTracker
User of the `Tracker()` class can override the `scoreFunc()` and define their own tracker.  The `BlobTracker()` included with this repo demonstrate exactly this.  The `BlobTracker()` is a tracker that knows how to match and track OpenCV blobs.
`blobTracker.py` also shows how `Tracker()` can be extended through class inheritance.

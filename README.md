An OpenRefine reconciliation service for [FAST](http://www.oclc.org/research/activities/fast.html?urlm=159754).

>FAST is available as Linked Data, which is an approach to publishing data which enhances the utility of information on the web by making references to persons, places, things, etc. more consistent and linkable across domains.

The service queries the [FAST AutoSuggest API](http://www.oclc.org/developer/documentation/fast-linked-data-api/request-types)
and provides normalized scores across queries for reconciling in Refine.

Run locally as:
~~~~
$ python reconcile.py --debug
~~~~

Michael Stephens wrote a [demo reconcilliation service](https://github.com/mikejs/reconcile-demo) that this code is based on.

## Changes for this Fork

Instead of the 'score' variable bringing back the relevance score of terms, I instead changed this to bring back the MARC field of the terms the API suggests.  

It was necessary to change 'score' because the extension currently only allows for a static number of variables, and 'score' was the least useful for our purposes.  

The MARC field tag helps us determine what 'type' of terms we are dealing with, and even if we don't choose to use the FAST heading, we can organize them to reconcile to different sources like GeoNames, VIAF, etc.  

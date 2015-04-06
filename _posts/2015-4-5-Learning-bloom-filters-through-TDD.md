---
layout: post
title: Learning bloom filters through TDD
---

Bloom filters are a valuable data structure that can help reduce costly lookups 
by determining if a value likely exists in some sort of storage.  The usage
cases of these filters might include protecting a database, a networked resource
of some kind, helping to prevent denial of service attacks, or really any data
structure where the 'contains' call has a time complexity that isn't constant.  
  
I use the word likely because a bloom filter cannot tell you for sure if an 
entry exists in a database, as it can return false positives.  However, a 
properly maintained bloom filter will never return a false negative.  In other
words, a bloom filter may sometimes tell you something exists when it actually
doesn't, however it will never tell you that something doesn't exist when it 
actually does.  
  
So how are these filters implemented and what do the underlying data structures
look like?  In reality a bloom filter uses multiple hashing functions on a 
queried entry which point to an array of boolean values.  When entries are
being added to the bloom filter, these hashing functions each hash the entry
independently and the boolean entries at the index of the hashed values are 
set to true.  If the entry in the bloom filter for that index is already true,
then that entry isn't changed.  
  
When the filter is actually being queried for the presence of an entry, that
entry is hashed as well by these hashing functions.  The filter then gets the 
values at the indexes on the boolean array, and if those values aren't set to
true, then the filter knows there is no way that entry exists within the
protected resource.  However, if the boolean values at those indexes all happen
to be true, then the filter knows it is quite likely that the queried entry
actually does exists within the protected resource.  In the end, all you need
to implement a bloom filter is an array of boolean values and a set of hashing
functions.  To this end, in my repo LearnBloomFilters, I have supplied the
developer with a set of hashing functions and also with a library I wrote 
specifically for this purpose, called bitArray.js.
  
For those that are curious, bitArray.js uses an array of unsigned integers and 
some very quick bitwise operations to implement the functionality of a boolean
array in javascript.  The testing suite, powered by mocha, is available by
simply running SpecRunner.html.  This will check up on your bloom filter 
implementation and run a series of tests on it to see if it is satisfactory.
If you can make your bloom filter pass all of the tests than you should have
a working bloom filter!  Have fun getting that page of green.

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.

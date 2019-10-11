# Streams
* brings functional programming to Java
* adv...
  * more efficient java programming
  * heavy use of lambda expressions
  * ParallelStreams make ease to multi-thread operations 

## working

`Stream Source---->Filter---->Sort---->Map---->Collect--->`

Stream Source can be created from Collections, Lists, Sets, ints, longs, doubles, arrays, lines of file

##### Operations
**Intermediate Ops** - such as filter, map or sort returns a steam so we can chain with other intermediatte ops.   
0 or moreiIntermediate ops are allowed.  
order matters for large datasets: filter first, then sort or map.    
for very large datasets use ParallelStream to enable multiple threads.
* anyMatch() 
* distinct()
* filter()
* findFirst()
* flatmap()
* map()
* skip()
* sorted()

**Terminal Ops** - such as forEach, collect or reduce returns either void or non-stream result
only one terminal ops allowed.  
forEach applies the same function to each elements.  
collect saves the elements to collection.  
other options reduce the stream to a single summary element.
* count()
* max()
* min()
* reduce()
* summaryStatistics()

**https://github.com/joeyajames/Java/blob/master/Java%208%20Streams/JavaStreams.java**

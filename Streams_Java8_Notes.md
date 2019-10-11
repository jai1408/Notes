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
Intermediate Ops - such as filter, map or sort returns a steam so we can chain with other intermediatte ops.  0 or more ops are allowed.  order matters for large datasets: filter first, then sort or map.  fore very large datasets use ParallelStream to enable multiple threads
Terminal Ops - such as forEach, collect or reduce returns either void or non-stream result

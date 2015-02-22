# szort
An easy to use multi-core aware command line sort utility

# rationale

Sorting numbers is awesome. Heck, that's the main thing computers are
good for, sorting and searching. You know the ol' unix 'sort' utility
only uses one core. I decided that was silly. szort will sort using N-1
of your cores!

# benchmark

We start with a file with a bunch of random numbers in it. How many?
```
  eduardos-mbp-5:szort earino$ wc -l random.txt
   11000000 random.txt
```
Well, how about 11 million?

Here we sort using the standard unix sort
```
  eduardos-mbp-5:szort earino$ time sort -n random.txt > /dev/null

  real    0m45.790s
  user    0m45.488s
  sys     0m0.272s
```
45 seconds to sort 11 million numbers? That's pretty cool, but using szsort?
```
  eduardos-mbp-5:szort earino$ time ./szsort random.txt > /dev/null

  real    0m31.290s
  user    1m5.375s
  sys     0m13.672s
```
31 seconds! We cut nearly 1/3 of the total time! Kinda magic if you ask
me.

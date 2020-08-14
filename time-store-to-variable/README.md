Adds options to time command:

```
-n - do not print elapsed time
-s <var> - store elapsed time in variable <var> (time in msecs)
```

Example usage in simple benchmark:

```
#!ipxe
set url http://100.100.100.69/100.bin
set loops:int8 5
set n:int8 0

:benchmark
imgfree
time -n -s _bench${n} imgfetch ${url}
inc n
iseq ${n} ${loops} || goto benchmark

set n:int8 0

:print
echo Run ${n} took ${_bench${n}} ms
inc n
iseq ${n} ${loops} || goto print
```


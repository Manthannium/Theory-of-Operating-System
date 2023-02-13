# Data Compression
```
In text file there are many zeros
So make blocks of size n (say 4 or 8)
Then we encode blocks according to some logic
Logic should be such that decoding is not ambiguous
```
Scheme 1
```
Make blocks of size 4
Full zero : 0000 -> 0
else      : abcd -> 1abcd

// example
encode 010100000011 -> 0101,0000,0011 -> 10101,0,10011 -> 10101010011
decode 010110011101 -> 0,10110,0,11101 -> 0000,0110,0000,1101 -> 0000011000001101
```


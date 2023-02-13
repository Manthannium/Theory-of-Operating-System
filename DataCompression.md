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
Scheme 2
```
Make blocks of size 4
Full zero : 0000 -> 0
single 1  : 1000/0100/0010/0001 -> 10 <address of 1 in 2 bits> -> 1000/1001/1010/1011
else      : abcd -> 11abcd

// example
encode 0101,0000,0100,0011 -> 110101,0,1001,110011
decode 1010110110011101 -> 1010,110110,0,11101 -> 0010,0110,0000,101
decode 110000 -> invalid as 11 means else block but it contains 0000 all zero
During decoding try to verify whether it aligns with the encoding scheme. Else it is invalid

// Note
observe in this scheme if there is single 1 in block,
then compression doesn't takes place as size remains same after encoding
But if block size is 8 or more then compression takes place

Also if there is not sufficient zero blocks then data expansion may also occur by encoding
```
Scheme 3
```
consecutive zeros and ones are separated out and encoded.
n 0s is encoded by (n+1)/2 a followed by ba/bb  ba for odd 0s, bb for even 0s
n 1s is encoded by (n-1) b
Insert 1 at beginning and at last (very much required)

While decoding remove 1 from start and end (if present)

// Example
encode : 10010001110
Add 1 at start and end : 1100100011101 
11,00,1,000,111,0,1
b,abb,,aaba,bb,aba,,   (Don't worry about ,,)
babbaababbaba is final code

decode : babbaababbaba
b,abb,,aaba,bb,aba
11,00,1,000,111,0
Now remove 1 at start and end if present
1,00,1,000,111,0
final string : 10010001110
```



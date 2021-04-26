# __HeroCTF v3__ 
## _Ping Pong_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Prog | 40 | Arthurique

**Description:** 

> Could you get the flag ?
Format : Hero{}
Author : xanhacks
+output.txt


## Solution
The order of PING's and PONG's looks suspicious, and letter O looks awfully similar to 0, and letter I - to 1.
What if we try and get a bit sequence from our PINGs and PONGs, and convert it to ASCII string?
This idea leads us to this simple script: 

```python
import sys

def main():
    filename = sys.argv[1]
    with open(filename, 'r') as f:
        file = f.readlines()
        
    bits = []
    for p in file:
        bits.append('0' if p == 'PONG\n' else '1')
    
    result = []
    for i in range(0, len(bits), 8):
        result.append(chr(int(''.join(bits[i:i+8]), 2)))
        
    print(''.join(result))

if __name__ == '__main__':
    main()
```

And as expected, from this we get our flag.


> Hero{p1n6_p0n6_15_fun}
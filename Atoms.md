# __HeroCTF v3__ 
## _Atoms_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Steganography | 50 | Arthurique

**Description:** 

> Dmitri sends us this message, will you be able to retrieve the secret message hidden inside?
MtMdDsFmMdHsMdMdUuo
Format : Hero{}
Author : xanhacks



## Solution
The task name and suspicious sequence suggest us that we should look at periodic table.
![periodic table](https://static.onecms.io/wp-content/uploads/sites/6/2013/08/breaking-bad-periodic-table.jpg)

Let's match each element with its atomic number.
```
Mt=109 
Md=101 
Ds=110 
Fm=100 
Md=101 
Hs=108 
Md=101
Md=101 
Uuo=118
```
This number sequence is also very suspicious! It looks like a sequence of ASCII codes. Let's check them. 

```python
atoms = [109, 101, 110, 100, 101, 108, 101, 101, 118]
result = []
for a in atoms:
    result.append(chr(a))

''.join(result)
```

The result is 'mendeleev'

> Hero{mendeleev}
# __HeroCTF v3__ 
## _Russian Doll_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Misc | 50 | Arthurique

**Description:** 

> Go deeper !
Format : Hero{}
Author : Enarior / xanhacks
+archive.zip

## Solution
Our flag is too deep in the archive, and the archives are full of Rick Roll's - all the more reason not to try to dig it manually and write a short script.
It's probably safe to assume that the file with flag is the deepest file in the archive hierarchy, so we can just find the longest pathname and read exactly that.

```python
import zipfile
archive = zipfile.ZipFile('archive.zip', 'r')

max = 0
max_i = 0
names = archive.namelist()
for i, nl in enumerate(names):
    if len(nl) > max:
    max = len(nl)
    max_i = i

f = archive.open(names[max_i])
f.read()
```

> Hero{if_yOu_gOt_HEre_By_clIcKInG_mANnUaLly_YoU_sHOuLd_REalLy_SeE_SoMeOne}
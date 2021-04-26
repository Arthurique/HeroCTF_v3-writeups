# __HeroCTF v3__ 
## _RansomWTF_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Steganography | 60 | Arthurique

**Description:** 

> My neighbour is obsessed with eggs.
So much that he doesn't have money left to buy some. When he was having a drink home, I left him 2 minutes on my PC, and I found all my pictures had been ransomwared.
He's asking for 2M eggs by tomorrow, but I can't buy that much eggs.
Even if I could, I'm not sure I would. Fortunately, he left the script he used to encrypt my pictures.
I hope you'll be able to retrieve this one..
Format : Hero{}
Author : iHuggsy


## Solution
Let's look at the scramble.py:

```python
import numpy as np
import cv2
import sys

"""
EGGMAN'S RANSOMWARE.
I LIKE EGGS, ESPECIALLY SCRAMBLED ONES. 
LET'S SEE HOW YOU LIKE YOUR SCRAMBLED PICTURES !
"""

def scramble(image):
    # 420 EGGS !
    np.random.seed(420)

    # Image dimensions : 1280x720
    to_hide = cv2.imread(image)
    to_hide_array = np.asarray(to_hide)

    for i in range(to_hide_array.shape[0]):
        np.random.shuffle(to_hide_array[i])
    
    gray = cv2.cvtColor(to_hide_array, cv2.COLOR_BGR2GRAY)
    cv2.imwrite('challenge.jpg', gray)

    print('EGGMAN IS DONE SCRAMBLING')

# You can totally scramble images as well, just use the script.

def main():
    if len(sys.argv) != 2:
        print('Usage : {} [FILENAME]'.format(sys.argv[1]))
        exit(1)
    
    scramble(sys.argv[1])

if __name__ == '__main__':
    main()
```

This script shuffles our image row by row with np.random.shuffle(to_hide_array[i]).
Seed for random shuffling is predetermined:
```python
np.random.seed(420)
```
So, if we look at how np.random.shuffle shuffles some array (for instance, array of numbers from 0 to 1279), we can get to know how to unshuffle any array back.

```python


def unshuffle(arr, size, indexes):
    result = [0] * size
    
    for i, ind in enumerate(indexes):
        result[ind] = arr[i]
    
    return np.array(result)
    
indexes = list(range(1280))
np.random.shuffle(indexes)
result = unshuffle(arr, 1280, indexes)
```

The only thing left is do this line by line and save our resulting image.
```python
def unscramble(image):
    np.random.seed(420)

    to_show = cv2.imread(image)
    to_show_array = np.asarray(to_show)
    image_size = 1280
    
    for i in range(to_show_array.shape[0]):
        indexes = list(range(image_size))
        np.random.shuffle(indexes)
        to_show_array[i] = unshuffle(to_show_array[i], image_size, indexes)
    
    gray = cv2.cvtColor(to_show_array, cv2.COLOR_BGR2GRAY)
    cv2.imwrite('result.jpg', gray)

    print('HERO IS DONE UNSCRAMBLING')
```

![result](https://sun9-50.userapi.com/impg/iEqwI7nQnePXDYILX8O-GTdbHIWLDu27Y0qwcw/1qMQOX_mzJc.jpg?size=1280x720&quality=96&sign=af110cb56990e1b913af7ce45baa9151&type=album)

> Hero{S3eD3d_Scr4Mbl3}
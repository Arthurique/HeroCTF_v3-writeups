# __HeroCTF v3__ 
## _HolyAbbot_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Steganography | 15 | Arthurique

**Description:** 

> A certain abbot tried to give us a message...
(the message is in lower case) (No need to speak French)
Format : Hero{messageinlowercase}
Author : Thib

+HolyAbbot.txt

## Solution
```
Dans son règne, Dans la béatitude
À tout jamais Dans son règne
Dans son royaume Irrévocablement
Dans son royaume Dans la béatitude
Dans son royaume Irrévocablement
Toujours En paradis


```

If we google some parts of these text, we'll discover that this is an Ave Maria cipher with known table for decoding it.
![table](https://sun9-21.userapi.com/impg/Jyw9uwyDW1zwTvqQEZY7mLx6eHQn5mFOPA1wsQ/_Ek6gccQ_Fg.jpg?size=395x269&quality=96&sign=9b8694f7da0b8568172a78dd1cd83ce4&type=album)
(from https://www.apprendre-en-ligne.net/crypto/tritheme/index.html)

Of course, there are a few letters for some parts of sentences, but it quickly becomes obvious which are the right ones.

> Hero{substitution}
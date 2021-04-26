# __HeroCTF v3__ 
## _Social ID #1_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
OSINT | 15 | Arthurique

**Description:** 

> Can you find the twitter ID of @HeroCTF.
Format : Hero{twitter_id}
Author : xanhacks

## Solution
Usually, id's on social networkink sites are present in photo links, buttons, tags properties and so on. Let's check few of those.
Follow button has an interesting property:
```
data-testid="815907006708060160-follow"
``` 
And also link to profile banner:
```
https://pbs.twimg.com/profile_banners/815907006708060160/1586530306/1080x360
```
It is now safe to assume that the same digit sequence 815907006708060160 in both of these cases is our user's profile id.


> Hero{815907006708060160}
# __HeroCTF v3__ 
## _Pushhhh_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
OSINT | 35 | Arthurique

**Description:** 

> The flag is in one of the two Github repositories of the last HeroCTF edition. Could you find it ?
Format : Hero{}
Author : xanhacks

## Solution
Let's look at the contest repository: https://github.com/HeroCTF
[HeroCTF_v1](https://github.com/HeroCTF/HeroCTF_v1)
[HeroCTF_v2](https://github.com/HeroCTF/HeroCTF_v2)

The thing that piques our interest is that [HeroCTF_v2](https://github.com/HeroCTF/HeroCTF_v2) has two active branches - and the second branch is named "flag"! 
The last commit message for this branch is
>xanhacks add flag :)

And that exact commit is a file flag.txt with our flag.

> Hero{y0u_re_g00d_4t_g1t_250820}
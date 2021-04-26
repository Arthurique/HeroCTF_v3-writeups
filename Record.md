# __HeroCTF v3__ 
## _Record_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Misc | 15 | Arthurique

**Description:** 

> Can you find anything special about this domain heroctf.fr ?
Format : Hero{}
Author : xanhacks

## Solution

Let's look at DNS records for the domain heroctf.fr. For that, we can use nslookup/dig utilites or some online variants, such as https://dnsdumpster.com/
Using any one of these, we easily get our flag from one of the TXT record.

``` 
v=spf1 mx a -all
Hero{cl34rtXt_15_b4d}
```

> Hero{cl34rtXt_15_b4d}
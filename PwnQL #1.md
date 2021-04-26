# __HeroCTF v3__ 
## _PwnQL #1_

## Information
**Category:** | **Points:** | **Writeup Author**
--- | --- | ---
Web | 50 | Arthurique

**Description:** 

> Login as admin to get the flag.
URL : http://chall1.heroctf.fr:8080
Format : Hero{}
Author : xanhacks

## Solution
If we look at the source code of this page, we can see an interesting comment left there by some pretty careless developers
><!-- Hello dev, do not forget to remove login.php.bak before committing your code. -->

If we check http://chall1.heroctf.fr:8080/login.php.bak , we can indeed see that the file has not been deleted.
Let's have a look.


```php
<?php

require_once(__DIR__  . "/config.php");

if (isset($_POST['username']) && isset($_POST['password'])) {
    $username = $_POST['username'];
    $password = $_POST['password'];

    $sql = "SELECT * FROM users WHERE username = :username AND password LIKE :password;";
    $sth = $db->prepare($sql, array(PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY));
    $sth->execute(array(':username' => $username, ':password' => $password));
    $users = $sth->fetchAll();

    if (count($users) === 1) {
        $msg = 'Welcome back admin ! Here is your flag : ' . FLAG;
    } else {
        $msg = 'Wrong username or password.';
    }
}

```

The most interesting line for us here is this one:
```php
    $sql = "SELECT * FROM users WHERE username = :username AND password LIKE :password;";
```
Or more specifically:
```php
    password LIKE :password;
```
The password that we enter in the "password" field is used as a pattern for querying sql-base.
So, the only thing left is find the pattern the admin password falls into - the wildcard character %. It matches every string of zero or more characters.

And voila!
``` 
Welcome back admin ! Here is your flag : Hero{pwnQL_b4sic_0ne_129835}
```

> Hero{pwnQL_b4sic_0ne_129835}
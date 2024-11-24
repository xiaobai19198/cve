# crud  has sql injection vulnerability in delete-inline.php

## supplier
https://code-projects.org/crud-operation-system-in-php-with-source-code/
## Vulnerability file
delete-inline.php
## describe
There is an unauthorized SQL injection vulnerability in  delete-inline.php of crud-system.

Control parameter: **$stu_id**

 The information of the database can be obtained without authorization, and arbitrary commands may be executed. 



## code analysis

The **$stu_id** parameter in delete-inline.php is controlled and is directly carried into the SQL statement for execution, resulting in SQL injection.

![image-20241124233142486](https://github.com/user-attachments/assets/a49c5cf5-a3ce-4211-83ed-bbc838bd3700)

Inject parameter：$stu_id

## POC

Get tables of crud

```
python sqlmap.py -u "http://localhost/crud/delete-inline.php?id=1*" --tables -D crud 
```

![image-20241124232721870](https://github.com/user-attachments/assets/ddfe303c-b428-43ea-8bb6-741aae1424d4)
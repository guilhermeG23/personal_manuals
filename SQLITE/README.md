//Não recomendado para uso extenso
* Limite de banco de 280 teras
* Não é recomendado para multiplos usuários ao mesmo tempo
* Limitado por uma escrita por vez

```
sqlite3 teste.db '.tables' 
```
```
sqlite3 teste.db 'select count(id) from openvpn_control limit 1'
```
```
.schema -> Mostra o comando usado para criar uma tabela
```

```
root@debian:~# touch banco.db
root@debian:~# sqlite3 banco.db 
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> create table t1 (a int, b int);
sqlite> .schema
CREATE TABLE t1 (a int, b int);
sqlite> insert into first (a,b) values (1,2);
Error: no such table: first
sqlite> insert into t1 (a,b) values (1,2);
sqlite> select * from t1;
1|2
```

```
sqlite> .quit
root@debian:~# 
```

____
Listar as tabelas
```
sqlite> .table
t1
```
```
sqlite> .tables
t1
```
```
root@debian:~/sqlite# sqlite3 teste1
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> .exit
root@debian:~/sqlite# 
```

```
root@debian:~/sqlite# ls
root@debian:~/sqlite# sqlite3 teste1
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> .quit
root@debian:~/sqlite# ls
root@debian:~/sqlite# sqlite3 teste1
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> create table t1 (a int, b int);
sqlite> insert into t1 (a,b) values (1,2);
sqlite> .quit
root@debian:~/sqlite# ls
teste1
```

```
root@debian:~/sqlite# ls
root@debian:~/sqlite# sqlite3 teste
SQLite version 3.34.1 2021-01-20 14:10:07
Enter ".help" for usage hints.
sqlite> create table teste (a int primary key,b varchar(20));
sqlite> insert into teste (a,b) values (0, 1);
sqlite> .tables
teste
sqlite> select * from teste;
0|1
sqlite> .exit
root@debian:~/sqlite# ls 
teste
```
___
Limpa o terminal sql
```
sqlite> .shell clear
```

```
sqlite> insert into teste (a,b) values (1,1),(2,2),(3,3);
sqlite> select * from teste;
0|1
1|1
2|2
3|3
sqlite> 
```

```
sqlite> create table t2 (t1 integer, t2 text);
sqlite> .tables
t2     teste
sqlite> .table
t2     teste
sqlite> select * from teste;
0|1
1|1
2|2
3|3
sqlite> .tables
t2     teste
sqlite> insert into t2 values (1, 't1');
sqlite> insert into t2 values (3, 't2');
sqlite> insert into t2 values (3, 't2');
sqlite> select * from t2;
1|t1
3|t2
3|t2
```

Ligando e desligando o titulo das colunas
```

sqlite> .headers on
sqlite> select * from t2;
t1|t2
1|t1
3|t2
3|t2
sqlite> .headers off
sqlite> select * from t2;
1|t1
3|t2
3|t2
sqlite> 
```

```
sqlite> alter table t2 rename to t3;
sqlite> select * from t2;
Error: no such table: t2
sqlite> select * from t3;
1|t1
3|t2
3|t2
sqlite> .tables
t3     teste
```

```
sqlite> .headers on
sqlite> .schema
CREATE TABLE teste (a int primary key,b varchar(20));
CREATE TABLE IF NOT EXISTS "t3" (t1 integer, t2 text);
sqlite> select * from t3;
t1|t2
1|t1
3|t2
3|t2
sqlite> delete from t3 where t1 = 3;
sqlite> select * from t3;
t1|t2
1|t1
```

```
sqlite> alter table t3 add t3;
sqlite> .schema
CREATE TABLE teste (a int primary key,b varchar(20));
CREATE TABLE IF NOT EXISTS "t3" (t1 integer, t2 text, t3);
sqlite> select * from t3;
t1|t2|t3
1|t1|
```

```
sqlite> drop table t3;
sqlite> .schema
CREATE TABLE teste (a int primary key,b varchar(20));
sqlite> .tables
teste
```


```
sqlite> select * from teste;
a|b
0|1
1|1
2|2
3|3
sqlite> select * from teste where a = 3;
a|b
3|3
sqlite> select * from teste where a = 3 and b = 3;
a|b
3|3
sqlite> select * from teste where a = 3 and b = 2;
sqlite> select * from teste where a = 3 or b = 2;
a|b
2|2
3|3
```


```
sqlite> select * from teste where a = 3 or b = 2 order by a;
a|b
2|2
3|3
sqlite> select * from teste where a = 3 or b = 2 order by a desc;
a|b
3|3
2|2
sqlite> select * from teste where a = 3 or b = 2 order by a asc;
a|b
2|2
3|3
```


```
sqlite> select * from teste where a = 3 or b = 2 order by a asc limit 1;
a|b
2|2
sqlite> select * from teste where a = 3 or b = 2 order by a asc;
a|b
2|2
3|3
```

Usando o like para filtrar qualquer valor que tenha uma parte especifica em uma coluna
```
sqlite> select * from teste where a like '%3%' or b = 2 order by a asc;
a|b
2|2
3|3
```

```
sqlite> select * from teste where a > 2;
a|b
3|3
```

```
sqlite> select * from teste where a < 2;
a|b
3|3
```

```
sqlite> select (a + b) as "soma a + b" from teste where a >= 2;
soma a + b
4
6
```
___
Somar todas as colunas
```
sqlite> select (a + b) as "soma a + b" from teste where a >= 2;
soma a + b
4
6
sqlite> select sum(a + b) as "soma a + b" from teste where a >= 2;
soma a + b
10
```


```
sqlite> select (a + b) as "soma a + b" from teste where a > 2;
soma a + b
6
```
____
Arrendodamento de valor
```
sqlite> select round(sum(a + b)) as "soma a + b" from teste where a >= 2;
soma a + b
10.0
```


```
sqlite> select * from teste;
a|b
0|1
1|1
2|2
3|3
sqlite> update teste set (a, b) = (6,6) where a = 3;
sqlite> select * from teste;
a|b
0|1
1|1
2|2
6|6
```


Retorna o tamanho das strings
```
sqlite> select length(a) from teste;
length(a)
1
1
1
1
2
```


```
sqlite> select * from teste where a > 10;
a|b
11|teste
12|teste1
13|TesTe1
sqlite> select lower(b) from teste where a > 10;
lower(b)
teste
teste1
teste1
sqlite> select upper(b) from teste where a > 10;
upper(b)
TESTE
TESTE1
TESTE1
```


Limita a apresentação da string a um numero de caracteres
```
sqlite> select substr(b,1,4) from teste where a > 10;
substr(b,1,4)
test
test
TesT
```

```
sqlite> select random();
random()
49583842884786252
```

```
sqlite> select * from teste;
a|b
0|1
1|1
2|2
6|6
10|
11|teste
12|teste1
13|TesTe1
sqlite> update teste set b = 'teste';
sqlite> select * from teste;
a|b
0|teste
1|teste
2|teste
6|teste
10|teste
11|teste
12|teste
13|teste
sqlite> select * from teste group by b;
a|b
0|teste
```


____
Having é a definição de ter para fazer a pesquisa
```
sqlite> select * from teste;
a|b
0|teste
1|teste
2|teste
6|teste
10|teste
11|teste
12|teste
13|teste
sqlite> select * from teste group by b;
a|b
0|teste
sqlite> select * from teste group by b having count(*) = 1;
sqlite> select * from teste group by b having count(*) > 1;
a|b
0|teste
```



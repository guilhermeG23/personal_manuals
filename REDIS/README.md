#Listar as chaves

127.0.0.1:6379> keys *
1) "pastel"

#Listar os valores das chaves 
lrange <chave> <inicio> <fim>

#Confirmar se o serviço está funcionando e retornando conexão
redis-cli -h 127.0.0.1 -p 6379 PING

Criar uma chave valor
set chave valor

Inserindo N valores
mset chave1 valor1 chave2 valor2

Buscando valor de uma chave setada
get chave

----------------------------------------------
127.0.0.1:6379> set teste 1
OK
127.0.0.1:6379> get teste
"1"
127.0.0.1:6379> del teste
(integer) 1
127.0.0.1:6379> get teste
(nil)

----------------------------------------------


inserindo do lado esquerdno
lpush lista valor (integer) 1

inserindo o lado direito 
rpush lista valor2 (integer) 2 

Deletar o valor de uma chave
del chave 

//Deleta todas as bases
FLUSHALL


_____________________________________________
Da para usar o Redis como banco normal

* Sem primary key nos valores

Strings -> Tudo é um string 
Lists -> Uma lista comporta varias strings
Sets -> Lista não ordenada
Sorted sets -> Listas ordenadas por valores
Hashes -> Dicionario chave -> valor com listas


Além do executavel, ele tem o arquivo de configuração e só

Pode usar toda a memória do sistema, porém, é limitado a 1 núcleo de CPU (Melhor escalar em cluster para ter mais performance que adicionar Hardware)

Se o dado não for usado em uma faixa de tempo, ele é removido pelo redis

se alguma coisa der o retorno de (nil), significa que foi um retorno nulo (null)


//Retornar se há comunicação com o Redis-cli
127.0.0.1:6379> ping
PONG
127.0.0.1:6379> ping 'hello world'
"hello world"




inserir uma string
set teste 1

Inserir várias chaves valor
mset t1 t1 t2 t2


Inserindo vários valores numa chave

127.0.0.1:6379> LPUSH t3 t1 t2 t t4 t5
(integer) 6

//get não pega mais normalmente
127.0.0.1:6379> get t3
(error) WRONGTYPE Operation against a key holding the wrong kind of value

//Tem que pegar pelo range de dados que 0 é o primeiro valor da lista e -1 representa o final da lista
127.0.0.1:6379> lrange t3 0 -1
1) "t5"
2) "t4"
3) "t"
4) "t2"
5) "t1"
6) "t1"

//Faz a mesma coisa que o L
RPUSH t3 t1 t2 t t4 t5


A diferença do L para o R é a posição de inserção dos dados


//Somente armazena valores unicos 
SADD chave t1 t2 t2 t3 t4 t5 t6

//Obter os valores de chave
127.0.0.1:6379> SMEMBERS chave
1) "t3"
2) "t4"
3) "t5"
4) "t6"
5) "t1"
6) "t2"

//Inserir e listar valores do ZADD
127.0.0.1:6379> ZADD teste 1 t1 2 t2 3 t3 4 t4 
(integer) 4
//Traz sempre do menor para o maior
127.0.0.1:6379> zrange teste 0 -1
1) "t1"
2) "t2"
3) "t3"
4) "t4"

//Traz do maior para o menor
127.0.0.1:6379> zrevrange teste 0 -1
1) "t4"
2) "t3"
3) "t2"
4) "t1"


//Coleção de chaves valores 
hmset testes t1 1 t2 2 t3 3

//Obtendos os valores das chaves de dentro da chave list
127.0.0.1:6379> HMGET testes t1
1) "1"


//Limpar os dados depois de um certo tempo
127.0.0.1:6379> expire t1:1 30
(integer) 1
127.0.0.1:6379> ttl t1:1 
(integer) 18


127.0.0.1:6379> hmset t1:1 t10 tttt t11 yyyy 
OK
127.0.0.1:6379> HMGET t1:1 t10
1) "tttt"



Exiset determinada chave
127.0.0.1:6379> keys *
1) "teste"
2) "t1:1"
3) "testes"
4) "pastelem154550"
5) "foo"
127.0.0.1:6379> exists foo
(integer) 1
127.0.0.1:6379> exists foo1
(integer) 0


Definir o tempo que um valor vai durar dentro de uma chave
127.0.0.1:6379> setex teste 10 1
OK
127.0.0.1:6379> get teste
"1"
127.0.0.1:6379> ttl teste
(integer) 5
127.0.0.1:6379> ttl teste
(integer) 3
127.0.0.1:6379> ttl teste
(integer) 2
127.0.0.1:6379> ttl teste
(integer) 1
127.0.0.1:6379> ttl teste
(integer) 0
127.0.0.1:6379> ttl teste
(integer) -2
127.0.0.1:6379> ttl teste
(integer) -2
127.0.0.1:6379> get teste
(nil)
127.0.0.1:6379> ttl teste
(integer) -2
127.0.0.1:6379> 


//É uma lista incrementavel
127.0.0.1:6379> lpush teste 1
(integer) 1
127.0.0.1:6379> lrange teste 0 -1
1) "1"
127.0.0.1:6379> lpush teste 2
(integer) 2
127.0.0.1:6379> lpush teste 3
(integer) 3
127.0.0.1:6379> lrange teste 0 -1
1) "3"
2) "2"
3) "1"
127.0.0.1:6379> rpush teste 4
(integer) 4
127.0.0.1:6379> lrange teste 0 -1
1) "3"
2) "2"
3) "1"
4) "4"


//Remover elementos da chave
127.0.0.1:6379> lpop teste
"3"
127.0.0.1:6379> lrange teste 0 -1
1) "2"
2) "1"
3) "4"
127.0.0.1:6379> rpop teste
"4"
127.0.0.1:6379> lrange teste 0 -1
1) "2"
2) "1"


//Lista de hash's
127.0.0.1:6379> hset teste1 teste t2
(integer) 0
127.0.0.1:6379>  hget teste1 teste
"t2"

//Pegar todos o valores armazenados em hash
127.0.0.1:6379> hgetall teste1
1) "teste"
2) "t2"
3) "teste1"
4) "t1"
5) "teste2"
6) "t2"
7) "teste3"
8) "t3"

//Confirmar se existe um campo chave no hash
127.0.0.1:6379> HEXISTS teste1 t1
(integer) 0
127.0.0.1:6379> HEXISTS teste1 teste1
(integer) 1


redis-cli --raw lrange teste 0 -1
t1
t2
t3

//---------------------------------------------------------------
Persistencia de dados

RDB (Banco de Dados Redis): A persistência RDB executa instantâneos point-in-time de seu conjunto de dados em intervalos especificados.

AOF (Append Only File): A persistência AOF registra cada operação de escrita recebida pelo servidor, que será reproduzida novamente na inicialização do servidor, reconstruindo o dataset original. Os comandos são registrados usando o mesmo formato que o próprio protocolo Redis, apenas de forma anexada. O Redis é capaz de reescrever o log em segundo plano quando fica muito grande.

Sem persistência : Se desejar, você pode desabilitar a persistência completamente, se quiser que seus dados existam apenas enquanto o servidor estiver em execução.

RDB + AOF : É possível combinar AOF e RDB na mesma instância. Observe que, nesse caso, quando o Redis reiniciar, o arquivo AOF será usado para reconstruir o conjunto de dados original, pois é garantido que ele seja o mais completo.
//---------------------------------------------------------------

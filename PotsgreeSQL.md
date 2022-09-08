# PotsgreeSQL
> PostgreSQL é um sistema gerenciador de banco de dados objeto relacional (SGBD), desenvolvido como projeto de código aberto.

## Comandos

### Criação do banco
```bash 
CREATE DATABASE LIBRARY;
```

### Conexão com o banco
```bash 
\connect LIBRARY
```

### Criação das tabelas
* ```creaate table```: cria uma nova tabela.
* ```if not exists```: cria uma nova tabela somente se ela já não existir.
* ```serial```: indica que é ```integer``` e ```not null```.
* ```not null```: o valor não pode ser nullo.
* ```default```: padroniza um valor caso não seja atribuído nenhum.
* ```constraint```: restrição. 
* ```serial```:

```bash 
create table if not exists book(
    id serial not null
        constraint pk_book_id primary key,
    title varchar(64) not null,
    pages int not null
    constraint df_book_pages default 0,
    gender_id int,
    author_id int,
    publisher_id int,
    constraint fk_book_gender_id foreign key (gender_id) references gender(id),
    constraint fk_book_author_id foreign key (author_id) references author(id),
    constraint fk_book_publisher_id foreign key (publisher_id) references publisher(id)
    );
```

#### Primary Key
> É a coluna que identifica uma tabela, devendo possuir valor único. 
* Deve-se adcionar uma restrição (```constraint```) à coluna, especificando que ela será a chave primária (```primary key```). 
```bash 
id serial not null
        constraint pk_book_id primary key,
```

#### Foreign Key
> É a chave primária de uma tabela X que é declarada em uma tabela Y, objetivando demonstrar a relação existente entre duas ou mais tabelas. 
* Após declarar a coluna, adiciona-se uma  restrição (```constraint```) à coluna, especificando que ela será a chave estrangeira (```foreign key```). 
```bash 
constraint fk_book_gender_id foreign key (gender_id) references gender(id),
```

### Inserção de valores
* Os valores devem ser inseridos em uma tabela com a utilização do comando ```insert into```, os quais devem ser inseridos na ordem em que foram declarados.
```bash 
insert into book values(0, 'Harry Potter e A Pedra Filosofal', 266, 0, 0, 1);
```

### Consultas 
> As consultas servem para buscarmos determinadas tabelas a partir de colunas específicas, ou ainda, buscar colunas específicas de uma tabela a partir de condições específicas.
* As consultas podem ser realizadas de diversas formas, sejam por ```select``` simples ou avançados, bem como por agrupamento de colunas específicas.

#### Select
* ```select```: especifica colunas a serem retornadas.
* ```*```: retorna todas as colunas da tabela.
* ```from```: especifica tabela.

```bash 
select * from author;
```

* ```where```: filtra as colunas de uma tabela por meio de uma condição.
* ```like```: compara pedaços de uma string. 
* ```author.name```: especifica qual coluna da tabela será analisada. 
```bash 
select *
FROM AUTHOR
where author.name like 'Mayana%';
```
> NOTA: a % desconsidera o que vem em seguida, anteriormente ou em qualquer direção, a depender do local onde é inserida. 

#### Joins 
* A cláusula ```join``` é responsável por juntar duas ou mais tabelas em um único ```select```, existindo 05 tipos de jois:
> NOTA: para cda join a estrutura é a mesma, o que muda é a condição de junção de cada uma, isto é, ```inner join ... on```, ```left join ... on``` e assim por diante.
> 
##### Inner join
> Junta as tabelas referenciadas apenas onde existe relação de colunas. 
* ```loan l```: emprega um apelido de referência para a tabela.
* ```inner join book b```: especifica com quem a tabela irá se juntar.
* ```on```: filtra a junção das tabelas por meio de uma condição, neste caso: onde os ```id``` de cada tabela forem iguais.

```bash 
select l.id as id, b.title as title, s.name as aluno, li.name as librarian
from loan l
         inner join book b
                    on b.id = l.book_id
         inner join librarian li
                    on li.id = l.librarian_id
         inner join student s
                    on s.id = l.student_id
where l.id = 1;
```
![inner join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image002.jpg)

##### Left join
> Leva em consideração apenas as colunas da tabela A e omite as colunas da tabela B que não estejam relacionadas com a tabela A. 

![left join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image004.png)

##### Right join
> Leva em consideração apenas as colunas da tabela B e omite as colunas da tabela A que não estejam relacionadas com a tabela B. 

![right join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image006.jpg)

##### Outer (Full) join
> Junta tudo de todas as tabelas referenciadas.

![outer join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image008.jpg)

##### Left Excluding join
> Omite a tabela B e a interseção dela com a tabela A. 

![left excluding join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image010.jpg)

##### Right Excluding join
> Omite a tabela A e a interseção dela com a tabela B. 

![right excluding join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image012.jpg)

##### Outer Excluding join
> Omite apenas a interseção entre as tabelas A e B (oposto ao ```inner join```. 

![outer excluding join](https://arquivo.devmedia.com.br/artigos/Fernanda_sallai/sql_join/image014.jpg)

#### Group By
* A cláusula GROUP BY agrupa linhas baseado em semelhanças entre elas. 
* No exemplo abaixo, está sendo agrupado a coluna ```name``` da tabela ```author``` e contando quantas vezes ele se repete.
> NOTA: o group by deve vir acompanhado de funções no select.
 
```bash 
select count(*), author.name
FROM AUTHOR
    inner join book b on author.id = b.author_id
where author.id = 2
group by author.name; 
```

### Outros comandos

#### Delete
> Deleta uma coluna da tabela.
```bash 
delete from author where id=8;
```

#### Drop 
> Deleta uma tabela inteira.
```bash 
drop table student;
```

# API (Interface de Programação de Aplicações)

> APIs são mecanismos que permitem que dois componentes de software se comuniquem usando um conjunto de ```definições e protocolos```.

## Conceito
API significa Application Programming Interface (```Interface de Programação de Aplicação```). No contexto de APIs, a palavra Aplicação refere-se a qualquer software 
com uma função distinta. A interface pode ser pensada como um contrato de serviço entre duas aplicações. Esse contrato define como as duas se comunicam usando 
solicitações e respostas. A documentação de suas respectivas APIs contém informações sobre como os desenvolvedores devem estruturar essas solicitações e respostas.
(AMAZON, 2022)

## Objetivo
Realizar uma comunicação plena entre o cliente (quem realiza requisições, como um usuário, por exemplo) e o servidor (quem fornece as informações, como a aplicação, 
por exemplo), bem como ```abstrair a comunicação``` entre dois aplicativos. 

## REST
> Transferência Representacional de Estado
* É um estilo de arquitetura que fornece ```padrões para a comunicação```. O padrão REST define um conjunto de funções como ```GET```, ```PUT```, ```DELETE```.
* A principal característica da API REST é a ausência de estado. A ausência de estado significa que os servidores não salvam dados do cliente entre as solicitações.

### Benefícios
1. ```Integração```: integra novas aplicações, não precisando construí-las do zero.
2. ```Inovação:``` novas funcionalidades.
3. ```Expansão:``` atende plataformas diversas.
4. ```Facilidade de manutenção:``` as alterações feitas em uma aplicação não afetam diretamente a outra, já que a API funciona como um ```gateway```.
> NOTA: gateway são  intermediários entre o utilizador e a rede.  

## Protocolo HTTP
> HTTP é um protocolo (protocol) que permite a obtenção de recursos, como documentos HTML. É a base de qualquer troca de dados na Web e um protocolo cliente-servidor, 
o que significa que as requisições são iniciadas pelo destinatário, geralmente um navegador da Web.
* ```Requisições```: solicitações (```requests```) eviadas pelo cliente.
> NOTA: toda requisição tem métodos. 
* ```Respostas```: mensagens (```responses```) enviadas como respostas pelo servidor.

### Requisições
* ```GET```: buscar.
* ```POST```: criar.
* ```PUT```: atualizar.
* ```DELETE```: deletar. 

### Status Code
> São as repostas enviadas pelo servidor, retornando o estado da requisição por meio de códigos.

```
------------------------------------------------------------------------------------------------
|     2**    |               3**               |          4**          |          5**          |
------------------------------------------------------------------------------------------------
|   sucesso  |  categoria de redirecionamento  |    erro no cliente    |   erro no servidor    |
------------------------------------------------------------------------------------------------
```

#### 2** (sucesso)
* ```200_OK```: (get) retorna informação.
* ```201_CREAT```: (post) retorna informação.
* ```204_NO_CONTENT```: (put/delete) não retorna informação.

#### 4** (erro no cliente)
* ```400_BADREQUEST```: erro de sintaxe (e.g.: int tratado como inteiro)
* ```422_UNPROCESSABLE_ENTITTY```: validação (e.g.: idade < 16)
* ```404_NOT_FOUND```: recurso não existe.
* ```403_FORBIDEN```: sem permissão.

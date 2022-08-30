# Aplicação prática da Arquitetura Hexagonal

## Divisão Geral
> Estruturação dos diretórios na arquitetura hexagonal, objetivando tornar a aplicação desacoplada. 

<p> <center> Figura 1: Estruturação dos principais diretórios da Arquitetura Hexagonal </center> </p>   
   <img src="Figuras/Estrutura-hexagonal.jpg" alt=""
    title="Figura 1: Estruturação dos principais diretórios da Arquitetura Hexagonal" width="300" height="auto"/>

### docker
> Contém o ```docker```, o qual armazena o banco de dados em um container, além do arquivo ```init.sql```.

### src
> Contém todos os diretórios que estruturam o código e fazem ele funcionar, com exceção do diretório ```docker```.

### Core (núcleo)
> Contém toda a lógica e as regras do negócio da aplicação, composta por domains e casos de uso, bem como por portas que introduzem os adaptadores, tornando possíel a injeção de dependências. 

#### Domains
* ```domain```: repressentação das entidades. Nela, criamos as ```structs```, os ```construtores``` e uma eventual ```String()```.

   <p> <center> Figura 2: Estruturação de um arquivo na domain. </center> </p>   
   <img src="Figuras/domainAuthor.png" alt=""
    title="Figura 2: Estruturação de um arquivo na domain." width="auto" height="400"/>

#### Interfaces (portas)
* ```interface```: contém as ```assinaturas dos métodos``` que são usados pelos ```adaptadores``` . Nela, declaramos as portas para o ```service``` (caso de uso/portas primárias), o qual é atrelado ao ```usuário```, e para o ```repositórios``` (portas secundárias), o qual é atrelado ao ```núcleo```.

   <p> <center> Figura 3: Estruturação de um arquivo na interface. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 3: Estruturação de um arquivo na interface." width="auto" height="400"/>
    
#### Serviços (casos de uso)
* ```services```: contém a ```lógica da aplicação``` diretamente relacionada às ```portas primárias```, pois espera a requisição do cliente. Nela, declaramos os métodos que serão usados na aplicação, além de declararmos uma ```interface do repositório```, pois não sabemos por quem ou como será tratada as informações, como qual tipo de ```banco de dados``` será utilizado.

   <p> <center> Figura 4: Estruturação de um arquivo no services. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 4: Estruturação de um arquivo no services." width="auto" height="400"/>

### Camadas externas
> São as camadas que se comunicam com o núcleo da aplicação, embora este desconheça quem os implementa. Isso é essencial, pois torna a aplicação desacoplada e de fácil manipulação e testes.

#### API
* ```api```: trata-se de uma camada de aplicação, que trata e ```manipula``` as requisições do usuário. Nela, declaramos as ```rotas``` e recolhemos as ```requisições do usuário```. Sobre ela, é importante mencionar que tem a função de implementar a ```interface do caso de uso``` a ser trabalhada.
 
   <p> <center> Figura 5: Estruturação de um arquivo no repositories. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 5: Estruturação de um arquivo no repositories." width="auto" height="400"/>

#### Repositórios
* ```repository```: contém o ```tratamento da informação``` por um banco de dados, por exemplo. Antes de ser manuiseada, é necessário trabalhar com sua interface, a qual é chamada no ```services```.

   <p> <center> Figura 6: Estruturação de um arquivo no repositories. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 6: Estruturação de um arquivo no repositories." width="auto" height="400"/>
 
#### DOCKER
* ```docker```: são ```contâiners``` que guardam de maneira organizada os mecanismos cruciais para a construção do sistema. Neste caso, o docker está guardando o nosso arquivo ```init.sql``` responsável por ```construir o banco de dados```. 

   <p> <center> Figura 7: Estruturação de um arquivo no docker. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 7: Estruturação de um arquivo no docker." width="auto" height="400"/>

#### DATA
* ```data```: diretório que contém os arquivos responsáveis por manipular o ```banco de dados```.

   <p> <center> Figura 8: Estruturação de um arquivo no data. </center> </p>   
   <img src="Figuras/interfaceAuthor.png" alt=""
    title="Figura 8: Estruturação de um arquivo no data." width="auto" height="400"/>

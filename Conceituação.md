# Conceituação da Arquitetura Hexagonal

## O que é?

A arquitetura hexagonal é um modelo de estruturação de códigos, a qual objetiva construir sistemas que confiram as seguintes características:

* Reusabilidade de código;
* Alta coesão:
* Baixo acoplamento:
* Independência de tecnologia;
* Facilidade em aplicar testes.

Além disso, caracteriza-se por reter a lógica de negócio em um núcleo (```core```), o que torna essa aplicação independente de sistemas externos.
Por outro lado, pode-se mencionar também que esta arquitetura trabalha com a ideia de "plugar" adaptadores (```adapters```) no sistema a partir de ```portas```. 
Por fim, destacar que a Arquitetura Hexagonal trabalha no sentindo de "interno >> externo" é importante, já que, por possuir um caráter desacoplado, 
é importante que nada externo ao sistema seja tratado em suas camadas mais internas. Assim, o nlúcleo do sistema dessa arquitetura está totalmente desconexo com 
o meio externo, a não ser pela ```injeção de dependências``` (que trataremos mais adiante). 


## Estrutura
A estrutura hexagonal dividi-se, principalmente em quatro partes:

### Núcleo
É o coração do sistema. É representada por ```entidades``` e ```regras de negócio```. O núcleo é independente da infraestrutura da aplicação, 
não recocnhecendo camadas externas que o envolvem, e facilmente testável em isolamento.

### Atores

Tudo o que interage com o núcleo, sejam eles:
* ```Primários``` (quem inicia a comunicação com o núcleo, como um ```usuário```); ou
* ```Secundários``` (espera que o núcleo inicie a comunicação, como o ```banco de dados```).

> NOTA: as linguagens que o núcleo e os autores utilizam para se comunicar podem não ser compreendidas para um ou para o outro, 
então é necessário criar uma INTERFACE DE COMUNICAÇÃO, a qual deve ser realizada por alguém que saiba traduzir essas informações 
(o que uma intérprete de LIBRAS faz, por exemplo). A intérprete de LIBRAS nesse nosso caso são as PORTAS e os ADAPTADORES.

### Portas
São interfaces pertecentes ao núcleo e define como a comunicação deve ser implementada.
* ```Portas primárias```: definições de ```casos de uso``` (serviços) que são usados pelos ```atores primários```.
* ```Portas secundárias```: definições do que o ator secundário deve implementar.

### Adaptadores
São os responsáveis pela tradução das informações entre o núcleo e os atores.

## Injeção de dependências 
A injeção de dependências ocorre quando os adaptadores são plugados nas portas que lhes são destinadas, ou seja, 
quando um serviço é disponibilizado para uso.


> Texto base disponível em <https://medium.com/avenue-tech/arquitetura-hexagonal-com-golang-c344411aa940>. 

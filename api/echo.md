### Conceitos

* ```echo.Context```: representa o contexto da solicitação HTTP atual. 
Ele contém referência de solicitação e resposta, caminho, parâmetros de caminho, dados, manipulador 
registrado e APIs para ler a solicitação e gravar a resposta. 
Como o Context é uma interface, é fácil estendê-lo com APIs personalizadas.
* ```bind```: liga o objeto ao contexto de solicitação. 

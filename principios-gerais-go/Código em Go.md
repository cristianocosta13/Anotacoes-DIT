# Código em Go

## Laços de repetição
```bash
for _, c := range clients {
		...
}
```

## Estruturas condicionais 
Condições em Go não são delimitadas por parênteses, embora precise-se utilizar as chaves quando houver estruturas com mais de uma linha de comando.
* Excetuando esses detalhes, as estruturas condicionais são semelhanes. 

## Tratamento de erros 
Go é uma linguagem em que muitos erros podem ocorrer, então é necessário que todos esses erros sejam tratados, visando o pleno funcionamento do código.
* Em Golang os erros podem ser um dos retornos das funções, diferente de outras linguagens, o que facilita a manipulação de problemas.
> No código abaixo, retornamos um erro se o saldo do cliente for negativo. Note que o erro é gerado no retorno e referenciado na declaração da função, com o tipo "error". 
```bash
func Payment(discount float32, plant templates.Plant) (float32, error) {
	var valuePaid float32
	fmt.Print("Insira o valor a ser pago: ")
	fmt.Scan(&valuePaid)
	if valuePaid > plant.Price {
		return valuePaid - (plant.Price - discount), nil, 0
	} else {
		return valuePaid, errors.New("Saldo insuficiente!")
	}
}
```
* É ideal que o erro seja o último retorno e que não sejam retornadas muitas variáveis. 
> Abaixo é demonstrado como manusear o retorno do erro.
```bash
payback, error := Payment(amountDebilled, *plant)
		if error != nil {
			log.Print("\O cliente deve pagar mais R$"+err.Error())
		}
		fmt.Print("O troco do cliente é R$", payback)
```
* É ideal que a excessão seja tratada primeiro, para evitar códigos verbosos (<i>elses</i> desnecessários). 
## Comunicação entre pacotes 
Sempre que for necessário consultar um método/struct contido em outro pacote deve-se importar o pacote desejado:
```bash
"library/src/api/handlers/dtos/request"
```
Depois disso, dve-se informar o que você irá manusear daquele pacote, sempre referenciando-o (semelhante o tratamento de atributos de um onjeto na linguagem <i>Java</i>):
```bash
var authorDTO request.RegisterAuthor
```

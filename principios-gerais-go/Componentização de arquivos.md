# Componentização de arquivos

## Structs
> Em comparação com a orientação a objetos, a struct desempenha um papel similar ao objeto em Java, por exemplo. Em linhas gerais, as structs coletam diferentes dados e os organizam sob diferentes nomes de campo.

### Estrutura

```bash
type RegisterLibrarian struct {
	Id    int    `json:"id"`
	Name  string `json:"name"`
	Cpf   string `json:"cpf"`
	Phone string `json:"phone"`
}
```
> NOTA: o `json: id` são tags que marcam os campos de uma struct, servindo para facilitar o manuseio desses campos em um banco de dados ou em uma estrutura json, por exemplo.
 
## Interfaces
> As interfaces são assinaturas de métodos, isto é, ela força determinadas classes a implementarem um método específico sem, no entanto, especificar como serão implementados. Em linhas gerais, pode-se entender as interfaces, a grosso modo, como um conjunto de métodos abstratos.

### Estrutura
```bash
type BookService interface {
	CreateBook(book domains.Book) (*domains.Book, error)
	UpdateBook(book domains.Book) (*domains.Book, error)
	FindBook(id int) (*domains.Book, error)
}
```
> NOTA: o `json: id` são tags que marcam os campos de uma struct, servindo para facilitar o manuseio desses campos em um banco de dados ou em uma estrutura json, por exemplo.


## Funções 
> As funções são entendidas como comportamentos próprios de uma struct.
> Exemplo: é próprio de um vendedor aplicar descontos em determinado produto se esta for a política de negócios a loja. Logo, uma possível função para uma struct ```seller``` seria applyDiscount().

* ```(s Seller)```: indica que esta função é específica da struct ```seller```, nenhuma outra struct pode implementá-la. 
* ```(plant templates.Plant)```: é o parâmetro recebido por esta função (variável seguida de tipo). 
* ```(float 32)```: é o retorno desta função, quando é retornado mais de uma variável é necessário o uso dos parênteses e da vírgula. 
```bash
func (s Seller) ApplyDiscount(plant templates.Plant) float32 {
	var discount float32
	fmt.Print("Insira o percentual de desconto: ")
	fmt.Scan(&discount)
	return plant.Price * discount / 100
}
```
## Métodos
> São comportamentos realizados por qualquer struct (sem restrição), seguindo a mesma lógica de estruturação da ```função```, com exceção de que não há um campo própria que designa quem irá executá-lo. 
 
```bash
func Payment(discount float32, plant templates.Plant) (float32, error, float32) {
	var valuePaid float32
	fmt.Print("Insira o valor a ser pago: ")
	fmt.Scan(&valuePaid)
	if valuePaid > plant.Price {
		return valuePaid - (plant.Price - discount), nil, 0
	} else {
		return valuePaid, errors.New("Saldo insuficiente!"), plant.Price - valuePaid
	}
}
```

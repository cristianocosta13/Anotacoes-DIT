# O que são testes unitários?

Os testes unitários servem o andamento da menor uniade da aplicação, como méodos ou classes, de maneira que funcionam ``isoladamente`` uma vez que precisam funcionar rapidamente. Devido a isso, não podem utilizar nenhum processo ou sistema externo.

# Como criar

Para desenvolver um teste unitário, você cria códigos (testes unitários) para resolver os problemas que surgem no desenvolvimento do código da aplicação funcional.

* Dê nomes que o ajudem a entender os requisitos do código em teste.
* Certifique-se de que um teste só tenha sucesso porque o código que ele testa está correto. 
* Assegure-se de que um teste só falha porque o código que ele testa está incorreto.
* Preze por criar mensagens curtas e significativas de falha que incluam parâmetros de teste relevantes. 
* Certifique-se de que cada teste possa produzir os resultados corretos (sucesso ou falha) mesmo quando for o único teste que você executar.

Para uma melhor compreensão, suponha a existência de uma classe pagamento que declara um ``método cobrar``, este ``recebendo um cliente`` como parâmetro.

```
public class Pagamento {

  public void cobrar(Cliente cliente) {
      // Remove créditos do cliente
  }
}
```

Um exemplo prático de como se daria um teste unitário para tal método é o seguinte: 

```
public class PagamentoTest {

    @Test
    public void testRemoverCreditosCliente() {
     Cliente cliente = ClienteDao.getCliente();
     float saldoAnterior = cliente.getSaldo();
     ...

    Pagamento pagamento = new Pagamento();
    pagamento.cobrar(cliente);

      Assert.assertTrue(cliente.getSaldo() < saldoAnterior);
    }
}
```

# Material de apoio:

> DevCast - O que são Testes Unitários: [https://www.devmedia.com.br/e-ai-como-voce-testa-seus-codigos/](https://www.devmedia.com.br/e-ai-como-voce-testa-seus-codigos/39478)

> Testes Unitários: Tutorial Sobre o que é, Como Fazer + Ferramentas a Utilizar
: [https://www.digite.com/pt-br/agile/testes-unitarios/](https://www.digite.com/pt-br/agile/testes-unitarios/)

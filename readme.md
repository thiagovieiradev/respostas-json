### Acesso

Vou passar, usando POST, login (que vai ser o código do PDV), senha e o número do terminal (maquininha) que o pdv esta usando para acessar.  
```
{
  "login" : "254",
  "senha" : "123456",
  "terminal" : "ABC123"  
}
```  

Deve conferir se o pdv que esta logando pode usar o terminal em questão.  
Para isso já deve existir a tela de cadastro de terminal e o relacionamento entre terminais e pdv.  

Em caso de sucesso, deve retornar:


```
{
  "status" : true,
  "id" : 1,
  "nome" : "Thiago Vieira",
  "email" : "thiagosilva.vieira@hotmail.com"  
}
```

Caso ele não possa usar o terminal:


```
{
  "status" : false,
  "message" : "Seu usuário não possui permissão para usar esse terminal. Por favor, contate a Bilhete Premium."  
}
```
Caso o login seja inválido:

```
{
  "status" : false,
  "message" : "Login ou senha inválidos. Tente novamente!"  
}
```

--------------------------------------------------------------------------------------------------  

### Eventos

Após o acesso, deve listar os eventos ativos e válidos para o PDV em questão.  

Exemplo de resposta com uma lista de eventos:  

__logo__: Se o evento possui logomarca para imprimir no ingresso  
__limitado (true ou false)__: Se o evento tem limite de venda por CPF  
__identificar (true ou false)__: Se é obrigatória a identificação dos ingressos  
__max_parcelas__: Maximo de parcelas no crédito  


```
[
  {
    "id": 1,
    "nome": "Henrique e Juliano",
    "local": "Avenida Beira Rio",
    "cidade" : "Colatina",
    "estado" : "ES",
    "logo" : "",
    "organizacao" : "Eventos Produções",
    "classificacao" : "12 Anos",
    "imagem": "https://bilhetepremium.com.br/assets/uploads/eventos/1656694470_52305402bfed75c0b9b2.jpeg",
    "data": "2022-09-22 14:00:00", 
    "limitado" : false, 
    "identificar" : false,
    "max_parcelas" : 5
  },
  {
    "id": 2,
    "nome": "Jota Quest",
    "local": "Ponte de Ferro",
    "cidade" : "Baixo Guandu",
    "estado" : "ES",
    "logo" : "",
    "organizacao" : "Plus Produções",
    "classificacao" : "16 Anos",
    "imagem": "https://bilhetepremium.com.br/assets/uploads/eventos/1656694470_52305402bfed75c0b9b2.jpeg",
    "data": "2022-11-10 22:00:00", 
    "limitado" : true,
    "identificar" : false,
    "max_parcelas" : 2
  }
]
```

#### Evento limitado por CPF

Quando um evento é limitado por CPF, deve existir um endpoint para que eu consiga confirmar se o CPF do comprador está liberado para efetuar compras em um evento.  
Ou seja, no aplicativo, quando o PDV clicar em um evento, caso ele seja limitado por CPF, vai aparecer um campo para que seja digitado o CPF do comprador. Assim que  



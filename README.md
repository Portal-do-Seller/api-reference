# Portal do Seller - API

#### Bem vindo a API Reference do Portal do Seller.

A API Portal do Seller foi desenvolvida de acordo com os melhores padrões [REST](https://en.wikipedia.org/wiki/Representational_State_Transfer).

As operações são feitas por requisições aos endpoints, de acordo com os verbos HTTP, com corpos de mensagem em JSON. As respostas podem ser interpretadas através do código de status HTTP. Isso permite que quaisquer aplicações consumam a API de forma simples e clara, independente da linguagem utilizada.

# Por onde eu começo?

1. Acesse a nossa [_central de desenvolvedores_](https://developers.portaldoseller.com.br/) e crie sua conta como Developer,
2. Após acessar a Central, crie sua primeira aplicação inserindo as seguintes informações:
   - **Nome da aplicação**: nome que será público sobre a sua aplicação para todos os usuários
   - **Nome curto**: nome curto para sua aplicação que será usado para montar a sua URL. Não coloque acentos ou caracteres especiais no _nome curto_.
   - **Logotipo**: insira uma logotipo para sua aplicação
   - **URL de notificação (Webhook)**: Essa é uma URL do seu sistema que irá então receber notificações sobre as alterações ocorridas dentro do Portal do Seller, referente a conta da empresa que autorizou a sua aplicação.

# Fazendo uma requisição
Todos os URLs começam com **https://api.portaldoseller.com.br/v1**. **Apenas SSL**.\
O caminho é prefixado com a versão da API. Se mudarmos a API de maneiras incompatíveis com versões anteriores, iremos bater no marcador de versão e manter o suporte estável para os URLs antigos.

Para fazer uma solicitação de todos os pedidos do seu cliente, por exemplo, você faria o seguinte no curl:
```sh
curl -H 'Authentication: Bearer AUTHORIZE_TOKEN ' \
  -H 'Content-Type: application/json' \
  https://api.portaldoseller.com/v1/orders
```
Onde o **AUTHORIZE_TOKEN** é o token de acesso da conta do seu cliente para a sua aplicação dentro do Portal do Seller (consulte Autenticação).

# Autenticação
Sua aplicação (criada em _Por onde eu começo?_) possui 02 informações essenciais:

1. **Access Key**: identificador único de sua aplicação dentro do nosso ambiente.
2. **Access Token**: seu token de acesso dentro do nosso ambiente. _Não compartilhe essa informação_

### Autorizando sua aplicação:

Ao obter as credenciais de sua aplicação, o próximo passo é fazer com que seu cliente autorize a conexão entre o Portal do Seller e sua aplicação. Para isso, siga os passos:

1. **Link de autorização**: Você deverá passar para o seu cliente um link de autorização para que ele aceite a nossa conexão com a sua aplicação. Esse link deverá conter dois parâmetros na URL, são eles:

   - **appId**: o parâmetro _appId_ deverá conter o **Access Key** da sua aplicação.
   - **redirect_url**: esse parâmetro deverá ser uma URL do seu sistema preparada para receber uma requisição POST, que faremos no ato da autorização para validar a conexão.

* Exemplo do Link de autorização: **https://sandboxapp.portaldoseller.com.br/apps/authorize?appId=168774&redirect_url=https%3A%2F%2Fapi.seusistema.com.br%2Fredirect**
##
Ao clicar no link, seu cliente irá efetuar o login dentro do nosso sistema e autorizará a conexão com a sua aplicação.
![](/imgs/app_authorize_example.png)
##
Assim que seu cliente clicar em **"Autorizar conexão"**, faremos uma requisição POST para o parâmetro _redirect_url_ informado, passando como body as seguintes informações:
| Parâmetro       | Explicação                                                                              |
|-----------------|-----------------------------------------------------------------------------------------|
| companyId       | Identificador da conta do seu cliente dentro do Portal do Seller                        |
| authorize_token | Token que vincula a sua aplicação com a conta do seu cliente dentro do Portal do Seller |
|                 |                                                                                         |
```sh
{
   companyId: 123456,
   authorize_token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ImV5SnBaRWx1ZEdWbmNtRjBiM0lpT2pVc0ltR
}
```
##
Ao receber nossa requisição, você deverá realizar uma requisição POST para nossa URL para validar a conexão com a sua aplicação.

## POST /apps/confirm-connection
| Parâmetro       | Explicação                                                                              |
|-----------------|-----------------------------------------------------------------------------------------|
| companyId       | Identificador da conta do seu cliente dentro do Portal do Seller                        |
| authorize_token | Token que vincula a sua aplicação com a conta do seu cliente dentro do Portal do Seller |
| access_token    | Access Token único da sua aplicação                                                     |

`body`
```sh
{
   companyId: 123456,
   authorize_token: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.ImV5SnBaRWx1ZEdWbmNtRjBiM0lpT2pVc0ltR,
   access_token: ciOiJIUzI1NiJ9.ImV5SnBaRWx1ZEdWbmNtRjBiM0lpT2pVc0ltRasdasf1QiLCJhbGciOiJIUzI1Ni
}
```
`HTTP/1.1 200 OK`
```sh
{
   Code: 000,
   Type: "Success",
   Message: "Aplicação autorizada com sucesso.",
   Data: null
}
```

# Tabela de códigos e erros
| Código          | Explicação                                                                              |
|-----------------|-----------------------------------------------------------------------------------------|
| 000             | Requisição realizada com sucesso                                                        |
| 400             | Requisição mal sucedida                                                                 |
| 001             | Dados incompletos - Algum parâmetro obrigatório está faltando ser enviado na requisição |

# Recursos da API Portal do Seller
   * [Produtos](/resources/product.md)

# Ajude-nos a melhorar nossa API
Diga-nos como podemos melhorar a API. Se você tiver uma solicitação de recurso específica ou se encontrou um bug, por favor, use o GitHub Issues. Sinta-se à vontade para realizar _fork_ desses documentos e enviar uma solicitações de _pull_ com melhorias.

Para falar conosco sobre a API, sinta-se à vontade para escrever para [api@portaldoseller.com.br](mailto:api@portaldoseller.com.br).

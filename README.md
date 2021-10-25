# Portal do Seller - API

#### Bem vindo a API Reference do Portal do Seller.

A API Portal do Seller foi desenvolvida de acordo com os melhores padrões [REST](https://en.wikipedia.org/wiki/Representational_State_Transfer).

As operações são feitas por requisições aos endpoints, de acordo com os verbos HTTP, com corpos de mensagem em JSON. As respostas podem ser interpretadas através do código de status HTTP. Isso permite que quaisquer aplicações consumam a API de forma simples e clara, independente da linguagem utilizada.

# Autenticação

#### Obtendo sua Chave de API

Antes de começar, você precisa obter suas chaves de API.
Para isso, siga os seguintes passos:

1. Acesse a nossa [_central de desenvolvedores_](https://developers.portaldoseller.com.br/) e faça login com seu usuário,
2. Após acessar a Central, crie sua primeira aplicação inserindo as seguintes informações:
   - **Nome da aplicação**: nome que será público sobre a sua aplicação para todos os usuários
   - **Nome curto**: nome curto para sua aplicação que será usado para montar a sua URL. Não coloque acentos ou caracteres especiais no _nome curto_.
   - **Logotipo**: insira uma logotipo para sua aplicação
   - **URL de notificação (Webhook)**: Essa é uma URL do seu sistema que irá então receber notificações sobre as alterações ocorridas dentro do Portal do Seller, referente a conta da empresa que autorizou a sua aplicação.

Após criar sua aplicação, nós disponibilizaremos 02 informações para você:

1. **Access Key**: esse será o identificador único de sua aplicação dentro do nosso ambiente.
2. **Access Token**: esse será o seu token de acesso dentro do nosso ambiente. _Não compartilhe essa informação_

### Autorizando sua aplicação:

Ao obter as credenciais de sua aplicação, o próximo passo é fazer com que seu cliente autorize a conexão entre o Portal do Seller e sua aplicação. Para isso, siga os passos:

1. **Link de autorização**: Você deverá passar para o seu cliente um link de autorização para que ele aceite a nossa conexão com a sua aplicação. Esse link deverá conter dois parâmetros na URL, são eles:

   - **appId**: o parâmetro _appId_ deverá conter o **Access Key** da sua aplicação.
   - **redirect_url**: esse parâmetro deverá ser uma URL do seu sistema, para qual faremos uma requisição POST no ato da autorização, passando como _body_ o **companyId** (identificador do seu cliente em nosso sistema ) e também um **authorize_token** que vincula a sua aplicação com o seu cliente dentro de nosso sistema.

* Exemplo do Link de autorização: **https://sandboxapp.portaldoseller.com.br/apps/authorize?appId=168774&redirect_url=https%3A%2F%2Fapi.seusistema.com.br%2Fredirect**

[](/imgs/app_authorize_example.png)

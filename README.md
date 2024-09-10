# Portal do Seller - API

#### Bem vindo a API Reference do Portal do Seller.

A API Portal do Seller foi desenvolvida de acordo com os melhores padrões [REST](https://en.wikipedia.org/wiki/Representational_State_Transfer).

As operações são feitas por requisições aos endpoints, de acordo com os verbos HTTP, com corpos de mensagem em JSON. As respostas podem ser interpretadas através do código de status HTTP. Isso permite que quaisquer aplicações consumam a API de forma simples e clara, independente da linguagem utilizada.

# Por onde eu começo?

## Autenticação

Para acessar os recursos da nossa API, é necessário autenticar-se utilizando uma Chave de API. A autenticação é feita através do cabeçalho HTTP `Authorization`, seguindo o padrão da HTTP Basic Authentication.

### Obtendo sua Chave de API

Antes de começar a fazer requisições para a API, você precisa obter suas chaves de API. Siga os passos abaixo:

1. **Acesse o Portal**: [Clique aqui](https://app.portaldoseller.com.br) para acessar o portal de autenticação e faça login com seu usuário.
2. **Acesse Configurações**: Após o login, navegue até a área de **Configurações**.
3. **Integrações**: Dentro de Configurações, clique em **Integrações**.
4. **Criação da Chave de API**: Caso ainda não tenha uma chave de API, clique no botão **Criar chave de API** e siga o passo a passo para gerar sua chave.

# Fazendo uma requisição
Todos os URLs começam com **https://api.portaldoseller.com.br/v2**. **Apenas SSL**.\
O caminho é prefixado com a versão da API. Se mudarmos a API de maneiras incompatíveis com versões anteriores, iremos bater no marcador de versão e manter o suporte estável para os URLs antigos.

Para fazer uma solicitação de todos os pedidos do seu cliente, por exemplo, você faria o seguinte no curl:
```sh
curl -H 'Authorization: Basic CHAVE_DE_API' \
     -H 'Content-Type: application/json' \
     -H 'grand_type: integrate' \
     https://api.portaldoseller.com.br/v2/products
```
Onde o **CHAVE_DE_API** é o token de acesso da sua conta.

## Recursos da API Portal do Seller
   * ### [Produtos](/resources/product.md)

## Ajude-nos a melhorar nossa API
Diga-nos como podemos melhorar a API. Se você tiver uma solicitação de recurso específica ou se encontrou um bug, por favor, use o GitHub Issues. Sinta-se à vontade para realizar _fork_ desses documentos e enviar uma solicitações de _pull_ com melhorias.

Para falar conosco sobre a API, sinta-se à vontade para escrever para [suporte@portaldoseller.com.br](mailto:suporte@portaldoseller.com.br).

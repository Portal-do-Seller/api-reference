# Produtos
Um Produto é um item à venda em uma conta de seller cadastrada no Portal. Por hora, são aceitos apenas itens físicos para venda.

### Visão geral sobre Produto
O objeto Produto contém as seguintes propriedades:

| Atributo        | Tipo    | Descrição                                                                               |
|-----------------|---------|-----------------------------------------------------------------------------------------|
| product_id      | integer | Identificador único para o produto dentro do Portal do Seller                           |
| title           | string  | Nome do seu produto                                                                     |
| description     | text    | Descrição do produto                                                                    |
| brand           | string  | Marca/Fabricante do produto                                                             |
| weight          | decimal | Peso do produto com a embalagem (aquela que você utiliza, não a da empresa de frete)    |
| height          | decimal | Altura do produto com a embalagem (aquela que você utiliza, não a da empresa de frete)  |
| width           | decimal | Largura do produto com a embalagem (aquela que você utiliza, não a da empresa de frete) |
| length          | decimal | Comprimento do produto com a embalagem (aquela que você utiliza, não a da empresa de frete)|
| warrantyTime    | integer | Quantidade de meses de garantia do produto |
| model           | string  | Modelo do produto |
| ncm             | string  | Código NCM do produto [(O que é NCM?)](https://www.fazcomex.com.br/blog/tabela-ncm/) |
| gender          | string  | Gênero alvo para qual o produto está sendo vendido (Masculino, Feminino ou Unissex)  |
| videoUrl        | string  | Link do vídeo sobre o produto  |
| grids           | string  | Lista de objetos de [Grade do Produto](product_grid.md), que representam diferentes versões do mesmo produto  |
| images          | string  | Lista de objetos de [Imagem do Produto](product_image.md), que representam as imagens do produto  |


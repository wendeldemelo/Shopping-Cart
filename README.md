# Boas vindas ao repositório do projeto de Carrinho de Compras!

#VQV 🚀

Aqui você vai encontrar os detalhes de como foi estruturado o projeto a partir desse repositório.

**Para acessar a aplicação em execução clique aqui (https://wendeldemelo.github.io/Shopping-Cart/)**

---

## SUMÁRIO

- [Habilidades](#habilidades)
  - [O que foi desenvolvido](#o-que-foi-desenvolvido)
    - [Protótipo do projeto](#protótipo-do-projeto)
- [Desenvolvimento](#desenvolvimento)
  - [Durante o desenvolvimento](#durante-o-desenvolvimento)
  - [ESLint e Stylelint](#eslint-e-stylelint)
- [Requisitos do projeto](#requisitos-do-projeto)
  - [API Shopping Cart](#api-shopping-cart)
  - [1. Listagem de produtos](#1-listagem-de-produtos)
  - [2. Adicione o produto ao carrinho de compras](#2-adicione-o-produto-ao-carrinho-de-compras)
  - [3. Remova o item do carrinho de compras ao clicar nele](#3-remova-o-item-do-carrinho-de-compras-ao-clicar-nele)
  - [4. Carregue o carrinho de compras através do **LocalStorage** ao iniciar a página](#4-carregue-o-carrinho-de-compras-através-do-LocalStorage-ao-iniciar-a-página)
  - [5. Soma do valor total dos itens do carrinho de compras](#5-soma-do-valor-total-dos-itens-do-carrinho-de-compras)
  - [6. Botão para limpar carrinho de compras](#6-botão-para-limpar-carrinho-de-compras)
  - [7. Texto de "loading" durante uma requisição à API](#7-texto-de-loading-durante-uma-requisição-à-api)
- [Depois de terminar o desenvolvimento](#depois-de-terminar-o-desenvolvimento)

---

## Habilidades

Nesse projeto, você verá:

- Requisições a uma API *(Application Programming Interface)* do Mercado Livre;
- Aplicação de conhecimentos sobre JavaScript, CSS e HTML;
- Funções assíncronas;

---

## O que foi desenvolvido

Nesse projeto foi desenvolvido um **carrinho de compras** totalmente dinâmico! E o melhor: consumindo dados diretamente de uma **API!** Isso mesmo. Da sigla em inglês _Application Programming Interface_, uma API é um ponto de contato na internet com determinado serviço. Através de **requisições HTTP** a essa API é possível interagir com ela da forma como quem a criou planejou. Aqui usaremos a API do Mercado Livre para buscarmos produtos à venda.

### Protótipo do projeto

O projeto tem o comportamento de acordo com o do gif abaixo:

![Project Gif](./out.gif)

---

# Desenvolvimento

O projeto contem os principais arquivos `index.html`, `style.css` e `script.js`, que contem o código HTML, CSS e JavaScript, respectivamente.

---

## Durante o desenvolvimento

* Foram feitos `commits` das alterações feitas no código regularmente;

* Após um ou alguns `commits` foi atualizado o repositório remoto (o famoso `git push`);

* Os comandos utilizados com mais frequência foram:

  1. `git status` _(para verificar o que está em vermelho - fora do stage - e o que está em verde - no stage)_;

  2. `git add` _(para adicionar arquivos ao stage do Git)_;

  3. `git commit` _(para criar um commit com os arquivos que estão no stage do Git)_;

  4. `git push -u nome-da-branch` _(para enviar o commit para o repositório remoto na primeira vez que fizer o `push` de uma nova branch)_;

  5. `git push` _(para enviar o commit para o repositório remoto após o passo anterior)_.

---

### ESLint e Stylelint

Para garantir a qualidade do código, foi utilizado neste projeto os linters `ESLint` e `Stylelint`.
Assim o código foi alinhado com as boas práticas de desenvolvimento, sendo mais legível
e de fácil manutenção! Para rodá-los localmente no projeto, foi executado os comandos abaixo:

```bash
  npm run lint
  npm run lint:styles
```

⚠️ Lembre-se esse projeto foi verificado passando pelos _checks_ do **linter**.

---

# Requisitos do projeto

## API Shopping Cart

O [manual da API do Mercado Livre](https://developers.mercadolivre.com.br/pt_br/itens-e-buscas) contém muitas informações sobre ela. Foi utilizado alguns dos _endpoints_, e a forma de uso está detalhada no primeiro requisito.

### 1. Listagem de produtos

Foi criada uma listagem de produtos que foram consultados através da API do Mercado Livre.

Foi utilizado o _endpoint_:
```javascript
"https://api.mercadolibre.com/sites/MLB/search?q=$QUERY"
```
onde `$QUERY` deve ser o valor da busca. Para este trabalho, a busca foi feita com o termo `computador`.

O retorno desse _endpoint_ será algo no formato `json`. Por exemplo, se for pesquisado "computador":
```json
{
    "site_id": "MLB",
    "query": "computador",
    "paging": {
        "total": 406861,
        "offset": 0,
        "limit": 50,
        "primary_results": 1001
    },
    "results": [
        {
            "id": "MLB1341925291",
            "site_id": "MLB",
            "title": "Processador Intel Core I5-9400f 6 Núcleos 128 Gb",
            "seller": {
                "id": 385471334,
                "permalink": null,
                "power_seller_status": null,
                "car_dealer": false,
                "real_estate_agency": false,
                "tags": []
            },
            "price": 899,
            "currency_id": "BRL",
            "available_quantity": 1,
            "sold_quantity": 0,
            "buying_mode": "buy_it_now",
            "listing_type_id": "gold_pro",
            "stop_time": "2039-10-10T04:00:00.000Z",
            "condition": "new",
            "permalink": "https://www.mercadolivre.com.br/processador-intel-core-i5-9400f-6-nucleos-128-gb/p/MLB13953199",
            "thumbnail": "http://mlb-s2-p.mlstatic.com/813265-MLA32241773956_092019-I.jpg",
            "accepts_mercadopago": true,
            "installments": {
                "quantity": 12,
                "amount": 74.92,
                "rate": 0,
                "currency_id": "BRL"
            },
            "address": {
                "state_id": "BR-SP",
                "state_name": "São Paulo",
                "city_id": "BR-SP-27",
                "city_name": "São José dos Campos"
            },
            "shipping": {
                "free_shipping": true,
                "mode": "me2",
                "tags": [
                    "fulfillment",
                    "mandatory_free_shipping"
                ],
                "logistic_type": "fulfillment",
                "store_pick_up": false
            },
            "seller_address": {
                "id": "",
                "comment": "",
                "address_line": "",
                "zip_code": "",
                "country": {
                    "id": "BR",
                    "name": "Brasil"
                },
                "state": {
                    "id": "BR-SP",
                    "name": "São Paulo"
                },
                "city": {
                    "id": "BR-SP-27",
                    "name": "São José dos Campos"
                },
                "latitude": "",
                "longitude": ""
            },
            "attributes": [
                {
                    "source": 1,
                    "id": "ALPHANUMERIC_MODEL",
                    "value_id": "6382478",
                    "value_struct": null,
                    "values": [
                        {
                            "name": "BX80684I59400F",
                            "struct": null,
                            "source": 1,
                            "id": "6382478"
                        }
                    ],
                    "attribute_group_id": "OTHERS",
                    "name": "Modelo alfanumérico",
                    "value_name": "BX80684I59400F",
                    "attribute_group_name": "Outros"
                },
                {
                    "id": "BRAND",
                    "value_struct": null,
                    "attribute_group_name": "Outros",
                    "attribute_group_id": "OTHERS",
                    "source": 1,
                    "name": "Marca",
                    "value_id": "15617",
                    "value_name": "Intel",
                    "values": [
                        {
                            "id": "15617",
                            "name": "Intel",
                            "struct": null,
                            "source": 1
                        }
                    ]
                },
                {
                    "name": "Condição do item",
                    "value_id": "2230284",
                    "attribute_group_id": "OTHERS",
                    "attribute_group_name": "Outros",
                    "source": 1,
                    "id": "ITEM_CONDITION",
                    "value_name": "Novo",
                    "value_struct": null,
                    "values": [
                        {
                            "id": "2230284",
                            "name": "Novo",
                            "struct": null,
                            "source": 1
                        }
                    ]
                },
                {
                    "id": "LINE",
                    "value_name": "Core i5",
                    "attribute_group_id": "OTHERS",
                    "attribute_group_name": "Outros",
                    "name": "Linha",
                    "value_id": "7769178",
                    "value_struct": null,
                    "values": [
                        {
                            "id": "7769178",
                            "name": "Core i5",
                            "struct": null,
                            "source": 1
                        }
                    ],
                    "source": 1
                },
                {
                    "id": "MODEL",
                    "value_struct": null,
                    "values": [
                        {
                            "id": "6637008",
                            "name": "i5-9400F",
                            "struct": null,
                            "source": 1
                        }
                    ],
                    "attribute_group_id": "OTHERS",
                    "name": "Modelo",
                    "value_id": "6637008",
                    "value_name": "i5-9400F",
                    "attribute_group_name": "Outros",
                    "source": 1
                }
            ],
            "differential_pricing": {
                "id": 33580182
            },
            "original_price": null,
            "category_id": "MLB1693",
            "official_store_id": null,
            "catalog_product_id": "MLB13953199",
            "tags": [
                "brand_verified",
                "good_quality_picture",
                "good_quality_thumbnail",
                "immediate_payment",
                "cart_eligible"
            ],
            "catalog_listing": true
        },
    ]
}
```
A lista de produtos que devem ser exibidos é o _array_ `results` no `JSON` acima.

Foi utilizada a função `createProductItemElement(product)` para criar os componentes _HTML_ referentes a um produto.

Foi adicionado o elemento retornado da função `createProductItemElement(product)` como filho do elemento `<section class="items">`.

**Obs:** as variáveis `sku`, no código fornecido, se referem aos campos `id` retornados pela API.

### 2. Adicione o produto ao carrinho de compras

Cada produto na página _HTML_ possui um botão com o nome `Adicionar ao carrinho!`.

Ao clicar nesse botão é realizada uma requisição para o _endpoint_:
```javascript
"https://api.mercadolibre.com/items/$ItemID"
```
onde `$ItemID` deve ser o valor `id` do item selecionado.

Quando colocado o id `MLB1341706310` retorno desse _endpoint_ será algo no formato:
```JSON
{
    "id": "MLB1341706310",
    "site_id": "MLB",
    "title": "Processador Amd Ryzen 5 2600 6 Núcleos 64 Gb",
    "subtitle": null,
    "seller_id": 245718870,
    "category_id": "MLB1693",
    "official_store_id": 1929,
    "price": 879,
    "base_price": 879,
    "original_price": null,
    "currency_id": "BRL",
    "initial_quantity": 0,
    "available_quantity": 0,
    "sold_quantity": 0,
    ...
    "warranty": "Garantia de fábrica: 3 anos",
    "catalog_product_id": "MLB9196241",
    "domain_id": "MLB-COMPUTER_PROCESSORS",
    "parent_item_id": null,
    "differential_pricing": null,
    "deal_ids": [],
    "automatic_relist": false,
    "date_created": "2019-10-15T18:13:00.000Z",
    "last_updated": "2019-12-20T18:06:54.000Z",
    "health": null,
    "catalog_listing": true
}
```
Preste atenção que o JSON deve conter apenas **um** item.

Foi utilizada a função `createCartItemElement()` para criar os componentes _HTML_ referentes a um item do carrinho.

Foi adicionado o elemento retornado da função `createCartItemElement(product)` como filho do elemento `<ol class="cart__items">`.

### 3. Remova o item do carrinho de compras ao clicar nele

Ao clicar no **produto no carrinho de compra**, ele deve ser removido da lista.
Para isso, foi utilizada uma função chamada `cartItemClickListener(event)` e foi implementada com a lógica necessária para realizar a remoção.

### 4. Carregue o carrinho de compras através do **LocalStorage** ao iniciar a página

Ao carregar a página, o estado atual do carrinho de compras deve ser carregado do **LocalStorage**.
Para que isso funcione, o carrinho de compras é salvo no **LocalStorage**, ou seja, todas as **adições** e **remoções** são abordadas para que a lista atual seja salva.

### 5. Soma do valor total dos itens do carrinho de compras

Cada vez que se adicionar um item ao carrinho de compras, seus valores são somados e apresentados na página principal do projeto. O elemento que tem como filho o preço total dos itens do carrinho é a classe `total-price`.

Obs: Aqui um ponto de atenção, pois estou buscando os dados do produto em uma API. Portanto, é necessário garantir que a API já retornou as informações para somente depois realizar o cálculo da soma.

### 6. Botão para limpar carrinho de compras

Foi criado um botão para remover todos os itens do carrinho de compras. Ele tem a classe `empty-cart`.

### 7. Texto de "loading" durante uma requisição à API

Uma requisição à API gasta um tempo e durante ele, ficamos sem saber se está tudo certo ou se algo deu errado.
Normalmente é utilizada alguma forma para mostrar que a requisição está em andamento.
Aqui a palavra "loading..." aparece na página **apenas durante** a requisição à API. O elemento mostrado durante o carregamento da página tem a classe `loading`.

---

## Depois de terminar o desenvolvimento

Foi sinalizado que o projeto foi concluído para o _"Code Review"_ dos meus colegas de turma em meu _Pull Request_.

---

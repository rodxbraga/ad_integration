### Categoria `Casas`

Para esta categoria, é necessário preencher o parâmetro `category` com o valor `1040`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `rooms` | `0` para 0 quartos<br> `1` para 1 quarto<br> `2` para 2 quartos<br> `3` para 3 quartos<br> `4` para 4 quartos<br> `5` para 5 ou mais quartos<br> | string | Sim | Quantidade de quartos |
| `bathrooms` | `1` para 1 banheiro<br> `2` para 2 banheiros<br> `3` para 3 banheiros<br> `4` para 4 banheiros<br> `5` para 5 ou mais banheiros<br> | string | Não | Quantidade de banheiros |
| `garage_spaces` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | string | Não | Quantidade de vagas de garagem |
| `size` |  | string numérica | Não | Área do apartamento (m²) |
| `home_type` | `1` para Padrão<br> `2` para Casa de vila<br> `3` para Casa de condomínio | string | Sim | Tipo de casa |
| `home_features` | `1` para Ar condicionado<br>`2` para Piscina<br>`3` para Armários no quarto<br> `4` para Varanda<br> `5` para Área de serviço<br> `6` para Churrasqueira<br> `7` para Quarto de serviço<br> `8` para Porteiro 24h<br> `9` para Armários na cozinha<br> `10` para Mobiliado | array de strings | Não | Detalhes do imóvel |
| `home_complex_features` | `1` para Condomínio fechado<br> `2` para Segurança 24h<br> `3` para Área murada<br> `4` para Permitido animais<br> `5` para Portão eletrônico<br> `6` para Academia<br> `9` para Piscina | array de strings | Não | Detalhes do condomínio |
| `price` |  | integer | Não | Preço de venda ou aluguel do imóvel |
| `iptu` |  | string numérica | Não | Valor mensal do IPTU |
| `condominio` |  | string numérica | Não | Valor mensal do condomínio |

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Apartamentos`:

```json
[
    {
        "id": "5555555555",
        "operation": "insert",
        "category": 1040,
        "subject": "Casa à Venda Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 1000500,
        "zipcode": "24230090",
        "params": {
            "rooms": "3",
            "bathrooms": "2",
            "garage_spaces": "2",
            "size": "150",
            "iptu": 1000,
            "condominio": 500,
            "home_type": "3",
            "home_features": [
                "1",
                "2"
            ],
            "home_complex_features": [
                "1",
                "2"
            ]
        },
        "images": [
            "http://www.a.com/image1.png",
            "http://www.a.com/image2.png"
        ]
    },
    {
        "id": "66666666",
        "operation": "insert",
        "category": 1040,
        "subject": "Casa para Alugar Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "u",
        "price": 1500,
        "zipcode": "24230090",
        "params": {
            "rooms": "3",
            "bathrooms": "2",
            "garage_spaces": "2",
            "size": "150",
            "iptu": 1000,
            "condominio": 500,
            "home_type": "3",
            "home_features": [
                "1",
                "2"
            ],
            "home_complex_features": [
                "1",
                "2"
            ]
        },
        "images": [
            "http://www.a.com/image1.png",
            "http://www.a.com/image2.png"
        ]
    }
]
```
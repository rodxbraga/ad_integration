### Subcategoria `Terrenos, sítios e fazendas`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `1100`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `size` |  | string numérica | Não<sup>1</sup> | Área do imóvel (m²) |
| `re_land_type` | `1` para Terrenos e lotes<br> `2` para Sítios e chácaras<br> `3` para Fazendas<br> `4` para Outros | string | Sim | Tipo de imóvel |
| `re_land_features` | `1` para Área verde<br> `2` para Casa sede<br> `3` para Pomar<br> `4` para Piscina<br> `5` para Churrasqueira<br> `6` para Poço artesiano<br> `7` para Água encanada<br> `8` para Energia elétrica<br> `9` para Campo de futebol<br> `10` para Acesso asfaltado | array de strings | Não<sup>1</sup> | Detalhes do imóvel |
| `iptu` |  | string numérica | Não<sup>1</sup> | Valor mensal do IPTU |
| `condominio` |  | string numérica | Não<sup>1</sup> | Valor mensal do condomínio |

<sup>1</sup>: Se você não quer enviar um parâmetro não-obrigatório, deixe de enviar o parâmetro no payload. Se você enviar o parâmetro com valor vazio ou `0`, a operação vai falhar (a menos, é claro, que o valor `0` seja esperado para esse parâmetro).

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Terrenos, sítios e fazendas`:

```json
[
    {
        "id": "5555555555",
        "operation": "insert",
        "category": 1100,
        "subject": "Terreno à Venda Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 1000500,
        "zipcode": "24230090",
        "params": {
            "size": "150",
            "iptu": 1000,
            "condominio": 500,
            "re_land_type": "2",
            "re_land_features": [
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
        "category": 1100,
        "subject": "Terreno à Venda Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 1000500,
        "zipcode": "24230090",
        "params": {
            "size": "150",
            "iptu": 1000,
            "condominio": 500,
            "re_land_type": "2",
            "re_land_features": [
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
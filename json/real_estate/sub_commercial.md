### Subcategoria `Comércio e indústria`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `1120`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `garage_spaces` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | string | Não<sup>1</sup> | Quantidade de vagas de garagem |
| `size` |  | string numérica | Não<sup>1</sup> | Área do imóvel (m²) |
| `commercial_type` | `1` para Escritório<br> `2` para Galpão/Depósito<br> `3` para Hotel<br> `4` para Fábrica<br> `5` para Garagem/Vaga<br>`6` para Loja<br>`7` para Outros | string | Não<sup>1</sup> | Tipo de imóvel comercial |
| `commercial_features` | `1` para Garagem<br> `2` para Segurança 24h<br> `3` para Câmeras de segurança<br> `4` para Elevador<br> `5` para Portaria<br> `6` para Acesso para deficientes | array de strings | Não<sup>1</sup> | Detalhes do imóvel |
| `iptu` |  | string numérica | Não<sup>1</sup> | Valor mensal do IPTU |
| `condominio` |  | string numérica | Não<sup>1</sup> | Valor mensal do condomínio |

<sup>1</sup>: Se você não quer enviar um parâmetro não-obrigatório, deixe de enviar o parâmetro no payload. Se você enviar o parâmetro com valor vazio ou `0`, a operação vai falhar (a menos, é claro, que o valor `0` seja esperado para esse parâmetro).

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Comércio e indústria`:

```json
[
    {
        "id": "5555555555",
        "operation": "insert",
        "category": 1120,
        "subject": "Galpão à Venda Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 1000500,
        "zipcode": "24230090",
        "params": {
            "garage_spaces": "2",
            "size": "150",
            "iptu": "1000",
            "condominio": "500",
            "commercial_type": "2",
            "commercial_features": [
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
        "id": "666666666",
        "operation": "insert",
        "category": 1120,
        "subject": "Escritório à Venda Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 1000500,
        "zipcode": "24230090",
        "params": {
            "garage_spaces": "1",
            "size": "150",
            "iptu": "1000",
            "condominio": "500",
            "commercial_type": "2",
            "commercial_features": [
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

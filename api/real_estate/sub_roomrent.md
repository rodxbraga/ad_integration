### Categoria `Aluguel de quartos`

Para esta categoria, é necessário preencher o parâmetro `category` com o valor `1060`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `room_rent_features` | `1` para Armário no quarto<br> `2` para Banheiro no quarto<br> `3` para Mobiliado<br> `4` para Ar condicionado<br> `5` para Varanda<br> `6` para Aquecimento<br> `7` para Internet<br> `8` para TV a cabo | array de strings | Não | Detalhes do quarto |

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Aluguel de quartos`:

```json
{
    "access_token": "ca18abccaadd282490e75173f98b8ec6f0c1c6c8",
    "ad_list": [
        {
            "id": "5555555555",
            "operation": "insert",
            "category": 1060,
            "subject": "Quarto para Alugar Super Legal",
            "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
            "phone": 2155555555,
            "type": "s",
            "price": 1000,
            "zipcode": "24230090",
            "params": {
                "room_rent_features": [
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
            "id": "6666666",
            "operation": "insert",
            "category": 1060,
            "subject": "Quarto para Alugar Super Legal",
            "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
            "phone": 2155555555,
            "type": "s",
            "price": 1000,
            "zipcode": "24230090",
            "params": {
                "room_rent_features": [
                    "1",
                    "2"
                ]
            },
            "images": [
                "http://www.a.com/image1.png",
                "http://www.a.com/image2.png"
            ]
        },
    ]
}
```
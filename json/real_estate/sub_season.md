### Categoria `Temporada`

Para esta categoria, é necessário preencher o parâmetro `category` com o valor `1080`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `rooms` | `0` para 0 quartos<br> `1` para 1 quarto<br> `2` para 2 quartos<br> `3` para 3 quartos<br> `4` para 4 quartos<br> `5` para 5 ou mais quartos<br> | string | Sim | Quantidade de quartos |
| `bathrooms` | `1` para 1 banheiro<br> `2` para 2 banheiros<br> `3` para 3 banheiros<br> `4` para 4 banheiros<br> `5` para 5 ou mais banheiros<br> | string | Não | Quantidade de banheiros |
| `garage_spaces` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | string | Não | Quantidade de vagas de garagem |
| `beds` | `1` para 1 cama<br> `2` para 2 camas<br> `3` para 3 camas<br> `4` para 4 camas<br> `5` para 5 camas<br> `6` para 6 camas<br>`7` para 7 camas<br>`8` para 8 camas<br>`9` para 9 camas<br>`10` para 10 camas<br>`11` para 11 camas<br>`12` para 12 camas<br>`13` para 13 camas<br>`14` para 14 camas<br>`15` para 15 camas<br>`16` para 20 camas<br>`17` para 25 camas<br>`18` para 30 ou mais camas | string | Sim | Quantidade de camas |
| `size` |  | string numérica | Não | Área do apartamento (m²) |
| `season_type` | `1` para Apartamento<br> `2` para Casa<br> `3` para Quarto individual<br> `4` para Quarto compartilhado<br> `5` para Hotel, hostel e pousada<br>`6` para Sítio, fazenda e chácara | string | Sim | Tipo de imóvel |
| `season_features` | `1` para Ar condicionado<br> `2` para Aquecimento<br> `3` para Café da manhã<br> `4` para Churrasqueira<br> `5` para Estacionamento<br> `6` para Fogão<br> `7` para Geladeira<br> `8` para Internet<br> `9` para Lareira<br> `10` para Máquina de lavar<br> `11` para Permitido animais<br> `12` para Piscina<br> `13` para Roupa de cama<br> `14` para Toalhas<br> `15` para TV a cabo<br> `16` para Ventilador<br> `17` para Varanda/Terraço | array de strings | Não | Detalhes do imóvel |
| `rent_type` | `1` para Por dia<br> `2` para Por semana<br> `3` para Por mês<br> `4` para Pacote | string | Não | Tipo de pagamento |

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Temporada`:

```json
[
    {
        "id": "5555555555",
        "operation": "insert",
        "category": 1080,
        "subject": "Casa para Aluguel de Temporada Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 150,
        "zipcode": "24230090",
        "params": {
            "rooms": "3",
            "bathrooms": "2",
            "garage_spaces": "2",
            "beds": "10",
            "size": "150",
            "rent_type": "1",
            "season_type": "2",
            "season_features": [
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
        "category": 1080,
        "subject": "Casa para Aluguel de Temporada Super Legal",
        "body": "Descrição do anúncio\nNova linha da descrição\nAinda outra linha da descrição",
        "phone": 2155555555,
        "type": "s",
        "price": 150,
        "zipcode": "24230090",
        "params": {
            "rooms": "3",
            "bathrooms": "2",
            "garage_spaces": "2",
            "beds": "10",
            "size": "150",
            "rent_type": "1",
            "season_type": "2",
            "season_features": [
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
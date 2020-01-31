### Subcategoria `Apartamentos`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `1020`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `rooms` | `0` para 0 quartos<br> `1` para 1 quarto<br> `2` para 2 quartos<br> `3` para 3 quartos<br> `4` para 4 quartos<br> `5` para 5 ou mais quartos<br> | string | Sim | Quantidade de quartos |
| `bathrooms` | `1` para 1 banheiro<br> `2` para 2 banheiros<br> `3` para 3 banheiros<br> `4` para 4 banheiros<br> `5` para 5 ou mais banheiros<br> | string | Não<sup>1</sup> | Quantidade de banheiros |
| `garage_spaces` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | string | Não<sup>1</sup> | Quantidade de vagas de garagem |
| `size` |  | string numérica | Não<sup>1</sup> | Área do apartamento (m²) |
| `apartment_type` | `1` para Padrão<br> `2` para Cobertura<br> `3` para Duplex/triplex<br> `4` para Kitnet<br> `5` para Loft | string | Sim | Tipo de apartamento |
| `apartment_features` | `1` para Ar condicionado<br> `2` para Academia<br> `3` para Armários no quarto<br> `4` para Varanda<br> `5` para Área de serviço<br> `6` para Academia<br> `7` para Quarto de serviço<br> `8` para Piscina<br> `11` para Armários na cozinha<br> `12` para Mobiliado | array de strings | Não<sup>1</sup> | Detalhes do imóvel|
| `apartment_complex_features` | `1` para Condomínio fechado<br> `2` para Elevador<br> `3` para Segurança 24h<br> `4` para Portaria<br> `5` para Permitido animais<br> `6` para Academia<br> `7` para Piscina<br> `8` para Salão de festas<br> | array de strings | Não<sup>1</sup> | Detalhes do condomínio |
| `iptu` |  | string numérica | Não<sup>1</sup> | Valor mensal do IPTU |
| `condominio` |  | string numérica | Não<sup>1</sup> | Valor mensal do condomínio |

<sup>1</sup>: Se você não quer enviar um parâmetro não-obrigatório, deixe de enviar o parâmetro no payload. Se você enviar o parâmetro com valor vazio ou `0`, a operação vai falhar (a menos, é claro, que o valor `0` seja esperado para esse parâmetro).

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Apartamentos`:

```json
{
    "access_token": "ca18abccaadd282490e75173f98b8ec6f0c1c6c8",
    "ad_list": [
        {
            "id": "5555555555",
            "operation": "insert",
            "category": 1020,
            "subject": "Apartamento à Venda Super Legal",
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
                "iptu": "1000",
                "condominio": "500",
                "apartment_type": "3",
                "apartment_features": [
                    "1",
                    "2"
                ],
                "apartment_complex_features": [
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
            "category": 1020,
            "subject": "Apartamento para Alugar Super Legal",
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
                "iptu": "1000",
                "condominio": "500",
                "apartment_type": "3",
                "apartment_features": [
                    "1",
                    "2"
                ],
                "apartment_complex_features": [
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
}
```
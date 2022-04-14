### Subcategoria `Carros, vans e utilitários`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `2020`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `regdate` | `2023` para 2023<br> `2022` para 2022<br> `2021` para 2021<br> `2020` para 2020<br> `2019` para 2019<br> `2018` para 2018<br> `2017` para 2017<br> `2016` para 2016<br> `2015` para 2015<br> `2014` para 2014<br> `2013` para 2013<br> `2012` para 2012<br> `2011` para 2011<br> `2010` para 2010<br> `2009` para 2009<br> `2008` para 2008<br> `2007` para 2007<br> `2006` para 2006<br> `2005` para 2005<br> `2004` para 2004<br> `2003` para 2003<br> `2002` para 2002<br> `2001` para 2001<br> `2000` para 2000<br> `1999` para 1999<br> `1998` para 1998<br> `1997` para 1997<br> `1996` para 1996<br> `1995` para 1995<br> `1994` para 1994<br> `1993` para 1993<br> `1992` para 1992<br> `1991` para 1991<br> `1990` para 1990<br> `1989` para 1989<br> `1988` para 1988<br> `1987` para 1987<br> `1986` para 1986<br> `1985` para 1985<br> `1984` para 1984<br> `1983` para 1983<br> `1982` para 1982<br> `1981` para 1981<br> `1980` para 1980<br> `1975` para Entre 1975 e 1980<br> `1970` para Entre 1970 a 1975<br> `1965` para Entre 1965 e 1970<br> `1960` para Entre 1960 e 1965<br> `1955` para Entre 1955 e 1960<br> `1950` para 1950 ou anterior | string | Sim | Ano do automóvel |
| `mileage` |  | integer | Sim | Quilometragem do automóvel |
| `gearbox` | `1` para Manual<br> `2` para Automático<br> `3` para Semi-Automático | string | Não<sup>1</sup> | Tipo de câmbio |
| `fuel` | `1` para Gasolina<br> `2` para Álcool<br> `3` para Flex<br> `4` para Gás Natural<br> `5` para Diesel<br> `6` para Híbrido<br> `7` para Elétrico | string | Não<sup>1</sup> | Tipo de combustível |
| `vehicle_brand` |  | string | Não<sup>1</sup> | Marca do automóvel. Para verificar as disponíveis, [use o serviço da OLX](car_models.md). |
| `vehicle_model` |  | string | Não<sup>1</sup> | Modelo da marca do automóvel. Para verificar os disponíveis, [use o serviço da OLX](car_models.md).  |
| `vehicle_version` |  | string | Não<sup>1</sup> | Versão do modelo do automóvel. Para verificar as disponíveis, [use o serviço da OLX](car_models.md).  |
| `car_features` | `1` para Ar condicionado<br> `2` para Direção hidráulica<br> `3` para Vidro elétrico<br> `4` para Trava elétrica<br> `5` para Air bag<br> `6` para Alarme<br> `7` para Som<br> `8` para Sensor de ré<br> `9` para Câmera de ré<br> `10` para Blindado | array de strings | Não<sup>1</sup> | Opcionais |
| `doors` | `1` para 2 portas<br>`2` para 4 portas | string | Não<sup>1</sup> | Número de portas |
| `end_tag` | `1` para 0<br> `2` para 1<br> `3` para 2<br> `4` para 3<br> `5` para 4<br> `6` para 5<br> `7` para 6<br> `8` para 7<br> `9` para 8<br> `10` para 9 | string | Não<sup>1</sup> | Número final da placa do automóvel |
| `car_steering` | `1` para Hidráulica<br> `2` para Elétrica<br> `3` para Mecânica<br> `4` para Assistida | string | Não<sup>1</sup> | Direção |
| `motorpower` | `1` para 1<br> `2` para 1.2<br> `3` para 1.3<br> `4` para 1.4<br> `5` para 1.5<br> `6` para 1.6<br> `7` para 1.7<br> `8` para 1.8<br> `9` para 1.9<br> `10` para 2.0 - 2.9<br> `11` para 3.0 - 3.9<br> `12` para 4.0 ou mais | string | Não<sup>1</sup> | Potência do motor |
| `cartype` | `1` para Passeio<br> `2` para Conversível<br> `3` para Pick-up<br> `4` para Antigo<br> `5` para SUV<br> `6` para Buggy<br> `7` para Van/Utilitário<br> `8` para Sedã<br> `9` para Hatch | string | Não<sup>1</sup> | Tipo de automóvel |
| `carcolor` | `1` para Preto<br>`2` para Branco<br>`3` para Prata<br>`4` para Vermelho<br>`5` para Cinza<br>`6` para Azul<br>`7` para Amarelo<br>`8` para Verde<br>`9` para Laranja<br>`10` para Outra | string | Não<sup>1</sup> | Cor do automóvel |
| `exchange` | `1` para Sim<br> `2` para Não | string | Não<sup>1</sup> | Aceita trocas pelo produto |
| `financial` | `1` para Financiado<br> `2` para IPVA Pago<br> `3` para Com multas<br> `4` para De leilão | string | Não<sup>1</sup> | Estado financeiro |
| `owner` | `1` para Sim<br> `2` para Não | string | Não<sup>1</sup> | Único dono |

<sup>1</sup>: Se você não quer enviar um parâmetro não-obrigatório, deixe de enviar o parâmetro no payload. Se você enviar o parâmetro com valor vazio ou `0`, a operação vai falhar (a menos, é claro, que o valor `0` seja esperado para esse parâmetro).

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Carros, vans e utilitários`:

```json
{
    "access_token": "ca18abccaadd282490e75173f98b8ec6f0c1c6c8",
    "ad_list": [
        {
            "id": "5555555555",
            "operation": "insert",
            "category": 2020,
            "subject": "Carro Novo",
            "body": "Corpo do anúnucio",
            "phone": 2155555555,
            "type": "s",
            "price": 10500,
            "zipcode": "24230090",
            "params": {
                "vehicle_brand": "3",
                "vehicle_model": "6",
                "vehicle_version": "2",
                "regdate": "1988",
                "gearbox": "1",
                "fuel": "1",
                "cartype": "2",
                "mileage": 10000,
                "doors": "1",
                "end_tag": "1",
                "motorpower": "5",
                "car_steering": "1",
                "carcolor": "1",
                "car_features": [
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
            "category": 2020,
            "subject": "Carro Novo 2",
            "body": "Corpo do anúnucio 2",
            "phone": 2155555544,
            "type": "s",
            "price": 12500,
            "zipcode": "24234590",
            "params": {
                "regdate": "2001",
                "gearbox": "2",
                "fuel": "3",
                "cartype": "2",
                "mileage": 1000,
                "doors": "1",
                "end_tag": "1",
                "motorpower": "5",
                "car_steering": "1",
                "carcolor": "1",
                "car_features": [
                    "1",
                    "2"
                ]
            },
            "images": [
                "http://www.a.com/image3.png"
            ]
        }
    ]
}
```

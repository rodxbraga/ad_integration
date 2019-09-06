### Categoria `Caminhões`

Para esta categoria, é necessário preencher o parâmetro `category` com o valor `2040`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:

| Parâmetro | Valor | Tipo | Obrigatório | Descrição |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------|----------------------------|
| `regdate` | `2019` para 2019<br> `2018` para 2018<br> `2017` para 2017<br> `2016` para 2016<br> `2015` para 2015<br> `2014` para 2014<br> `2013` para 2013<br> `2012` para 2012<br> `2011` para 2011<br> `2010` para 2010<br> `2009` para 2009<br> `2008` para 2008<br> `2007` para 2007<br> `2006` para 2006<br> `2005` para 2005<br> `2004` para 2004<br> `2003` para 2003<br> `2002` para 2002<br> `2001` para 2001<br> `2000` para 2000<br> `1999` para 1999<br> `1998` para 1998<br> `1997` para 1997<br> `1996` para 1996<br> `1995` para 1995<br> `1994` para 1994<br> `1993` para 1993<br> `1992` para 1992<br> `1991` para 1991<br> `1990` para 1990<br> `1989` para 1989<br> `1988` para 1988<br> `1987` para 1987<br> `1986` para 1986<br> `1985` para 1985<br> `1984` para 1984<br> `1983` para 1983<br> `1982` para 1982<br> `1981` para 1981<br> `1980` para 1980<br> `1975` para Entre 1975 e 1980<br> `1970` para Entre 1970 a 1975<br> `1965` para Entre 1965 e 1970<br> `1960` para Entre 1960 e 1965<br> `1955` para Entre 1955 e 1960<br> `1950` para 1950 ou anterior | string | Sim | Ano do caminhão |
| `mileage` |  | integer | Sim | Quilometragem do caminhão |
| `gearbox` | `1` para Manual<br> `2` para Automático<br> `3` para Semi-Automático | string | Não | Tipo de câmbio |
| `fuel` | `1` para Gasolina<br> `2` para Álcool<br> `3` para Flex<br> `4` para Gás Natural<br> `5` para Diesel | string | Não | Tipo de combustível |
| `trucktype` | `1` para Caçamba<br> `2` para No chassi<br> `3` para Baú<br> `4` para Carroceria<br> `5` para Graneleiro<br> `6` para Plataforma<br> `7` para Munck<br> `8` para Pipa<br> `9` para Boladeiro<br> `10` para Carga seca<br> `11` para Guindaste<br> `12` para Outro | string | Não | Tipo de caminhão |
| `truck_features` | `1` para Ar condicionado<br> `2` para Vidro elétrico<br> `3` para Trava elétrica<br> `4` para Blindado<br> `5` para ABS | array de strings | Não | Opcionais |
| `exchange` | `1` para Sim<br> `2` para Não | string | Não | Aceita trocas pelo produto |
| `financial` | `1` para Financiado<br> `2` para IPVA Pago<br> `3` para Com multas<br> `4` para De leilão | string | Não | Estado financeiro |
| `owner` | `1` para Sim<br> `2` para Não | string | Não | Único dono |

Aqui está um exemplo de JSON para inserção ou edição de anúncios na subcategoria `Caminhões`:

```json
{
    "access_token": "ca18abccaadd282490e75173f98b8ec6f0c1c6c8",
    "ad_list": [
        {
            "id": "5555555555",
            "operation": "insert",
            "category": 2040,
            "subject": "Caminhão Novo",
            "body": "Caminhão legal, super bom, com características X, Y e Z.\nEntre em contato e vamos fazer negócio.",
            "phone": 2155555555,
            "type": "s",
            "price": 10500,
            "zipcode": "24230090",
            "params": {
                "regdate": "1988",
                "gearbox": "1",
                "fuel": "1",
                "trucktype": "2",
                "mileage": "10000",
                "carcolor": "1",
                "truck_features": [
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
            "category": 2040,
            "subject": "Caminhão Novo 2",
            "body": "Caminhão legal, super bom, com características X, Y e Z.\nEntre em contato e vamos fazer negócio.",
            "phone": 2155555544,
            "type": "s",
            "price": 12500,
            "zipcode": "24234590",
            "params": {
                "regdate": "2001",
                "gearbox": "2",
                "fuel": "3",
                "trucktype": "2",
                "mileage": "1",
                "truck_features": [
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
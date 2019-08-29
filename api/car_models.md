# Listagem de Marcas e Modelos de Automóveis e Motos na OLX

## Automóveis

A URL usada para fazer a requisição do arquivo JSON é https://apps.olx.com.br/autoupload/car_info, contendo as seguintes rotas:

| Rota | Descrição |
|---------------------------------------------------------------------|-------------------------------------------------------|
| https://apps.olx.com.br/autoupload/car_info | Para listar todas as marcas disponíveis |
| https://apps.olx.com.br/autoupload/car_info/{id_marca} | Para listar todos os modelos de determinada marca |
| https://apps.olx.com.br/autoupload/car_info/{id_marca}/{id_modelo} | Para listar todas as versões de um determinado modelo |

Nosso servidor deve receber a requisição com método do tipo `POST`, sendo que o formato do arquivo a ser enviado para nosso servidor deverá ser do tipo JSON.

### Listagem de Marcas Disponíveis

Exemplo de chamada para https://apps.olx.com.br/autoupload/car_info:

```json
{
    "access_token":"ca18abccaadd282490e75173f98b8ec6f0c1c6c8"
}
```

Exemplo de retorno:

```json
{
    "status": "ok",
    "data": {
        "AM GEN": 1,
        "ACURA": 2,
        "AGRALE": 3,
        "ALFA ROMEO": 4,
        "ASIA MOTORS": 5,
        "AUDI": 6,
        "BMW": 7,
        "BRM": 8,
        "BUGGY": 9,
        "BUGRE": 10,
        "CBT JIPE": 11,
        "CHANGAN": 12
    }
}
```


### Listagem de Modelos de Determinada Marca

Exemplo de chamada: https://apps.olx.com.br/autoupload/car_info/6 (no caso, o id `6` é a marca `AUDI`, conforme visto no exemplo acima):

```json
{
    "access_token": "2cb68a524c25b9a934e9edf4102ef82db5babd77"
}
```

Exemplo de retorno: 

```json
{
    "status": "ok",
    "data": {
        "80": 2,
        "100": 1,
        "A1": 3,
        "A3": 4,
        "A4": 5,
        "A5": 6,
        "A6": 7,
        "A7": 8,
        "A8": 9
    }
}
```

### Listagem de Versões de Determinado Modelo

Exemplo de chamada para: https://apps.olx.com.br/autoupload/car_info/6/3 (no caso, o id `6` identifica a marca `AUDI e o id `3` identifica o modelo `A3`, conforme exemplos acima):

```json
{
    "access_token": "2cb68a524c25b9a934e9edf4102ef82db5babd77"
}
```

Exemplo de retorno:

```json
{
    "status": "ok",
    "data": {
        "A1 1.4 TFSI 122CV S-TRONIC 3P": 1,
        "A1 SPORT 1.4 TFSI 185CV 3P S-TRONIC": 2,
        "A1 SPORTBACK 1.4 TFSI 185CV 5P S-TRONIC": 3,
        "A1 SPORTBACK 1.4 TFSI 5P S-TRONIC": 4,
        "A1 2.0 TFSI QUATTRO 256CV 3P": 5,
        "A1 SPORTBACK 1.8 TFSI 192CV 5P S-TRONIC": 6,
        "A1 SPORT. S EDITION 1.4 TFSI 5P S-TRONIC": 7
    }
}
```

## Motos

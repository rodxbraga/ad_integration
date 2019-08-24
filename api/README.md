# Documentação da API de Integração de Anúncios da OLX

> **IMPORTANTE**: A nova versão da API de Integração de Anúncios da OLX está em construção. Se você já está integrado com a OLX, preste atenção nas mudanças iminentes.

> Se tiver dificuldades ou sugestões, [abra uma Issue nesse repositório](https://github.com/olxbr/ad_integration/issues/new) e a equipe de desenvolvimento da OLX vai responder seu contato. Em casos urgentes, entre em contato com suporteintegrador@olxbr.com. Se tiver sugestões ou quiser conversar sobre a integração de anúncios, [agende um *call* com o Gerente de Produto do time de Integrações](https://calendly.com/renato-cairo-olx/papo_integracao_olx).

***

## Autenticação oAuth no OLX

Para utilizar a integração de anúncios via API, é necessário autenticar-se em nome de um usuário do OLX através do protocolo oAuth. A documentação da autenticação oAuth encontra-se [aqui](https://github.com/olxbr/ad_integration/blob/master/oauth/README.md).

Na autenticação, o sistema solicitante receberá o `client_id` e o `client_secret` que deverão ser usados na URL de conexão. Durante o fluxo oAuth será requisitado que o usuário dê permissão ao integrador para gerenciar seus anúncios na OLX. No *handshake* do oAuth, é requisitado também o `scope` que a aplicação-cliente necessitará. Para utilizar o sistema de integração de anúncios via API, é preciso o `scope` `autoupload`.


## Requisição de importação ao servidor olx.com.br

O processo de integração de anúncios via API consiste no envio de um arquivo no formato JSON descrevendo um ou mais anúncios para inserção, edição ou deleção.

A URL usada para fazer o envio do arquivo JSON é: https://apps.olx.com.br/autoupload/import

O nosso servidor deve receber a chamada com método do tipo `PUT` e o header enviado deverá ser: `Content-type: application/json`. O formato do *encode* do JSON deverá ser UTF-8.


Para uma inserção ou edição de anúncios, é necessário respeitar parâmetros básicos, além de específicos de cada categoria e/ou subcategoria. Os parâmtros básicos são os seguintes:

| Parâmetro | Valores | Tipo | Obrigatório | Descrição  |
|--------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| access_token | A identificação fornecida pelo olx.com.br através do handshake do oAuth.   | string | sim | Token de acesso |
| id |  | Regular expression: [A-Za-z0-9_{}-]{1,19} | sim | O identificador do anúncio |
| operation | insert delete | string | Sim | Valores para identificar qual será a operação a ser feita:<br>Insert - inserir anúncios<br>Delete - apagar anúncios     |
| category | 1020<br>1040<br>1060<br>1080<br>1100<br>1120<br>1140<br>2020<br>2060 | integer | Sim | Categoria do anúncio: 1020–Apartamentos<br> 1040–Casas<br> 1060–Aluguel de Quartos<br> 1080–T emporada<br> 1100–Terrenos, sítios e fazendas<br> 1120–Lojas, salas e outros<br> 1140–Lançamentos<br> 2020–Carros<br>2060–Motos   |
| Subject |  | string | Sim | Título do anúncio. Mínimo: 2 Máximo: 90    |
| Body |  | string | sim | Descrição do anúncio. Mínimo: 2 Máximo: 6000     |
| Phone |  | string númerica | sim | Telefone para contato Mínimo: 10 Máximo: 11 (telefones com 9 dígitos) Formato: <ddd><telefone> Exemplo: 21999998888   |
| type | `s` para categorias 2020 e 1140.<br> `u` para categorias 1060 e 1080.<br> `s` ou `u` para as demais | string | sim | Tipo de oferta do anúncio: s: venda u: aluguel |
| price |  | integer | não | Preço do anúncio (não aceita centavos)   |
| zipcode |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor / loja.      |
| params | (ver tabela abaixo) | array | não | Lista de parâmetros com as características do anúncio. Os valores dessa lista variam de acordo com a categoria do anúncio.    |
| images | URL da imagem | array de string |  | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Para carro só serão permitidas no máximo 6 imagens. No máximo 20 imágens nas outras categorias. Importante: a primeira imagem da lista será a imagem principal do anúncio!          |



## Exemplo

A seguir, um exemplo de um arquivo, contendo duas inserções e uma deleção:

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
                "mileage": "10000",
                "doors": "1",
                "end_tag": "1",
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
                "mileage": "1",
                "doors": "1",
                "end_tag": "1",
                "car_features": [
                    "1",
                    "2"
                ]
            },
            "images": [
                "http://www.a.com/image3.png"
            ]
        },
        {
            "id": "444444444",
            "operation": "delete"
        }
    ]
}
```

### Retorno Esperado 
   
O formato do retorno de nosso servidor será do tipo JSON.

#### Sucesso

| Paramêtro | Valor | Descrição |
|---------------|------------------------------------------|------------------------------------------------------------------------|
| `token` |  | Retorna uma string com um token a ser usado para acessar o status da importação |
| `statusMessage` | `The ads were imported and will beprocessed` | Os anúncios foram importados e serão processados  |
| `statusCode` | `0` |  |
| `errors` | `array` | Retorna uma lista de erros |

2.7.3 Exemplo de Retorno

```json
{
    "token": "06fb235e216f3095ba913654d10afee2f55eae35",
    "statusCode": 0,
    "statusMessage": "The ads were imported and will be processed",
    "errors": []
}
```



| Código | Mensagem | Descrição  |
|--------|-------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| 0 | The ads were imported and will be processed | Os anúncios foram importados com sucesso e serão processados  |
| -1 | Unexpected error | Erro inesperado |
| -2 | The request was blocked | Usuário não pode importar pois está bloqueado temporariamente por excesso de requisições     |
| -3 | There is no ad to import | Não há anúncios para importar   |
| -4 | An ad had problems on import | Se um anúncio falhar em sua validação, a importação é cancelada      |
| -5 | Import is down | O serviço de importação está desativado    |
| -6 | Without permission | Usuário sem permissão  |
| -7 | Trying to import <n> ad(s), but user just have slot for <f> more. | O usuário está tentando importar <n> anúncios mas só podem importar mais <f>.    |
| -8 | Trying to import <n> ad(s), only <f> were imported and will be processed. The following ads were ignored due to limit exceeded: <t> | Tentando importar <n> anúncios, só <f> foram importados e serão processados. Os seguintes anúncios foram ignorados devido ao limite excedido.    |



```json
{
    "token": null,
    "statusCode": -4,
    "statusMessage": "An ad had problems on import",
    "errors": [
        {
            "id": "5555555555",
            "status": "error",
            "messages": []
        }
   {
            "category": "ERROR_CATEGORY_INVALID"
        }
    ]
}
```

| Código | Descrição  |
|--------------------------------|--------------------------------------------|
| `ERROR_CATEGORY_INVALID` | Categoria inválida |
| `ERROR_REGION_MISSING` | Região inválida  |
| `ERROR_ZIPCODE_INVALID` | CEP inválido |
| `ERROR_TYPE_INVALID` | Tipo inválido |
| `ERROR_PHONE_INVALID` | Número de telefone inválido  |
| `ERROR_PHONE_TOO_SHORT` | Número de telefone muito curto |
| `ERROR_PHONE_TOO_LONG` | Número de telefone muito longo |
| `ERROR_BODY_TOO_SHORT` | Descrição muito curta  |
| `ERROR_BODY_TOO_LONG` | Descrição muito longa  |
| `ERROR_SUBJECT_TOO_SHORT` | Título muito curto |
| `ERROR_SUBJECT_TOO_LONG` | Título muito longo |
| `ERROR_FUEL_INVALID` | Tipo de combustível inválido  |
| `ERROR_FUEL_MISSING` | Tipo de combustível ausente |
| `ERROR_CARTYPE_INVALID` | Tipo de carro inválido |
| `ERROR_DOORS_MISSING` | Tipo de portas inválidos |
| `ERROR_ROOMS_INVALID` | Total de quartos inválidos |
| `ERROR_ROOMS_MISSING` | Número de quartos ausente |
| `ERROR_CATEGORY_SUBTYPE_MISSING` | Tipo de apartamento inválido |
| `ERROR_SIZE_INVALID` | Tamanho inválido |
| `ERROR_UNKNOWN_APARTMENT_TYPE` | Tipo de apartamento desconhecido |
| `ERROR_MILEAGE_INVALID` | Quilometragem incorreta |
| `ERROR_REGDATE_INVALID` | Ano inválido para carro |
| `ERROR_UNKNOWN_CAR_FEATURES` | Parâmetro adicional de carros desconhecido |
| `ERROR_NO_SUCH_PARAMETER` | Indica que não existe o parâmetro passado  |
| `ERROR_OPERATION_INVALID` | Tipo de operação inválida   |

| Parâmetro | Valores | Tipo | Obrigatório | Descrição  |
|--------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| access_token | A identificação fornecida pelo olx.com.br através do handshake do oAuth.   | string | sim | Token de acesso |
| id |  | Regular expression: [A-Za-z0-9_{}-]{1,19} | sim | O identificador do anúncio |
| operation | insert delete | string | Sim | Valores para identificar qual será a operação a ser feita:<br>Insert - inserir anúncios<br>Delete - apagar anúncios     |
| category | 1020<br>1040<br>1060<br>1080<br>1100<br>1120<br>1140<br>2020<br>2060 | integer | Sim | Categoria do anúncio: 1020–Apartamentos<br> 1040–Casas<br> 1060–Aluguel de Quartos<br> 1080–T emporada<br> 1100–Terrenos, sítios e fazendas<br> 1120–Lojas, salas e outros<br> 1140–Lançamentos<br> 2020–Carros<br>2060–Motos   |
| Subject |  | string | Sim | Título do anúncio. Mínimo: 2 Máximo: 90    |
| Body |  | string | sim | Descrição do anúncio. Mínimo: 2 Máximo: 6000     |
| Phone |  | string númerica | sim | Telefone para contato Mínimo: 10 Máximo: 11 (telefones com 9 dígitos) Formato: <ddd><telefone> Exemplo: 21999998888   |
| type | `s` para categorias 2020 e 1140.<br> `u` para categorias 1060 e 1080.<br> `s` ou `u` para as demais | string | sim | Tipo de oferta do anúncio: s: venda u: aluguel |
| price |  | integer | não | Preço do anúncio (não aceita centavos)   |
| zipcode |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor / loja.      |
| params | (ver tabela abaixo) | array | não | Lista de parâmetros com as características do anúncio. Os valores dessa lista variam de acordo com a categoria do anúncio.    |
| images | URL da imagem | array de string |  | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Para carro só serão permitidas no máximo 6 imagens. No máximo 20 imágens nas outras categorias. Importante: a primeira imagem da lista será a imagem principal do anúncio!          |

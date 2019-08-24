# Documentação da API de Integração de Anúncios da OLX 

A nova versão da API de Integração de Anúncios da OLX está em construção. A documentação será escrita e disponibilizada nesse repositório, mas por enquanto vamos já alinhando sobre as primeiras mudanças necessárias.

## Ajuste inicial de chamadas da nova API

Nós estamos trabalhando para melhorar a experiência de integração com a OLX. Estamos ajustando nossa API para garantir uma maior disponibilidade e performance para o gerênciamento do seu anúncio. A API tem como objetivo dar maior transparência do status do seu anúncio, assim como facilitar a manipulação do mesmo.

Nesse primeiro momento precisamos uniformizar as chamadas que são feitas para a API. A versão atual aceita chamadas feitas incorretamente e, para avançarmos com a nova versão, precisamos ajustar esse ponto. Os endpoints que podem ser utilizados para a importação e consulta de status deverão receber chamadas seguindo o padrão:

### Inserção, edição e deleção
`PUT /autoupload/import`<br>
header: `Content-type: application/json`
### Status
`POST /autoupload/import/{id}`<br>
header: `Content-type: application/json`

## Dúvidas e sugestões?

Abram uma `Issue` aqui nesse repositório, para contato direto com a equipe de desenvolvimento da OLX. Se quiser agendar uma conversa direto com o Gerente de Produto da equipe, é só agendar aqui: https://calendly.com/renato-cairo-olx/papo_integracao_olx




# Documentação da Importação de Anúncios via API

## Autenticação oAuth no OLX

Para utilizar a importação automática é necessário autenticar-se em nome de um usuário do OLX através do protocolo oAuth. No processo de autenticação, o integrador utilizado deve ser homologado com o olx.com.br. O processo de homologação encontra-se descrito  (https://github.com/olxbr/ad_integration/blob/master/oauth/README.md).

No cadastro, o solicitante (Integrador/Administrador) receberá o client_id e o client_secret que deverão ser usados na url de conexão. Durante o fluxo oAuth será requisitado ao usuário que dê permissão ao integrador para gerenciar seus anúncios no OLX através do sistema de importação. No handshake do oAuth, é requisitado também o scope que a aplicação cliente necessitará. Para utilizar o sistema de importação automática, é preciso o scope autoupload.

## Requisição de importação ao servidor olx.com.br
O processo de importação de anúncios de forma automática no olx.com.br consiste no envio de um arquivo no formato JSON descrevendo um ou mais anúncios para inserção e/ou deleção. Ao receber este arquivo, nosso servidor faz a validação das informações presentes e insere os anúncios em uma fila, onde serão posteriormente processados e inseridos.
Ao final do processamento do arquivo JSON, é gerado um token que será retornado como resposta. Com esse token é possível consultar o status da importação e dos anúncios importados.
Um anúncio importado passa pelos seguintes estados:

- `pending`: anúncio na fila de inserção;
- `queued`: anúncio inserido na fila de revisão;
- `accepted`: anúncio publicado;
- `refused`: anúncio recusado;
- `error`: ocorreu um erro no anúncio.

Abaixo, as instruções para realizar uma importação:

## URL

A URL usada para fazer o envio do arquivo JSON é: https://apps.olx.com.br/autoupload/import

## Método

O nosso servidor deve receber a requisição com método do tipo PUT.

## Operações

Na importação automática de anúncios, é possível realizar operações de insert ou delete, que indicam, respectivamente, inserção ou deleção de anúncios. Para definir qual operação executar para um determinado anúncio, deve-se utilizar o parâmetro operation em seu arquivo JSON.

- Insert - Indica a inserção de um anúncio. Caso o anúncio já exista em nossa base, nosso sistema irá tratá-lo como uma edição;
- Delete - Realiza a deleção do anúncio de nossa base. Neste caso, basta passar o id do anúncio (ver exemplo abaixo). 

## Formato

O formato do arquivo a ser enviado deverá ser do tipo JSON.

## Codificação

O formato do encode do arquivo a ser enviado deverá ser UTF8.

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

2.7 Retorno Esperado 
   
2.7.1 Formato
O formato do retorno de nosso servidor será do tipo JSON.
2.7.2 Sucesso

| Parameter | Value | Description |
|---------------|------------------------------------------|------------------------------------------------------------------------|
| token |  | Retorna umastringcom umtokena ser usado para acessar o status doimport |
| statusMessage | The ads wereimported andwill beprocessed | Os anúncios foram importados e serão processados  |
| statusCode | 0 |  |
| errors | array | Retorna uma lista de erros |

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


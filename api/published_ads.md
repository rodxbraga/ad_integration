# Consulta de Anúncios Publicados

Esta consulta retorna todos os anúncios que já foram processados e estão ativos, ou seja, disponíveis para visualização em nosso site por qualquer usuário da OLX.

Nosso servidor deve receber a requisição com método do tipo `POST`, contendo um arquivo JSON.

Exemplo de chamada para a URL https://apps.olx.com.br/autoupload/published:

```json
{
    "access_token":"2cb68a524c25b9a934e9edf4102ef82db5babd77"
}
```

O retorno da chamda trará o identificador usado pelo integrador/anunciante na inserção do anúncio e outro identificador do anúncio na OLX. Caso o anunciante não tenha anúncios ativos, será retornado um array vazio.

| Parâmetro | Valores | Descrição  |
|-----------|-------------------------------------------|------------------------------------------------|
| `id` | Regular expression: [A-Za-z0-9_{}-]{1,19} | Identificador do anúncio definido pelo usuário  |
| `list_id` | integer | id do anúncio na OLX |

Exemplo de retorno:

```json
[
    {
        "id": "original-id-01",
        "list_id": "81262515"
    },
    {
        "id": "original-id-02",
        "list_id": "81262987"
    }
]
```

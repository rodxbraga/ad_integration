# Status de Publicação

Depois da importação, os anúncios vão para a fila de importação da OLX Brasil para serem processados. Essa consulta retorna a confirmação de inserção do anúncio com sucesso, bem como informa e detalha um eventual erro no processo de importação de um anúncio.


## Requisição de Status

A URL usada para fazer a requisição do arquivo JSON: https://apps.olx.com.br/autoupload/import/{token}. O `token` a ser inserido no final da URL é o retorno mencionado na importação.

A requisição feita para esta URL deve conter o `access_token` de cada anunciante, usando o método `POST`:

```JSON
{
     "access_token": "37812426ab5961d8a029b224b8e1288e192062ef"
}
```

## Retorno Esperado 

O formato do retorno de nosso servidor será do tipo JSON, que contém a seguinte estrutura:


| Parâmetro | Valores | Descrição  |
|-----------|-------------------------------------------|------------------------------------------------|
| `autoupload_status` | `done`, `pending` | Retorna o status dos anúncios. `done`: todos os anúncios foram processados (inseridos ou deletados) `pending`: Pelo menos um anúncio ainda está na fila de importação |
| `ads` | array[] | Este parâmetro detalha o resultado de publicação de determinado anúncio, seguindo a descrição da tabela abaixo. |

A tabela abaixo detalha o retorno do parâmetro `ads`, que de fato explica o que houve com o anúncio em si:

| Parâmetro | Valores | Descrição  |
|-----------|---------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `status` | `pending`, `error`, `queued`, `accepted`, `refused` | Retorna o status dos anúncios.<br> `pending`: o anúncio será processado.<br> `error`: o anúncio está com erro(s).<br> `queued`: o anúncio foi inserido e será ativado em breve<br> `accepted`: o anúncio foi ativado. Caso a operação seja de deleção, significa que o anúncio foi deletado.<br> `refused`: o anúncio não foi ativado               |
| `operation` | `insert`, `delete` | Operação utilizada<br> `insert`: inserção de anúncio<br> `delete`: deleção de anúncio        |
| `message` | Exemplos: `ERROR_IMAGE_TOO_SMALL`,<br> `ERROR_DOWNLOADING_IMAGE`,<br> `ERROR_UPLOADING_IMAGE` | Mensagens de aviso sobre erros ocorridos |
| `list_id` | string | Retorna o id do seu anúncio, caso o mesmo tenha sido aprovado |



## Exemplos de retorno:


Para um anúncio inserido ou editado, que ainda não entrou na fila de ativação:
```json
{
    "autoupload_status": "pending",
    "ads": {
        "1111111111": {
            "status": "pending",
            "operation": "insert"
        }
    }
}
```

Para um anúncio editado antes de ter sido ativado:
```json
{
    "autoupload_status": "pending",
    "ads": {
        "1111111111": {
            "status": "queued",
            "operation": "edit",
            "list_id": "8000000",
            "message": []
        }
    }
}
```

Para anúncio inserido e aguardando ativação:
```json
{
    "autoupload_status": "pending",
    "ads": {
        "1111111111": {
            "status": "queued",
            "operation": "insert",
            "message": []
        }
    }
}
```

Para um anúncio inserido com sucesso:
```json
{
    "autoupload_status": "done",
    "ads": {
        "1111111111": {
            "status": "accepted",
            "operation": "insert",
            "message": [],
            "url": "http://www.olx.com.br/vi/8000005.htm"
        }
    }
}
```


Para um anúncio que não foi inserido por algum motivo: 
```json
{
    "autoupload_status": "done",
    "ads": {
        "1111111111": {
            "status": "refused",
            "operation": "insert",
            "message": []
        }
    }
}
```

Para um anúncio editado com sucesso: 
```json
{
    "autoupload_status": "done",
    "ads": {
        "1111111111": {
            "status": "accept",
            "operation": "edit",
            "list_id": "8000000",
            "message": []
        }
    }
}
```


Para um anúncio que teve uma edição recusada:
```json 
{
    "autoupload_status": "done",
    "ads": {
        "1111111111": {
            "status": "refused",
            "operation": "edit",
            "message": []
        }
    }
}
```

Para um anúncio removido com sucesso:
```json
{
    "autoupload_status": "done",
    "ads": {
        "1111111111": {
            "status": "accepted",
            "operation": "delete",
            "message": []
        }
    }
}
```
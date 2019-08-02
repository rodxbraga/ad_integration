### Categoria `Carros, vans e utilitários`

Para esta categoria, é necessário preencher o parâmetro `category` com o valor `2101`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:

| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|-------------|------------------------------------------------|
| `carcolor` | `1` para Preto<br>`2` para Branco<br>`3` para Prata<br>`4` para Vermelho<br>`5` para Cinza<br>`6` para Azul<br>`7` para Amarelo<br>`8` para Verde<br>`9` para Laranja<br>`10` para Outra | string | não | Cor do carro |
| `parts_name_cars` | `1` para Pneus<br>`2` para Rodas<br>`3` para Calotas<br>`4` para Peças automotivas<br>`5` para GPS<br>`6` para Som e multimídia<br>`7` para Tuning e Performance<br>`8` para Acessórios para interior<br>`9` para Acessórios para exterior<br>`10` para Outros | string | não | Indica o tipo de peça |
| `condition` | `1` para Novo<br>`2` para Usado | String | não | Produto novo ou de segunda mão  |
| `exchange` | `1` para Sim<br>`2` para Não | String | não | Aceita troca como pagamento |

Aqui está um exemplo de JSON para a subcategoria `Carros, vans e utilitários`:

```json
{  
   "account_id":"123445",
   "ad_list":[  
      {  
         "subject":"Peça de carro em ótimo estado",
         "body":"Peça de carro",
         "category":"2101",
         "id":"CAR005_ROD1",
         "images":[  
            "http://img1.jpg",
            "http://img2.jpg"
         ],
         "params":{  
            "carcolor":"1",
            "condition":"1",
            "exchange":"2"
         },
         "price":1000,
         "type":"s",
         "zipcode":"20521160"
      },
      {  
         "subject":"Peça de carro em ótimo estado",
         "body":"Peça de carro",
         "category":"2101",
         "id":"CAR005_ROD2",
         "images":[  
            "http://img1.jpg",
            "http://img2.jpg"
         ],
         "params":{  
            "carcolor":"1",
            "condition":"1",
            "exchange":"2"
         },
         "price":1000,
         "type":"s",
         "zipcode":"20521160"
      }
   ]
}```

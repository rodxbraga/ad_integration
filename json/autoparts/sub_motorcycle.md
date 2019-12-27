### Subcategoria `Motos`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `2103`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:

| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|-------------|------------------------------------------------|
| `carcolor` | `1` para Preto<br>`2` para Branco<br>`3` para Prata<br>`4` para Vermelho<br>`5` para Cinza<br>`6` para Azul<br>`7` para Amarelo<br>`8` para Verde<br>`9` para Laranja<br>`10` para Outra | string | não | Cor do carro |
| `parts_name_motos` | `1` para Pneus<br>`2` para Rodas<br>`3` para Calotas<br>`4` para Capacetes<br>`5` para Acabamento<br>`6` para Roupas de moto<br>`7` para Bagageiros, baús e mochilas<br>`8` para Suportes<br>`9` para Alarmes<br>`10` para Peças de motos<br>`11` para Outros | string | não | Indica o tipo de peça |
| `condition` | `1` para Novo<br>`2` para Usado | String | sim | Produto novo ou de segunda mão  |
| `exchange` | `1` para Sim<br>`2` para Não | String | não | Aceita troca como pagamento |

Aqui está um exemplo de JSON para a subcategoria `Motos`:

```json
[  
   {  
      "subject":"Peça de moto em ótimo estado",
      "body":"Peça de moto do tipo X, usado no caso Y.\nPeça em excelente estado, com características X, Y e Z.",
      "category":2103,
      "id":"MOTO005_ROD1",
      "images":[  
         "http://www.sitedeautos.com/img1.jpg",
         "http://www.sitedeautos.com/img2.jpg"
      ],
      "params":{  
         "carcolor":"1",
         "parts_name_motos":"9",
         "condition":"1",
         "exchange":"2"
      },
      "price":1000,
      "type":"s",
      "zipcode":"20521160"
   },
   {  
      "subject":"Peça de moto em ótimo estado",
      "body":"Peça de moto do tipo X, usado no caso Y.\nPeça em excelente estado, com características X, Y e Z.",
      "category":2103,
      "id":"MOTO005_ROD2",
      "images":[  
         "http://www.sitedeautos.com/img1.jpg",
         "http://www.sitedeautos.com/img2.jpg"
      ],
      "params":{  
         "carcolor":"1",
         "parts_name_motos":"9",
         "condition":"1",
         "exchange":"2"
      },
      "price":1000,
      "type":"s",
      "zipcode":"20521160"
   }
]
```

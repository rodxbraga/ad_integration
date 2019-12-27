### Subcategoria `Barcos e aeronaves`

Para esta subcategoria, é necessário preencher o parâmetro `category` com o valor `2104`.

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:

| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|-------------|------------------------------------------------|
| `carcolor` | `1` para Preto<br>`2` para Branco<br>`3` para Prata<br>`4` para Vermelho<br>`5` para Cinza<br>`6` para Azul<br>`7` para Amarelo<br>`8` para Verde<br>`9` para Laranja<br>`10` para Outra | string | não | Cor do veículo |
| `parts_name_boats` | `1` para Motores<br>`2` para Inversores<br>`3` para Bombas<br>`4` para Iluminação<br>`5` para Rotores<br>`6` para Cabos<br>`7` para Velas<br>`8` para Sonares e GPS<br>`9` para Hélices<br>`10` para Âncoras<br>`11` para Outros | string | não | Indica o tipo de peça |
| `condition` | `1` para Novo<br>`2` para Usado | String | sim | Produto novo ou de segunda mão  |
| `exchange` | `1` para Sim<br>`2` para Não | String | não | Aceita troca como pagamento |

Aqui está um exemplo de JSON para a subcategoria `Barcos e aeronaves`:

```json
[  
   {  
      "subject":"Peça de barco em ótimo estado",
      "body":"Peça de barco do tipo X, usado no caso Y.\nPeça em excelente estado, com características X, Y e Z.",
      "category":2104,
      "id":"BOAT005_ROD1",
      "images":[  
         "http://www.sitedeautos.com/img1.jpg",
         "http://www.sitedeautos.com/img2.jpg"
      ],
      "params":{  
         "carcolor":"1",
         "parts_name_boats":"9",
         "condition":"1",
         "exchange":"2"
      },
      "price":1000,
      "type":"s",
      "zipcode":"20521160"
   },
   {  
      "subject":"Peça de avião em ótimo estado",
      "body":"Peça de avião do tipo X, usado no caso Y.\nPeça em excelente estado, com características X, Y e Z.",
      "category":2104,
      "id":"PLANE005_ROD2",
      "images":[  
         "http://www.sitedeautos.com/img1.jpg",
         "http://www.sitedeautos.com/img2.jpg"
      ],
      "params":{  
         "carcolor":"1",
         "parts_name_boats":"9",
         "condition":"1",
         "exchange":"2"
      },
      "price":1000,
      "type":"s",
      "zipcode":"20521160"
   }
]
```

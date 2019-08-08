# Documentação para a Importação via JSON para a categoria `Agro e Indústria` na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de Agro e Indústria para as subcategorias `Tratores e máquinas agrícolas`, `Máquinas pesadas para construção`, `Máquinas para produção industrial`, `Peças para tratores e máquinas`, `Animais para agropecuária`, `Produção Rural` e `Outros itens para agro e indústria`, via JSON.

Os parâmetros para preenchimento do JSON para essas subcategorias estão explicador a seguir: 

| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|-------------------------------------------------|------------------------------------------------------------------------|-------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `subject` |  | string | sim | Título do anúncio Mínimo: 2 Máximo: 90    |
| `body` |  | string | sim | Descrição do anúncio Mínimo: 2 Máximo: 6000     |
| `category` | `12020` para Tratores e máquinas agrícolas<br> `12120` para Máquinas pesadas para construção<br> `12140` para Máquinas para produção industrial<br> `12040` para Peças para tratores e máquinas<br> `12100` para Animais para agropecuária<br> `12180` para Produção Rural<br> `12160` para Outros itens para agro e indústria| string | sim | Categoria do anúncio. |
| `id` |  | string | sim | Identificador do anúncio. Regular expression : [A-Za-z0- 9_{}- ]{1,19}<br>Atenção: o campo id deve ser único no arquivo. |
| `images` | URL das imagens | Array de string | não | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Máximo de 20 imagens.<br>Importante: a primeira imagem da lista será a imagem principal do anúncio.         |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos).   |
| `zipcode` |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor/loja.|
| `type` | `s` | string | sim | Tipo de oferta do anúncio. O valor `s` indica que o produto está à venda. |

Aqui está um exemplo de JSON para esta categoria:

```json
{  
   "account_id":"12345",
   "ad_list":[  
      {  
         "subject":"Trator em bom estado",
         "body":"Trator excelente, quase não foi usado.\nTem com características X, Y e Z.",
         "category":"2105",
         "id":"AGRO01",
         "images":[  
            "http://img1.jpg",
            "http://img2.jpg"
         ],
         "price":1000,
         "type":"s",
         "zipcode":"20521160"
      },
      {  
         "subject":"Trator excelente",
         "body":"Escavadeira excelente, com característica X, usado no caso Y.\nPeça em excelente estado, com características X, Y e Z.",
         "category":"12120",
         "id":"AGRO02",
         "images":[  
            "http://img1.jpg",
            "http://img2.jpg"
         ],
         "price":1000,
         "type":"s",
         "zipcode":"20521160"
      }
   ]
}
```

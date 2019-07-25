Eis um exemplo de JSON para Peças de Automóveis, Caminhões, Barcos, 

```json
[
    {
        "subject": "Peça de carro em ótimo estado",
        "body": "Peça de carro",
        "category": "2101",
        "id": "CAR005_ROD1",
        "images": [
            "http://img1.jpg",
            "http://img2.jpg"
        ],
        "params": {
            "carcolor": "1",
            "condition": "1",
            "exchange": "2"
        },
        "price": 1000,
        "type": "s",
        "zipcode": "20521160"
    },
    {
        "subject": "Peça de carro em ótimo estado",
        "body": "Peça de carro",
        "category": "2101",
        "id": "CAR005_ROD2",
        "images": [
            "http://img1.jpg",
            "http://img2.jpg"
        ],
        "params": {
            "carcolor": "1",
            "condition": "1",
            "exchange": "2"
        },
        "price": 1000,
        "type": "s",
        "zipcode": "20521160"
    }
]
```



| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|-------------------------------------------------|-----------------|-----------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Subject |  | string | sim | Título do anúncio Mínimo: 2 Máximo: 90    |
| Body |  | string | sim | Descrição do anúncio Mínimo: 2 Máximo: 6000     |
| Category | 2101 | string | sim | Categoria do anúncio. Deve ser 2101 para peças  |
| id |  | string | sim | Identificador do anúncio. Regular expression : [A-Za-z0- 9_{}- ]{1,19}<br>Atenção​: o campo id deve ser único no arquivo. |
| images | URL das imagens | Array de string | não | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Para carro só serão permitidas no máximo 6 imagens. No máximo 20 imagens nas outras categorias.<br>Importante: a primeira imagem da lista será a imagem principal do anúncio!         |
| price |  | integer | não | Preço do anúncio (não aceita centavos)   |
| zipcode |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor / loja.|
| type | s | string | sim | Tipo de oferta do anúncio: s: venda |




| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|-------------|------------------------------------------------|
| carcolor | 1 para Preto<br>2 para Branco<br>3 para Prata<br>4 para Vermelho<br>5 para Cinza<br>6 para Azul<br>7 para Amarelo<br>8 para Verde<br>9 para Laranja<br>10 para Outra | string | não | Cor do carro |
| parts_name_cars | 1 para Pneus<br>2 para Rodas<br>3 para Calotas<br>4 para Peças automotivas<br>5 para GPS<br>6 para Som e multimídia<br>7 para Tuning e Performance<br>8 para Acessórios para interior<br>9 para Acessórios para exterior<br>10 para Outros    | string | não | Indica o tipo de peça |
| condition | 1 para Novo<br>2 para Usado | String | não | Indica se é um produto novo ou de segunda mão  |
| exchange | 1 para Sim<br>2 para Não | String | não | Indica se aceita troca como forma de pagamento |

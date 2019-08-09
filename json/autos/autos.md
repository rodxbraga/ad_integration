# Documentação para a Importação via JSON para Veículos na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de veículos para as subcategorias `Carros, vans e utilitários`, `Ônibus`, `Caminhões`, `Motos` e `Barcos e aeronaves`, via JSON.

Para todas essas subcategorias há um conjunto de parâmetros básicos compartilhados, detalhados a seguir:


| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|-------------------------------------------------|---------------------------------------------------------|-------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `subject` |  | string | sim | Título do anúncio Mínimo: 2 Máximo: 90    |
| `body` |  | string | sim | Descrição do anúncio Mínimo: 2 Máximo: 6000     |
| `category` | `2020` para `Carros, vans e utilitários`<br>`2040` para `Caminhões`<br>`2060` para `Motos`<br>`2080` para `Barcos e aeronaves`<br>`2050` para `Ônibus`| string | sim | Categoria do anúncio. Deve ser preenchido conforme a subcategoria (mais informação ao final desta página)  |
| `id` |  | string | sim | Identificador do anúncio. Regular expression : [A-Za-z0- 9_{}- ]{1,19}<br>Atenção: o campo id deve ser único no arquivo. |
| `images` | URL das imagens | Array de string | não | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Para carro só serão permitidas no máximo 6 imagens. No máximo 20 imagens nas outras categorias.<br>Importante: a primeira imagem da lista será a imagem principal do anúncio!         |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos)   |
| `zipcode` |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor / loja.|
| `type` | `s` | string | sim | Tipo de oferta do anúncio. O valor `s` indica que o produto está à venda. |


### Parâmetros específicos por subcategoria

Cada subcategoria tem seu conjunto de parâmetros e valores específicos. Para isso, você deverá considerar os parâmetros específicos para cada subcategoria, bem como os parâmetros gerais da categoria Autos (contidos na tabela acima).

Exemplos de JSONs completos de cada subcategoria estão disponíveis na página de cada subcategoria.

- [Carros, vans e utilitários](https://github.com/olxbr/ad_integration/blob/master/json/autos/autos.md) (Em breve)
- [Motos](https://github.com/olxbr/ad_integration/blob/master/json/autos/motorcycle.md) (Em breve)
- [Ônibus](https://github.com/olxbr/ad_integration/blob/master/json/autos/bus.md) (Em breve)
- [Caminhões](https://github.com/olxbr/ad_integration/blob/json/autos/truck.md)
- [Barcos e aeronaves](https://github.com/olxbr/ad_integration/blob/master/json/autos/boat_plane.md) (Em breve)

# Documentação para a Importação via JSON para Peças na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de autopeças para as subcategorias `Carros, vans e utilitários`, `Ônibus`, `Caminhões`, `Motos` e `Barcos e aeronaves`, via JSON.

### Como integrar com a OLX?

Atendendo a este modelo de JSON, o anunciante ou seu integrador ficam responsáveis por disponibilizar uma URL onde o JSON ficará armazenado e sempre disponível, para que a OLX consulte o arquivo a cada importação.

A partir dos anúncios contidos no arquivo XML e o respectivo `<id>` contido em cada anúncio, a OLX vai inferir a inserção, edição ou deleção.


### Sobre a publicação dos anúncios

Além da validação contida nesse manual, há validações adicionais que são feitas sobre os anúncios. Com isso, a importação com sucesso dos anúncios não garante a publicação e/ou a permanência dos anúncios publicados. Caso infrinjam qualquer regra na OLX, o anúncio pode ser recusado imediatamente.


| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|-------------------------------------------------|-----------------|-----------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `subject` |  | string | sim | Título do anúncio Mínimo: 2 Máximo: 90    |
| `body` |  | string | sim | Descrição do anúncio Mínimo: 2 Máximo: 6000     |
| `category` |  | string | sim | Categoria do anúncio. Deve ser preenchido conforme a subcategoria (mais informação ao final desta página)  |
| `id` |  | string | sim | Identificador do anúncio. Regular expression : [A-Za-z0- 9_{}- ]{1,19}<br>Atenção​: o campo id deve ser único no arquivo. |
| `images` | URL das imagens | Array de string | não | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Para carro só serão permitidas no máximo 6 imagens. No máximo 20 imagens nas outras categorias.<br>Importante: a primeira imagem da lista será a imagem principal do anúncio!         |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos)   |
| `zipcode` |  | string numérica | sim | O CEP do anúncio. Caso o anúncio seja de uma categoria de Imóveis, deve ser o CEP do endereço do imóvel. Caso contrário, o CEP deve ser o do vendedor / loja.|
| `type` | `s` | string | sim | Tipo de oferta do anúncio: s: venda |


### Parâmetros específicos por subcategoria

Cada subcategoria de autopeças tem seu conjunto de parâmetros e valores específicos. Para isso, você deverá considerar os parâmetros específicos para cada subcategoria, bem como os parâmetros gerais da categoria Autopeças (contidos na tabela acima).

Exemplos de JSONs completos de cada subcategoria estão disponíveis na página de cada subcategoria.

- [Carros, vans e utilitários](https://github.com/olxbr/ad_integration/blob/master/autoparts/auto.md)
- [Motos](https://github.com/olxbr/ad_integration/blob/master/autoparts/motorcycle.md)
- [Ônibus](https://github.com/olxbr/ad_integration/blob/master/autoparts/bus.md)
- [Caminhões](https://github.com/olxbr/ad_integration/blob/master/autoparts/truck.md)
- [Barcos e aeronaves](https://github.com/olxbr/ad_integration/blob/master/autoparts/boat_plane.md)

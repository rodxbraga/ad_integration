# Documentação para a Importação via JSON para Peças na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de autopeças para as subcategorias `Carros, vans e utilitários`, `Ônibus`, `Caminhões`, `Motos` e `Barcos e aeronaves`, via JSON.

### Subcategorias 

Para que o anúncio seja categorizado corretamente na OLX, é preciso que cada anúncio esteja associado à `category` correspondente:

| `category` | Categoria na OLX |
|------------|----------------------------|
| `2101` | Carros, vans e utilitários |
| `2103` | Motos |
| `2105` | Ônibus |
| `2102` | Caminhões |
| `2104` | Barcos e aeronaves |


### Parâmetros específicos por subcategoria

Cada subcategoria de autopeças tem seu conjunto de parâmetros e valores específicos. Para isso, você deverá considerar os parâmetros específicos para cada subcategoria, bem como os [parâmetros gerais para quaisquer anúncio na OLX](/json/README.md).

Exemplos de JSONs completos de cada subcategoria estão disponíveis na página de cada subcategoria.

- [Carros, vans e utilitários](sub_autos.md)
- [Motos](sub_motorcycle.md)
- [Ônibus](sub_bus.md)
- [Caminhões](sub_truck.md)
- [Barcos e aeronaves](sub_boat_plane.md)

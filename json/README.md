# Importação de Anúncios via Arquivo JSON

Para a integração via Arquivo, a OLX vai consultar periodicamente (mínimo de uma vez por dia) o arquivo disponibilizado pelo anunciante. Para isso, caberá ao anunciante (junto com seu integrador, quando isso for aplicável) disponibilizar uma URL onde esse arquivo estará sempre disponível.

### Parâmetros básicos

Para a montagem do JSON, é necessário respeitar parâmetros genéricos e específicos de cada categoria e/ou subcategoria. Os parâmtros básicos são os seguintes:

| Parâmetro | Valor | Tipo | Obrigatório | Descrição  |
|-------------------------------------------------|---------------------------------------------------------|-------|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `subject` |  | string | sim | Título do anúncio Mínimo: 2 Máximo: 90    |
| `body` |  | string | sim | Descrição do anúncio Mínimo: 2 Máximo: 6000     |
| `category` | | string | sim | Código que define onde o anúncio vai ser exibido na OLX. Verifique a documentação da categoria (ou subcategoria) para saber qual valor inserir para o parâmetro. |
| `id` |  | string | sim | Identificador do anúncio.<br>Regular expression : [A-Za-z0- 9_{}- ]{1,19}<br>Atenção: o campo id deve ser único no arquivo. |
| `images` | URL das imagens | Array de string | não | URL das imagens do anúncio. Não pode haver URLs repetidas neste array. Máximo de 20 imagens por anúncio.<br>Importante: a primeira imagem da lista será a imagem principal do anúncio.         |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos)   |
| `zipcode` |  | string numérica | sim | CEP do local onde o produto está disponível.|
| `type` | `s` | string | sim | Tipo de oferta do anúncio. O valor `s` indica que o produto está à venda. |

Exemplos de JSONs de cada categoria podem ser achados na documentação específica por categoria.


### Categorias Suportadas

**A Integração via JSON é suportada para anúncios de todas as categorias da OLX**. Atualmente temos a documentação escrita para as seguintes categorias:

- [Autopeças](https://github.com/olxbr/ad_integration/tree/master/json/autoparts/cat_autoparts.md)
- [Veículos](https://github.com/olxbr/ad_integration/tree/master/json/autos/cat_autos.md)
- [Agro & Indústria](https://github.com/olxbr/ad_integration/tree/master/json/agro/cat_agro.md)

Estamos escrevendo a documentação ad hoc. Caso tenha interesse em integrar para uma categoria não contemplada, recomendamos abrir uma Issue ou entrar em contato via suporteintegrador@olxbr.com.


### Inferência de Inserção, Edição e Deleção de Anúncios

A OLX funciona com um modelo de inserção paga de anúncios. Para a importação de anúncios via arquivo, a OLX vai inferir que há uma nova inserção quando houver um anúncio com identificador inédito. Para JSONs, o identificador é o parâmetro `id`, contido no JSON.

Se um anúncio com um identificador já existente estiver no arquivo em uma nova importação, não realizaremos nenhuma operação, a menos que haja alguma alteração nas outras informações desses anúncio. Nesse caso, trataremos a operação como uma edição (e não inserção).

Para que ocorra a deleção de um anúncio, basta que ele deixe de existir no arquivo e, no próximo processamento dessa carga vamos inferir que esse anúncio deve ser removido. 

**Importante**: se um anúncio for removido e no próximo processamento ele voltar a aparecer no arquivo (ou, especificamente, se um determinado identificador deixar de existir no arquivo e, em outra importação, voltar a aparecer, vamos inferir (e, portanto, contabilizar) uma nova inserção. Por isso é crítico que um anúncio sempre esteja disponível com o mesmo identificador no arquivo e só deixe de aparecer quando de fato tivermos que removê-lo do seu inventário.

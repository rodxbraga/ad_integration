# Importação de Anúncios via Arquivo JSON

Para a integração via Arquivo, a OLX vai consultar periodicamente (mínimo de uma vez por dia) o arquivo disponibilizado pelo anunciante. Para isso, caberá ao anunciante (junto com seu integrador, quando isso for aplicável) disponibilizar uma URL onde esse arquivo estará sempre disponível.


### Categorias Suportadas

A Integração via JSON é suportada para anúncios de todas as categorias da OLX. Atualmente temos a documentação escrita para as seguintes categorias:

- [Autopeças](https://github.com/olxbr/ad_integration/tree/master/json/autoparts/cat_autoparts.md)
- [Veículos](https://github.com/olxbr/ad_integration/tree/master/json/autos/cat_autos.md)
- [Agro & Indústria](https://github.com/olxbr/ad_integration/tree/master/json/agro/cat_agro.md)

Estamos escrevendo a documentação ad hoc. Caso tenha interesse em integrar para uma categoria não contemplada, recomendamos abrir uma Issue ou entrar em contato via suporteintegrador@olxbr.com.


### Inferência de Inserção, Edição e Deleção de Anúncios

A OLX funciona com um modelo de inserção paga de anúncios. Para a importação de anúncios via arquivo, a OLX vai inferir que há uma nova inserção quando houver um anúncio com identificador inédito. Para JSONs, o identificador é o parâmetro `id`, contido no JSON.

Se um anúncio com um identificador já existente estiver no arquivo em uma nova importação, não realizaremos nenhuma operação, a menos que haja alguma alteração nas outras informações desses anúncio. Nesse caso, trataremos a operação como uma edição (e não inserção).

Para que ocorra a deleção de um anúncio, basta que ele deixe de existir no arquivo e, no próximo processamento dessa carga vamos inferir que esse anúncio deve ser removido. 

**Importante**: se um anúncio for removido e no próximo processamento ele voltar a aparecer no arquivo (ou, especificamente, se um determinado identificar deixar de existir no arquivo e, em outra importação, voltar a aparecer, vamos inferir (e, portanto, contabilizar) uma nova inserção. Por isso é crítico que um anúncio sempre esteja disponível com o mesmo identificado no arquivo e só deixe de aparecer quando de fato tivermos que removê-lo do seu inventário.

# Documentação para a Importação de Anúncios da OLX Brasil

A OLX hoje suporta dois tipos de importação de anúncios, para anunciantes que querem gerenciar seus anúncios a partir de um software terceiro (ou seja, sem passar pelas interfaces nativas da OLX para gestão de inventário).

Há duas formas principais para integrar anúncios: via API ou via arquivo (JSON ou XML).

## Integração via arquivo (JSON ou XML)

Para a integração via Arquivo, a OLX vai consultar periodicamente (mínimo de uma vez por dia) o arquivo disponibilizado pelo anunciante. Para isso, caberá ao anunciante (junto com seu integrador, quando isso for aplicável) disponibilizar uma URL onde esse arquivo estará sempre disponível.

[Categoria Imóveis, via arquivo (XML)](https://github.com/olxbr/ad_integration/blob/master/docs/real_estate_xml.md)<br>
[Categoria Veículos, via arquivo (JSON)](https://github.com/olxbr/ad_integration/blob/master/docs/autos_json.md)<br>
[Categoria Autopeças, via arquivo (JSON)](https://github.com/olxbr/ad_integration/blob/master/docs/autoparts_json.md)

#### Inserção e Deleção

A OLX funciona com um modelo de inserção paga de anúncios. Para a importação de anúncios via arquivo, a OLX vai inferir que há uma nova inserção quando houver um anúncio com identificar inédito. Para JSONs, o identificador é o parâmetro `id` e, para XMLs, o identificador é o parâmetro `<CodigoImovel>`. 

Se um anúncio com um identificador já existente estiver no arquivo, presumiremos que é o mesmo anúncio e trataremos a operação como uma edição (e não inserção), caso hajam alterações nas informações do arquivo.

Para que ocorra a deleção de um anúncio, basta que ele deixe de existir no arquivo e, no próximo processamento dessa carga vamos inferir que esse anúncio deve ser removido. 

Importante: se um anúncio for removido e no próximo processamento ele voltar a aparecer no arquivo (ou, especificamente, se um anúncio com um determinado identificador , vamos inferir (e, portanto, contabilizar) uma nova inserção. Por isso é crítico que um anúncio sempre esteja disponível no arquivo e deixe de aparecer quando de fato tivermos que removê-lo do seu inventário.


## Integração via API

Atualmente a OLX tem uma API para integração, que suporta apenas as categorias `Imóveis`, `Carros, vans e utilitários` e `Motos`. Uma nova versão está em desenvolvimento e será publicada aqui assim que disponível.

Para ter informações sobre a integração via API atual (chamada de Autoupload), contate suporteintegrador@olxbr.com.

## Dúvidas, sugestões e comentários

Caso você queria um suporte para sua integração, pode enviar email para suporteintegrador@olxbr.com.

Alternativamente, você pode simplesmente abrir uma [`Issue` aqui neste repositório](https://github.com/olxbr/ad_integration/issues), que a equipe técnica da OLX vai discutir quaisquer questões levantadas.

# Documentação para a Importação de Anúncios da OLX Brasil

A OLX hoje suporta dois tipos de importação de anúncios, para anunciantes que querem gerenciar seus anúncios a partir de um software terceiro (ou seja, sem passar pelas interfaces nativas da OLX para gestão de inventário).

Há duas formas principais para integrar anúncios: via API ou via arquivo (JSON ou XML).


### Integração via Arquivo (JSON ou XML)

Para integração via Arquivo, temos dois formatos diferentes: JSON e XML. O formato JSON suporta qualquer categoria na OLX, enquanto XML é um formato específico para a Categoria `Imóveis`.

A documentação para essas integrações está a seguir:

- [Importação de Anúncios via Arquivo JSON (Todas as Categorias)](https://github.com/olxbr/ad_integration/blob/master/docs/json.md)
- [Importação de Anúncios via Arquivo XML (Categoria Imóveis)](https://github.com/olxbr/ad_integration/blob/master/docs/xml.md)<br>


### Integração via API

Atualmente a OLX tem uma API para integração, que suporta apenas as categorias `Imóveis`, `Carros, vans e utilitários` e `Motos`. Uma nova versão está em desenvolvimento e será publicada aqui assim que disponível.

Para ter informações sobre a integração via API atual (chamada de Autoupload), contate suporteintegrador@olxbr.com.


## Dúvidas, sugestões e comentários

Caso você queria um suporte para sua integração, pode enviar email para suporteintegrador@olxbr.com.

Ou você pode [abrir uma Issue neste repo](https://github.com/olxbr/ad_integration/issues), que a equipe técnica da OLX vai olhar e responder a issue.

**Importante**: Esta documentação está focada na importação de anúncios para o portal OLX Brasil. Para importação de anúncios para os portais Autoshift e Storia Imóveis, contate suporteintegrador@olxbr.com.

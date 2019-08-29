# Documentação da API de Integração de Anúncios da OLX

> **IMPORTANTE**: A OLX está prestes a lançar uma **nova versão de sua API de Integração de Anúncios**. Leia este doc para saber o que muda.

A API de Importação de Anúncios da OLX contempla as seguintes funcionalidades:

| Funcionalidade                       | Descrição                                                                                                             | Status             |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------|--------------------|
| Autenticação oAuth                   | Permite que anunciantes autentiquem via integrador para configurar integração com OLX                                 | Estável            |
| Importação (Inserção/Edição/Deleção) | Permite gestão do inventário de anúncios publicados na OLX.                                                           | Em rollout         |
| Status de Importação                 | Informa o anunciante/integrador sobre o sucesso da publicação de um anúncio, bem como o motivo de uma não-publicação. | Em desenvolvimento |
| Marcas/Modelos de Carros             | Disponibiliza o catálogo de marcas e modelos de carros que podem ser publicados na OLX                                | Estável            |
| Consulta de Limite de Inserção       | Informa ao anunciante/integrador quantos anúncios ainda podem ser inseridos pelo anunciante.                          | Não-iniciado       |


## Por que uma nova API?

Estamos construindo uma nova API para atacar diferentes restrições técnicas e de negócio da Integração de Anúncios proporcionada pela API atual. Ela vai substituir duas rotas existentes na API atual: a rota de importação e a rota de status de publicação.

Os principais benefícios da mudança:

- **Suporte para todas as categorias de anúncios da OLX**<br>
A API atual é restrita para algumas categorias (Imóveis e Automóveis). A nova versão será flexível para atender qualquer categoria de anúncio existente na OLX.
- **Consistência na contagem de anúncios inseridos**<br>
Um dos pontos críticos da API atual é a discrepância entre o limite disponível para inserção de anúncios que é exibido na área do anunciante da OLX e a resposta da API. A nova API manterá consistência ao informar o limite disponível de inserção.
- **Melhorias técnicas na importação**<br>
Por baixo dos panos a nova API trará maior robustez, auxiliando na correção de erros e permitindo melhorias. Erros que hoje acontecem correntemente e melhorias que já identificamos (e são inviáveis de serem realizadas na API atual) já serão atendidas com a nova API.


## O que muda?

Fora os benefícios acima, do ponto de vista técnico muda pouca coisa. Em especial, algumas validações que eram síncronas passam a ser assíncronas. Mais detalhes [aqui](lerolerolero.com).


## Quais as fases do rollout?

1) **Chamadas à API**: Em andamento, com finalização em 30/08/19

A partir de 30/08/19, as chamadas para a API terão que respeitar o modelo abaixo:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Rota Inserção, edição e deleção**<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`PUT /autoupload/import`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;header: `Content-type: application/json`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Status**<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`POST /autoupload/import/{id}`<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;header: `Content-type: application/json`

2) **Rota de Importação**: Início de setembro

No início de Setembro vamos começar a comunicar e virar os integradores elegíveis para a API 2.0, modificando apenas a rota de importação. 

3) **Rota de Status**: Final de setembro

Ao final de setembro, vamos virar o restante dos integradores para a nova API, desta vez alterando tanto as rotas de importação quanto a rota de status de publicação.


# Dúvidas e sugestões

Se tiver dificuldades ou sugestões, [abra uma Issue nesse repositório](https://github.com/olxbr/ad_integration/issues/new) e a equipe de desenvolvimento da OLX vai responder seu contato. Em casos urgentes, entre em contato com suporteintegrador@olxbr.com. Se tiver sugestões ou quiser conversar sobre a integração de anúncios, [agende um *call* com o Gerente de Produto do time de Integrações](https://calendly.com/renato-cairo-olx/papo_integracao_olx).

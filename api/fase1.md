# Mudanças na Fase 1 de Migração para a API de Importação de Anúncios da OLX

A OLX está migrando seus integradores para uma nova API de Importação de Anúncios. Se você já está integrado via API com a OLX, é importante deixar claro o que muda na sua vida. 

A grande mudança - do ponto de vista técnico - está na resposta síncrona da API. Teremos algumas poucas validações síncronas adicionais, em linha com o que os outros canais de inserção (JSON, XML e inserção manual) já aplicam.

| Código | Descrição  |
|-----------------------|-----------------------------------------|
| `UNDEFINED_AD_ID` | Anúncio enviado sem ID |
| `NOT_ENOUGH_AD_SLOTS` | Limite de inserção de anúncios atingido |
| `NO_IMAGE` | Anúncio enviado sem imagens |
| `NO_REGION` | CEP enviado corresponde a região inválida  |
| `NO_REGION` | CEP enviado em formato inválido |
| `ERROR_TYPE_INVALID` | Tipo inválido |
| `ERROR_BODY_TOO_SHORT` | Descrição muito curta  |
| `ERROR_BODY_TOO_LONG` | Descrição muito longa  |
| `ERROR_SUBJECT_TOO_SHORT` | Título muito curto |
| `ERROR_SUBJECT_TOO_LONG` | Título muito longo |
| `ERROR_FUEL_INVALID` | Tipo de combustível inválido  |
| `ERROR_FUEL_MISSING` | Tipo de combustível ausente |
| `ERROR_CARTYPE_INVALID` | Tipo de carro inválido |
| `ERROR_DOORS_MISSING` | Tipo de portas inválidos |
| `ERROR_ROOMS_INVALID` | Total de quartos inválidos |
| `ERROR_ROOMS_MISSING` | Número de quartos ausente |
| `ERROR_CATEGORY_SUBTYPE_MISSING` | Tipo de apartamento inválido |
| `ERROR_SIZE_INVALID` | Tamanho inválido |
| `ERROR_UNKNOWN_APARTMENT_TYPE` | Tipo de apartamento desconhecido |
| `ERROR_MILEAGE_INVALID` | Quilometragem incorreta |
| `ERROR_REGDATE_INVALID` | Ano inválido para carro |
| `ERROR_UNKNOWN_CAR_FEATURES` | Parâmetro adicional de carros desconhecido |
| `ERROR_NO_SUCH_PARAMETER` | Indica que não existe o parâmetro passado  |
| `ERROR_CATEGORY_INVALID` | Categoria inválida |
| `ERROR_OPERATION_INVALID` | Tipo de operação inválida   |
| `ERROR_PHONE_INVALID` | Número de telefone inválido  |
| `ERROR_PHONE_TOO_SHORT` | Número de telefone muito curto |
| `ERROR_PHONE_TOO_LONG` | Número de telefone muito longo |
| `ERROR_BODY_HTML`<sup>1</sup> | Descrição do anúncio contém tag HTML |

<sup>1</sup> Nova validação síncrona, antes não existente na API de Importação da OLX.


## Quem é elegível para a mudança nessa Fase 1?

Todos os integradores serão migrados nessa Fase 1, incluindo quem consulta a rota de Status de Publicação de Anúncios já existente.



## Como será a migração dos integradores para nova API durante essa Fase 1?

Todos os integradores serão migrados nessa Fase 1, incluindo quem consulta a rota de Status de Publicação de Anúncios já existente. Faremos a migração dos anunciantes de cada integrador elegível gradualmente, de modo a garantir que consigamos entender se há impacto na capacidade de inserção de anúncios da OLX.
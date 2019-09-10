# Mudanças com a nova API de Integração de Anúncios

A OLX está migrando seus integradores para uma nova API de Importação de Anúncios. Se você já está integrado via API com a OLX, é importante deixar claro o que muda na sua vida. 

Para felicidade geral, do ponto de vista técnico muda pouca coisa. E do ponto de vista de experiência, acreditamos que vai mudar bastante.

A grande mudança - do ponto de vista técnico - está na resposta síncrona da API. Teremos menos casos sendo validados sincronamente. A seguir estão os casos validados sincronamente pela API:

| Código | Descrição  |
|-----------------------|-----------------------------------------|
| `UNDEFINED_AD_ID` | Anúncio enviado sem ID |
| `NOT_ENOUGH_AD_SLOTS` | Limite de inserção de anúncios atingido |
| `NO_IMAGE` | Anúncio enviado sem imagens |
| `NO_REGION` | CEP enviado corresponde a região inválida  |
| `NO_REGION` | CEP enviado em formato inválido |

Caso algum anúncio enviado viole algumas dessas validações, é importante notar que a importação falhará, **mesmo** se houver anúncios válidos na carga.

## Validações deprecadas

Várias das validações que antes eram feitas pela API passam a acontecer assincronamente. Ou seja, não serão retornadas pela nova API e terão que ser consultadas em outros endpoints. A saber:

| Código | Descrição  |
|----------------------------------|--------------------------------------------|
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

Ainda está em desenvolvimento a atualização do endpoint responsável por trazer o status da publicação de cada anúncio, contendo as validações que passam a ser assíncronas. Se a sua plataforma **não** requer do status de publicação, recomendamos migrar para a nova API imediatamente.

Caso precise mostrar o status de publicação, traremos mais detalhes brevemente.
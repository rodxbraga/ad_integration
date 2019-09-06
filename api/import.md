# Importação de Anúncios (Inserção/Edição/Deleção)

## Autenticação oAuth no OLX

Para utilizar a integração de anúncios via API, é necessário autenticar-se em nome de um usuário do OLX através do protocolo oAuth. A documentação da autenticação oAuth encontra-se [aqui](api/oauth.md).

Na autenticação, o sistema solicitante receberá o `client_id` e o `client_secret` que deverão ser usados na URL de conexão. Durante o fluxo oAuth será requisitado que o usuário dê permissão ao integrador para gerenciar seus anúncios na OLX. No *handshake* do oAuth, é requisitado também o `scope` que a aplicação-cliente necessitará. Para utilizar o sistema de integração de anúncios via API, é preciso o `scope` `autoupload`.


## Importação de Anúncios

O processo de integração de anúncios via API consiste no envio de um arquivo no formato JSON descrevendo um ou mais anúncios para inserção, edição ou deleção.

A URL usada para envio da requisição é: https://apps.olx.com.br/autoupload/import

O nosso servidor deve receber a chamada com método do tipo `PUT` e o header enviado deverá ser: `Content-type: application/json`. O formato do *encode* do JSON deverá ser `UTF-8`.


## Inserção ou Edição de Anúncios

Para uma inserção ou edição de anúncios, é necessário montar o JSON com parâmetros básicos para qualquer categorias, além de específicos de cada categoria e/ou subcategoria. Os parâmtros básicos são os seguintes:

| Parâmetro | Valores | Tipo | Obrigatório | Descrição  |
|--------------|-----------------------------------------------------------------------------------------------------|-------------------------------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `access_token` | | string | sim | Token de acesso |
| `id` |  | Regular expression: [A-Za-z0-9_{}-]{1,19} | sim | O identificador do anúncio. Deve ser único no JSON (caso haja mais de um anúncio no JSON). |
| `operation` | `insert` ou `delete` | string | sim | Valores para identificar qual será a operação a ser feita:<br>`insert` para inserir ou editar anúncios<br>`delete` para despublicar anúncios. |
| `category` |  | integer | sim | Categoria do anúncio. |
| `Subject` |  | string | sim | Título do anúncio. Mínimo de 2 e máximo de 90 caracteres. |
| `Body` |  | string | sim | Descrição do anúncio. Mínimo de 2 e máximo de 6 mil caracteres |
| `Phone` |  | string númerica | sim | Telefone para contato. Mínimo de 10 e máximo de 11 caracteres. Enviar DDD + Telefone sem caracteres especiais ou espaços. |
| `type` | `s` ou `u`  | string | sim | Tipo de oferta do anúncio. `s` para venda e `u` para aluguel. |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos) |
| `zipcode` |  | string numérica | sim | O CEP do anúncio. |
| `params` |  | array | não | Lista de parâmetros com as características do anúncio. Os valores dessa lista variam de acordo com a categoria do anúncio. |
| `images` | URL da imagem | array de string | não | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Máximo de 20 imagens. Importante: a primeira imagem da lista será a imagem principal do anúncio! |

Os parâmetros específicos de categorias e JSONs de exemplo podem ser encontrados na documentação de cada categoria:

| Categoria | Subcategoria |
|-------------------------|-----------------------------------------|
| [Imóveis](real_estate/README.md) | [Apartamentos](real_estate/README.md) |
| [Imóveis](real_estate/README.md) | [Casas](real_estate/README.md) |
| [Imóveis](real_estate/README.md) | [Aluguel de quartos](real_estate/README.md) |
| [Imóveis](real_estate/README.md) | [Temporada](real_estate/README.md) |
| [Imóveis](real_estate/README.md) | [Terrenos sítios e fazendas](real_estate/README.md) |
| [Imóveis](real_estate/README.md) | [Comércio e indústria](real_estate/README.md) |
| [Autos e peças](autos/README.md) | [Carros vans e utilitários](autos/README.md) |
| [Autos e peças](autos/README.md) | [Motos](autos/README.md) |
| [Autos e peças](autos/README.md) | [Ônibus](autos/README.md) |
| [Autos e peças](autos/README.md) | [Caminhões](autos/README.md) |
| [Autos e peças](autos/README.md) | [Barcos e aeronaves](autos/README.md) |
| Peças e acessórios<sup>1</sup> | Carros vans e utilitários<sup>1</sup> |
| Peças e acessórios<sup>1</sup> | Motos<sup>1</sup> |
| Peças e acessórios<sup>1</sup> | Ônibus<sup>1</sup> |
| Peças e acessórios<sup>1</sup> | Caminhões<sup>1</sup> |
| Peças e acessórios<sup>1</sup> | Barcos e aeronaves<sup>1</sup> |
| Para a sua casa<sup>1</sup> | Móveis<sup>1</sup> |
| Para a sua casa<sup>1</sup> | Eletrodomésticos<sup>1</sup> |
| Para a sua casa<sup>1</sup> | Materiais de construção e jardim<sup>1</sup> |
| Para a sua casa<sup>1</sup> | Utilidades domésticas<sup>1</sup> |
| Para a sua casa<sup>1</sup> | Objetos de decoração<sup>1</sup> |
| Eletrônicos e celulares<sup>1</sup> | Videogames<sup>1</sup> |
| Eletrônicos e celulares<sup>1</sup> | Computadores e acessórios<sup>1</sup> |
| Eletrônicos e celulares<sup>1</sup> | Celulares e telefonia<sup>1</sup> |
| Eletrônicos e celulares<sup>1</sup> | Áudio TV vídeo e fotografia<sup>1</sup> |
| Música e hobbies<sup>1</sup> | Instrumentos musicais<sup>1</sup> |
| Música e hobbies<sup>1</sup> | CDs DVDs etc<sup>1</sup> |
| Música e hobbies<sup>1</sup> | Livros e revistas<sup>1</sup> |
| Música e hobbies<sup>1</sup> | Antiguidades<sup>1</sup> |
| Música e hobbies<sup>1</sup> | Hobbies e coleções<sup>1</sup> |
| Esportes e lazer<sup>1</sup> | Esportes e ginástica<sup>1</sup> |
| Esportes e lazer<sup>1</sup> | Ciclismo<sup>1</sup> |
| Artigos infantis<sup>1</sup> |  |
| Animais de estimação<sup>1</sup> | Cachorros e acessórios<sup>1</sup> |
| Animais de estimação<sup>1</sup> | Gatos e acessórios<sup>1</sup> |
| Animais de estimação<sup>1</sup> | Cavalos e acessórios<sup>1</sup> |
| Animais de estimação<sup>1</sup> | Aquários e acessórios<sup>1</sup> |
| Animais de estimação<sup>1</sup> | Roedores e acessórios<sup>1</sup> |
| Animais de estimação<sup>1</sup> | Outros animais e acessórios<sup>1</sup> |
| Moda e beleza<sup>1</sup> | Beleza e saúde<sup>1</sup> |
| Moda e beleza<sup>1</sup> | Roupas e calçados<sup>1</sup> |
| Moda e beleza<sup>1</sup> | Bolsas malas e mochilas<sup>1</sup> |
| Moda e beleza<sup>1</sup> | Bijouterias relógios e acessórios<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Tratores e máquinas agrícolas<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Máquinas pesadas para construção<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Máquinas para produção industrial<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Peças para tratores e máquinas<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Animais para agropecuária<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Produção Rural<sup>1</sup> |
| Agro e indústria<sup>1</sup> | Outros itens para agro e indústria<sup>1</sup> |
| Comércio e escritório<sup>1</sup> | Equipamentos e mobiliário<sup>1</sup> |
| Comércio e escritório<sup>1</sup> | Trailers e carrinhos comerciais<sup>1</sup> |
| Comércio e escritório<sup>1</sup> | Outros itens para comércio e escritório<sup>1</sup> |
| Serviços<sup>1</sup> |  |
| Vagas de emprego<sup>1</sup> |  |

<sup>1</sup> Estamos escrevendo a documentação gradualmente. Caso tenha interesse em integrar para uma categoria com documentação ainda não disponível, abra uma Issue ou entre em contato via suporteintegrador@olxbr.com.


## Deleção de Anúncios

Para uma deleção, basta enviar o `id` e a operação `delete`.

A seguir um JSON de exemplo com uma deleção:

```json
{
    "access_token": "ca18abccaadd282490e75173f98b8ec6f0c1c6c8",
    "ad_list": [
        {
            "id": "444444444",
            "operation": "delete"
        }
    ]
}
```

O anúncio permanecerá publicado a menos que uma operação de deleção seja enviada para a OLX Brasil com o `id` utilizado em sua inserção. Portanto recomendamos atenção redobrada para o integrador enviar a deleção para a OLX Brasil, para evitar que anúncios de produtos já vendidos continuem publicados - prejudicando a experiência do anunciante e do comprador.


## Retorno Esperado 
   
O formato do retorno de nosso servidor será do tipo JSON, que contém a seguinte estrutura:

| Paramêtro | Valor | Descrição |
|---------------|------------------------------------------|------------------------------------------------------------------------|
| `token` |  | Retorna uma string com um token a ser usado para posteriormente acessar o status da importação |
| `statusMessage` | | Explica o retorno síncrono da importação, com detalhamento de erros da validação síncrona. |
| `statusCode` | | Identifica o retorno síncrono da importação. |
| `errors` | `array` | Retorna uma lista de erros |

Os `statusCode` e `statusMessage` possíveis são os seguintes:

| Código | Mensagem | Descrição  |
|--------|-------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| `0` | `The ads were imported and will be processed` | No caso, os anúncios foram validados sincronamente. Não é garantia de publicação, dado que há a validação assíncrona posterior (moderação, etc). |
| `-1` | `Unexpected error` | Erro inesperado. |
| `-2` | `The request was blocked` | Usuário não pode importar pois está bloqueado temporariamente por excesso de requisições.    |
| `-3` | `There is no ad to import` | Não há anúncios para importar.   |
| `-4` | `An ad had problems on import` | Se um anúncio falhar em sua validação, a importação é cancelada.      |
| `-5` | `Import is down` | O serviço de importação está desativado.    |
| `-6` | `Without permission` | Usuário sem permissão.  |
| `-7` | `Trying to import <n> ad(s), but user just have slot for <f> more.` | O usuário está tentando importar <n> anúncios mas só podem importar mais <f>.    |
| `-8` | `Trying to import <n> ad(s), only <f> were imported and will be processed. The following ads were ignored due to limit exceeded: <t>` | Tentando importar <n> anúncios, só <f> foram importados e serão processados. Os seguintes anúncios foram ignorados devido ao limite excedido.    |

No caso do erro do tipo `-4`, alguma validação síncrona aconteceu e, por isso, algum dos anúncios deixou de ser importado com sucesso. Os possíveis motivos são os seguintes:

| Código | Descrição  |
|----------------------------------|--------------------------------------------|
| `ERROR_CATEGORY_INVALID` | Categoria inválida |
| `ERROR_REGION_MISSING` | Região inválida  |
| `ERROR_ZIPCODE_INVALID` | CEP inválido |
| `ERROR_TYPE_INVALID` | Tipo inválido |
| `ERROR_PHONE_INVALID` | Número de telefone inválido  |
| `ERROR_PHONE_TOO_SHORT` | Número de telefone muito curto |
| `ERROR_PHONE_TOO_LONG` | Número de telefone muito longo |
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
| `ERROR_OPERATION_INVALID` | Tipo de operação inválida   |

Eis exemplos de JSONs de retorno da API.

```json
{
    "token": "06fb235e216f3095ba913654d10afee2f55eae35",
    "statusCode": 0,
    "statusMessage": "The ads were imported and will be processed",
    "errors": []
}
```


```json
{
    "token": null,
    "statusCode": -4,
    "statusMessage": "An ad had problems on import",
    "errors": [
        {
            "id": "5555555555",
            "status": "error",
            "messages": [
                {
                    "category": "ERROR_CATEGORY_INVALID"
                }
            ]
        }
    ]
}
```

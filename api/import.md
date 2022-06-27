# Importação de Anúncios (Inserção/Edição/Deleção)

## Autenticação oAuth no OLX

Para utilizar a integração de anúncios via API, é necessário autenticar-se em nome de um usuário do OLX através do protocolo oAuth. A documentação da autenticação oAuth encontra-se [aqui](oauth.md).

Na autenticação, o sistema solicitante receberá o `client_id` e o `client_secret` que deverão ser usados na URL de conexão. Durante o fluxo oAuth será requisitado que o usuário dê permissão ao integrador para gerenciar seus anúncios na OLX. No *handshake* do oAuth, é requisitado também o `scope` que a aplicação-cliente necessitará. Para utilizar o sistema de integração de anúncios via API, é preciso o `scope` `autoupload`.


## Importação de Anúncios

O processo de integração de anúncios via API consiste no envio de um arquivo no formato JSON descrevendo um ou mais anúncios para inserção, edição ou deleção.

A URL usada para envio da requisição é: https://apps.olx.com.br/autoupload/import

O nosso servidor deve receber a chamada com método do tipo `PUT` e o header enviado deverá ser: `Content-type: application/json`. O formato do *encode* do JSON deverá ser `UTF-8` e o tamanho do payload não pode ultrapassar 1 MB.


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
| `Phone` |  | integer | sim | Telefone para contato. Mínimo de 10 e máximo de 11 caracteres. Enviar DDD + Telefone sem caracteres especiais ou espaços. |
| `type` | `s` ou `u`  | string | sim | Tipo de oferta do anúncio. `s` para venda e `u` para aluguel. |
| `price` |  | integer | não | Preço do anúncio (não aceita centavos) |
| `zipcode` |  | string numérica | sim | O CEP do anúncio. |
| `phone_hidden` | `true` ou `false`  | boolean | não | Ocultar telefone? `true` para ocultar e `false` para mostrar o telefone no anúncio. Caso não envie o comando o mesmo será interpretado como 'false'. Enviar os valores sem aspas |
| `params` |  | array | não<sup>1</sup> | Lista de parâmetros com as características do anúncio. Os valores dessa lista variam de acordo com a categoria do anúncio. |
| `images` | URL da imagem | array de string | não<sup>1</sup> | URL de imagens que serão inseridas no anúncio do olx.com.br. Não pode haver URLs repetidas neste array. Máximo de 20 imagens. Importante: a primeira imagem da lista será a imagem principal do anúncio! |
| `videos`<sup>2</sup> | URL do vídeo | array de string | não<sup>1</sup> | URL de vídeo<sup>3</sup>. que será inserida no anúncio do olx.com.br deve ser apenas do https://www.youtube.com/. Aceito 1 vídeo por anúncio! |

<sup>1</sup>: Se você não quer enviar um parâmetro não-obrigatório, deixe de enviar o parâmetro no payload. Se você enviar o parâmetro com valor vazio ou `0`, a operação vai falhar (a menos, é claro, que o valor `0` seja esperado para esse parâmetro).

<sup>2</sup>: **A inserção de vídeo está em fase Beta** e pode sofrer alterações com o tempo. **A disponibilidade via API é para categoria de Autos e Imóveis.**

<sup>3</sup> Formato recomendado de URL: https://www.youtube.com/watch?v=Vt&28raiI1q5

Segue um exemplo de envio de Vídeo: 

       },
        "videos": [
            "https://www.youtube.com/watch?v=Vt&28raiI1q5"
        ]
    },

***Observações:***

*- Caso seja necessário alterar o vídeo do anúncio, deve-se alterar a URL e realizar uma edição em outro campo, por exemplo: Descrição e título.*

*- Caso seja **enviado mais de um link** de vídeo no anúncio **será publicado apenas o primeiro da listagem.***

*- Em caso de **dúvidas entre em contato: video.experience@olxbr.com***


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
| [Peças e acessórios](autoparts/README.md)  | [Carros vans e utilitários](autoparts/README.md) |
| [Peças e acessórios](autoparts/README.md)| [Motos](autoparts/README.md) |
| [Peças e acessórios](autoparts/README.md) | [Ônibus](autoparts/README.md) |
| [Peças e acessórios](autoparts/README.md)| [Caminhões](autoparts/README.md) |
| [Peças e acessórios](autoparts/README.md) | [Barcos e aeronaves](autoparts/README.md) |
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

<sup>1</sup> Categoria não suportada atualmente pela API de Importação de Anúncios da OLX


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

| Código | Descrição  |
|-----------------------|-----------------------------------------|
| `UNDEFINED_AD_ID` | Anúncio enviado sem ID |
| `NOT_ENOUGH_AD_SLOTS` | Limite de inserção de anúncios atingido |
| `NO_IMAGE` | Anúncio enviado sem imagens |
| `NO_REGION` | CEP enviado corresponde a região inválida  |
| `NO_REGION` | CEP enviado em formato inválido |

Se você já é integrado com a OLX, [veja aqui o que muda com a nova API](autoupload_taffarel.md).


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
            "id": "78192371",
            "status": "error",
            "messages": [
                {
                    "category": "NO_REGION"
                }
            ]
        }
    ]
}
```

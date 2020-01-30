# Documentação para a Importação via XML para Imóveis na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de XML para o segmento de Imóveis.

Para que o cliente seja elegível à integração via XML com a OLX, seus anúncios devem ser disponibilizados no formato XML em uma URL pública, com o devido permissionamento para seu download em diferentes momentos do dia. Usualmente é feito um processo diário apenas.

O formato do encoding do arquivo a ser enviado deverá ser UTF8:

```xml
<?xml version="1.0" encoding="utf-8"?>
```


## Parâmetros básicos

Para a montagem do XML, é necessário respeitar parâmetros genéricos e específicos de cada categoria e/ou subcategoria. Os parâmtros básicos são os seguintes:

| Tag XML| Valor | Obrigatório? | Descrição|
|------------------------------------|-------------------|--------------|------------------------------------|
| `<CodigoImovel>` | String de até 20 caracteres | Sim | Também conhecido como `Ref` ou `External ID`, essa tag serve para te ajudar a identificar o anúncio depois de processado na OLX. |
| `<TituloAnuncio>` | Título com até 90 caracteres | Não | Título do Imóvel, que será mostrado na listagem de resultados |
| `<Titulo>` | Título com até 90 caracteres | Não | Título do Imóvel, que será mostrado na listagem de resultados.  Se o `<TituloAnuncio>` for preenchido, a tag `<Titulo>` é ignorada.   |
| `<Bairro>` | | Não | Esse campo só é utilizado para formar o título do anúncio, caso as tags `<TituloAnuncio>` ou `<Titulo>` não tenham sido preenchidas. Não é usado em nenhum outro lugar da OLX atualmente.|
| `<Cidade>` | | Não | Esse campo só é utilizado para formar o título do anúncio, caso as tags `<TituloAnuncio>` ou `<Titulo>` não tenham sido preenchidas. Não é usado em nenhum outro lugar da OLX atualmente. |
| `<SubTipoImovel>` | Consulte a SubCategoria para saber os valores aceitos em `<SubTipoImovel>` | Sim | Define a categoria onde o anúncio vai ser encontrado. |
| `<CEP>` | Para processamento, nós vamos limpar todo caractere não-numérico enviado. | Sim | Código de localização espacial do imóvel.  |
| `<Observacao>` | Descrição com até 6 mil caracteres | Sim | Descrição do anúncio. Não aceita tags HTML. Para quebra de linha, use a tag `\n` |
| `<PrecoVenda>` | Número inteiro, sem parte decimal, sem separador de milhares | Não | Valor de venda do imóvel.  |
| `<PrecoLocacao>` | Número inteiro, sem parte decimal, sem separador de milhares | Não | Valor de aluguel do imóvel. O `<PrecoLocacao>` será ignorado, caso o campo `<PrecoVenda>` seja preenchido também. |
| `<PrecoLocacaoTemporada>` | Número inteiro, sem parte decimal, sem separador de milhares | Não | Valor de aluguel por temporada do imóvel. O `<PrecoLocacaoTemporada>` será ignorado, se `<PrecoLocacao>` ou `<PrecoVenda>` seja preenchido também. |
| `<PrecoCondominio>` | Número inteiro, sem parte decimal, sem separador de milhares  | Não | Valor do condomínio do imóvel. |
| `<ValorIPTU>` | Número inteiro, sem parte decimal, sem separador de milhares | Não | Valor mensal do IPTU do imóvel.  |
| `<AreaTotal>` | Número inteiro, sem parte decimal | Não | Tamanho em metros quadrados do imóvel.  |
| `<AreaUtil>` | Número inteiro, sem parte decimal | Não | Tamanho em metros quadrados do imóvel. Se a `<AreaTotal>` for preenchida, a tag `<AreaUtil>` é ignorada. |
| `<Foto>` `<URLArquivo>` |  | Não | URL em que a imagem está hospedada |
| `<Foto>` `<Principal>` | `1` para definir a imagem principal | Não | Valor `1` caso a imagem seja a imagem principal do anúncio |


Cada subcategoria pode ter parâmetros específicos para cada uma delas. A documentação destas pode ser achada na página de cada subcategoria - onde também você encontrará exemplos de XMLs para cada subcategoria.

- [Apartamentos](sub_apartment.md)
- [Casas](sub_house.md)
- [Terrenos, sítios e fazendas](sub_land.md)
- [Comércio de Indústria](sub_commercial.md)

## Observações

Feita a avaliação de que os anúncios poderão ser adaptados ao formato XML e disponibilizados em uma URL, o cliente entrará em contato com a OLX informando que seus anúncios estão disponíveis para cadastro, solicitando a URL que contém os anúncios à empresa que as disponibiliza ou ao seu departamento de tecnologia. 

Obs.: Em alguns casos, será solicitado ao cliente que envie os dados de acesso da sua conta na OLX para validação de seu cadastro. 


## Inferência de Inserção, Edição e Deleção de Anúncios

A OLX funciona com um modelo de inserção paga de anúncios. Para a importação de anúncios via arquivo, a OLX vai inferir que há uma nova inserção quando houver um anúncio com identificador inédito. Para JSONs, o identificador é o parâmetro `CodigoImovel`, contido no XML.

Se um anúncio com um identificador já existente estiver no arquivo em uma nova importação, não realizaremos nenhuma operação, a menos que haja alguma alteração nas outras informações desses anúncio. Nesse caso, trataremos a operação como uma edição (e não inserção).

Para que ocorra a deleção de um anúncio, basta que ele deixe de existir no arquivo e, no próximo processamento dessa carga vamos inferir que esse anúncio deve ser removido. 

**Importante**: se um anúncio for removido e no próximo processamento ele voltar a aparecer no arquivo (ou, especificamente, se um determinado identificador deixar de existir no arquivo e, em outra importação, voltar a aparecer, vamos inferir (e, portanto, contabilizar) uma nova inserção. Por isso é crítico que um anúncio sempre esteja disponível com o mesmo identificador no arquivo e só deixe de aparecer quando de fato tivermos que removê-lo do seu inventário.

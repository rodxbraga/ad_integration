# Documentação para a Importação via XML para Imóveis na OLX

Este manual tem como objetivo auxiliar a implantação de importação de anúncios de XML para o segmento de Imóveis.

### Como integrar com a OLX?

Atendendo a este modelo de XML, o anunciante ou seu integrador ficam responsáveis por disponibilizar uma URL onde o XML ficará armazenada e sempre disponível, para que a OLX consulte o arquivo a cada importação.

A partir dos anúncios contidos no arquivo XML e o respectivo `<CodigoImovel>` contido em cada anúncio, a OLX vai inferir a inserção, edição ou deleção.


### Sobre a publicação dos anúncios

A OLX não utiliza necessariamente todos os campos previstos no formato ZAP, ainda que o portal siga este modelo. Além disso, a validação de cada campo pode ser diferente de outros portais onde o anunciante/integrador publica anúncios.

Além da validação contida nesse manual, há validações adicionais que são feitas sobre os anúncios. Com isso, a importação com sucesso dos anúncios não garante a publicação e/ou a permanência dos anúncios publicados. Caso infrinjam qualquer regra na OLX, o anúncio pode ser recusado imediatamente.

Abaixo está um exemplo de XML com os campos mínimos obrigatórios na OLX:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Carga xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <Imoveis>
    <Imovel>
      <CodigoCliente />
      <CodigoImovel>17-DU63501</CodigoImovel>
      <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
      <TipoImovel>Apartamento</TipoImovel>
      <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
      <CategoriaImovel>Padrão</CategoriaImovel>
      <Cidade>Porto Alegre</Cidade>
      <Bairro>Cidade Baixa</Bairro>
      <Endereco>Miguel Teixeira</Endereco>
      <Numero>66</Numero>
      <CEP>90050250</CEP>
      <PrecoVenda>482745</PrecoVenda>
      <PrecoLocacao>0</PrecoLocacao>
      <PrecoCondominio>1</PrecoCondominio>
      <ValorIPTU>500</ValorIPTU>
      <QtdVagas>0</QtdVagas>
      <AreaUtil>67</AreaUtil>
      <QtdDormitorios>1</QtdDormitorios>
      <Observacao>Residencial projetado para você em cada detalhe.\nPrédio com 2 Elevadores, Salão de Festas, Sala Fitness, Apartamento Zelador, Guarita e Bicicletário.\nRef.: 17-DU63501</Observacao>
      <Fotos>
        <Foto>
          <NomeArquivo>Imagem de Destaque Home - 500x500</NomeArquivo>
          <URLArquivo>http://multimidia.lopes.com.br/383/17-DU63501/apartamento-cidade-baixa-porto-alegre-imagem-iy8m8p_6349957eab f8c06807.jpg</URLArquivo>
        </Foto>
      </Fotos>
    </Imovel>
    <Imovel>
      <CodigoCliente />
      <CodigoImovel>17-DU65009</CodigoImovel>
      <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
      <TipoImovel>Apartamento</TipoImovel>
      <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
      <CategoriaImovel>Padrão</CategoriaImovel>
      <Cidade>Porto Alegre</Cidade>
      <Bairro>Auxiliadora</Bairro>
      <Endereco>Marcelo Gama</Endereco>
      <Numero>1030</Numero>
      <CEP>90540041</CEP>
      <PrecoVenda>536485</PrecoVenda>
      <PrecoLocacao>0</PrecoLocacao>
      <PrecoCondominio>1</PrecoCondominio>
      <ValorIPTU>500</ValorIPTU>
      <QtdVagas>0</QtdVagas>
      <AreaUtil>60</AreaUtil>
      <QtdDormitorios>2</QtdDormitorios>
      <Observacao>Apartamentos com dois dormitórios, suíte e vaga dupla e 1 dormitório com vaga e lavabo.\nAcabamento muito acima da média, apartamentos entregues com porcelanato nas áreas frias e laminado na sala e quartos, medidores de água e gás instalados, gesso, mármore e granito nos banheiros e cozinha. Todos os apartamentos possuem churrasqueira na cozinha. - Ref.: 17-DU65009</Observacao>
      <Fotos>
        <Foto>
          <NomeArquivo>Imagem de Destaque Home - 500x500</NomeArquivo>
          <URLArquivo>http://multimidia.lopes.com.br/383/17-DU65009/apartamento-auxiliadora-porto-alegre-imagem-ig5v7l_6500657eab57 356e8d.jpg</URLArquivo>
        </Foto>
      </Fotos>
    </Imovel>
    <Imovel>
      <CodigoCliente />
      <CodigoImovel>17-DU63821</CodigoImovel>
      <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
      <TipoImovel>Apartamento</TipoImovel>
      <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
      <CategoriaImovel>Padrão</CategoriaImovel>
      <Cidade>Porto Alegre</Cidade>
      <Bairro>Jardim Botânico</Bairro>
      <Endereco>Itaboraí</Endereco>
      <Numero>1158</Numero>
      <CEP>90670030</CEP>
      <Latitude>-23,4593654</Latitude>
      <Longitude>-46,5169560</Longitude>
      <PrecoVenda>298991</PrecoVenda>
      <PrecoLocacao>0</PrecoLocacao>
      <PrecoCondominio>1</PrecoCondominio>
      <ValorIPTU>500</ValorIPTU>
      <QtdVagas>0</QtdVagas>
      <AreaUtil>42</AreaUtil>
      <QtdDormitorios>1</QtdDormitorios>
      <Observacao>Apartamentos de 42m2 a 68m2, 1 e 2 dormitórios com suíte ou sem suíte e 1 vaga de garagem. Apartamentos com excelente orientação solar. Localizado no Bairro Jardim Botânico, próximo ao Shopping Bourbon Ipiranga, PUC e a todos os recursos do bairro. Condomínio conta, ainda com elevador, salão de festas, água quente e gás central. - Ref.: 17-DU63821</Observacao>
      <Fotos>
        <Foto>
          <NomeArquivo>Imagem de Destaque Home - 500x500</NomeArquivo>
          <URLArquivo>http://multimidia.lopes.com.br/383/17-DU63821/apartamento-jardim-botanico-porto-alegre-imagem-iy0b2g_63820560 163a8c514c.jpg</URLArquivo>
          <Alterada>1</Alterada>
        </Foto>
      </Fotos>
    </Imovel>
    <Imovel>
      <CodigoCliente />
      <CodigoImovel>17-DU65007</CodigoImovel>
      <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
      <TipoImovel>Apartamento</TipoImovel>
      <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
      <CategoriaImovel>Padrão</CategoriaImovel>
      <Cidade>Porto Alegre</Cidade>
      <Bairro>Auxiliadora</Bairro>
      <Endereco>Marcelo Gama</Endereco>
      <Numero>1030</Numero>
      <CEP>90540041</CEP>
      <PrecoVenda>367387</PrecoVenda>
      <PrecoLocacao>0</PrecoLocacao>
      <PrecoCondominio>1</PrecoCondominio>
      <ValorIPTU>500</ValorIPTU>
      <QtdVagas>0</QtdVagas>
      <AreaUtil>39</AreaUtil>
      <QtdDormitorios>1</QtdDormitorios>
      <Observacao>Apartamentos com dois dormitórios, suíte e vaga dupla e 1 dormitório com vaga e lavabo. Acabamento muito acima da média, Apartamentos entregues com porcelanato nas áreas frias e laminado na sala e quartos, medidores de água e gás instalados, gesso, mármore e granito nos banheiros e cozinha. Todos os apartamentos possuem churrasqueira na cozinha. - Ref.: 17-DU65007</Observacao>
      <Fotos>

        <Foto>
          <NomeArquivo>Imagem de Destaque Home - 500x500</NomeArquivo>
          <URLArquivo>http://multimidia.lopes.com.br/383/17-DU65007/apartamento-auxiliadora-porto-alegre-imagem-ig5v7l_6500657eab57 356e8d.jpg</URLArquivo>
        </Foto>
      </Fotos>
    </Imovel>
  </Imoveis>
</Carga>
```

Para que o cliente seja elegível à integração via XML com a OLX, seus anúncios devem ser disponibilizados no formato ZAP XML via URL.

Feita a avaliação de que os anúncios poderão ser adaptados ao formato XML e disponibilizados em uma URL, o cliente entrará em contato com a OLX informando que seus anúncios estão disponíveis para cadastro, solicitando a URL que contém os anúncios à empresa que as disponibiliza ou ao seu departamento de tecnologia. 

Obs.: Em alguns casos, será solicitado ao cliente que envie os dados de acesso da sua conta na OLX para validação de seu cadastro. 

| Tag XML| Tamanho | Obrigatório? | Descrição|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|--------------|---------------------------------------------------------------------------------------------|
| `<CodigoImovel>` | 20 | Sim | Referência do anúncio no banco de dados do cliente|
| `<TituloAnuncio>` | 20 | Não | Título do Imóvel, que será mostrado na listagem de resultados|
| `<TipoImovel>` | 40 | Sim | Classificação do imóvel (ex.: Apartamentos, Casa, Terreno, etc)|
| `<SubTipoImovel>` | 40 | Sim | Segunda classificação (ex.: Casa de Vila, Casa de Condominio)|
| `<CategoriaImovel>` | 30 | Sim | Classificação do imóvel|
| `<CEP>` | 8 | Sim | Código de localização espacial do imóvel|
| `<PrecoVenda>` | 8 | Sim | Valor de venda do imóvel. Número inteiro, sem parte decimal, sem separador de milhares|
| `<PrecoLocacao>` | 8 | Sim | Valor de aluguel do imóvel. Número inteiro, sem parte decimal, sem separador de milhares|
| `<PrecoCondominio>` | 8 | Não | Valor do condomínio do imóvel. Número inteiro, sem parte decimal, sem separador de milhares|
| `<ValorIPTU>` | 20 | Não | Valor mensal do IPTU do imóvel. Número inteiro, sem parte decimal, sem separador de milhares|
| `<AreaTotal>` | 15 | Não | Tamanho em metros quadrados do imóvel. Número inteiro, sem parte decimal|
| `<AreaUtil>` | 15 | Não | Tamanho em metros quadrados do imóvel. Número inteiro, sem parte decimal|
| `<QtdDormitorios>` | 1 | Sim | Número de quartos do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel mais de 5 dormitórios.|
| `<Observacao>` | 6000 | Sim | Descrição do anúncio|
| `<QtdVagas>` | 4 | Não | Número de vagas do imóvel. Valores de `1` a `5`. Com o valor `5`, informamos que o imóvel mais de 5 vagas.|
| `<ArCondicionado>`,<br>`<SalaGinastica>`,<br>`<ArmarioEmbutido>`,<br>`<Varanda>`,<br>`<AreaServico>`,<br>`<Churrasqueira>`,<br>`<QuartoWCEmpregada>`,<br>`<Piscina>`,<br>`<SalaoFestas>`,<br>`<Porteiro>`||| Características adicionais do imóvel. Se o imóvel tem algum desses atributos, inclua esse parâmetro com valor `1`|
| `<Foto>` `<NomeArquivo>` | 255 | Não | Nome da imagem no banco de dados do cliente|
| `<Foto>` `<URLArquivo>` | 255 | Não | Link em que a imagem está hospedada|


## Título e categorização dos anúncios

Essas informações definem a categorização dos anúncios dentro da OLX. É necessário informar o `<SubTipoImovel>` para que o imóvel seja apresentado na categoria correta.

Caso o campo `<TituloAnuncio>` esteja em branco no XML enviado, utilizaremos o Título apropriado para cada categoria e tipo de imóvel, conforme tabelas abaixo.

#### Para que seu anúncio apareça na categoria `Apartamentos`, na OLX:

| `<TipoImovel>` | `<SubTipoImovel>` | `<CategoriaImovel>` | Título do anúncio (OLX)      |
|---------------------|---------------------------------|------------------------  |-------------------------     |
| Apartamento | Loft | Duplex | Loft Duplex  |
| Apartamento | Loft | Triplex | Loft Triplex  |
| Apartamento | Loft | Padrão | Loft |
| Apartamento | Apartamento Padrão | Cobertura | Cobertura |
| Apartamento | Apartamento Padrão | Duplex | Duplex |
| Apartamento | Apartamento Padrão | Triplex | Triplex |
| Apartamento | Apartamento Padrão | Cobertura Duplex  | Cobertura Duplex  |
| Apartamento | Apartamento Padrão | Cobertura Triplex  | Cobertura Triplex  |
| Apartamento | Apartamento Padrão | Padrão | Apartamento |
| Apartamento | Kitchenette/ Conjugados | Padrão | Conjugado |
| Flat/Aparthotel | Flat | Padrão | Flat/Aparthotel |
| Flat/Aparthotel | Flat | Padrão | Flat/Aparthotel |
| Apartamento Duplex | Apartamento Duplex Residencial | Padrão |Duplex |
| Apartamento Triplex | Apartamento Triplex Residencial | Padrão | Triplex |
| Cobertura | Cobertura Residencial | Padrão | Cobertura |
| Flat | Flat Residencial | Padrão | Flat/Aparthotel |
| Apartamento | Apartamento Residencial | Padrão | Apartamento |
| Apartamento | Apartamento de Condomínio | Padrão | Apartamento |
| Kitnet | Kitnet Residencial | Padrão | Conjugado |


#### Para que seu anúncio apareça na categoria `Casas`, na OLX:

| `<TipoImovel>` | `<SubTipoImovel>` | `<CategoriaImovel>` | Título do anúncio (OLX)      |
|------------------|-----------------------    |------------------------  |--------------------|
| Casa | Casa de Condomínio   | Sobrado/Duplex | Casa de Condomínio     |
| Casa | Casa de Condomínio   | Sobrado/Triplex | Casa de Condomínio   |
| Casa | Casa de Condomínio   | Térrea | Casa de Condomínio     |
| Casa | Casa de Condomínio   | Padrão | Casa de Condomínio     |
| Casa | Casa de Vila    | Sobrado/Duplex | Casa de Vila    |
| Casa | Casa de Vila    | Sobrado/Triplex | Casa de Vila    |
| Casa | Casa de Vila    | Térrea | Casa de Vila    |
| Casa | Casa Padrão   | Sobrado/Duplex | Casa |
| Casa | Casa Padrão   | Sobrado/Triplex | Casa |
| Casa | Casa Padrão   | Térrea | Casa |
| Casa | Casa Padrão   | Padrão | Casa |
| Sobrado | Sobrado Residencial | Padrão | Sobrado |

#### Para que seu anúncio apareça na categoria `Comércio e indústria`, na OLX:

| `<TipoImovel>` | `<SubTipoImovel>` | `<CategoriaImovel>` | Título do anúncio (OLX)      |
|-----------------------|-------------------------- |------------------------  |--------------------------|
| Comercial | Casa Comercial  | Padrão | Casa Comercial  |
| Comercial | Conjunto Comercial / Sala | Padrão | Conjunto Comercial |
| Comercial | Loja/Salão | Padrão | Loja / Salão     |
| Comercial | Hotel | Padrão | Hotel |
| Comercial/Industrial | Box/Garagem | Padrão | Box / Garagem |
| Comercial/Industrial | Conjunto Comercial / Sala | Padrão | Conjunto Comercial |
| Comercial/Industrial | Galpão / Depósito / Armazém   | Padrão | Galpão / Depósito / Armazém   |
| Comercial/Industrial | Loja / Salão | Padrão | Loja / Salão |
| Comercial/Industrial | Prédio Inteiro   | Padrão | Prédio Comercial   |

#### Para que seu anúncio apareça na categoria `Terrenos, sítios e fazendas`, na OLX:

| `<TipoImovel>` | `<SubTipoImovel>` | `<CategoriaImovel>` | Título do anúncio (OLX)      |
|-------------------  |------------------------   |------------------------  |------------------------|
| Terreno | Terreno Padrão   | Padrão | Terreno |
| Terreno | Loteamento/Condomínio | Padrão | Loteamento/Condomínio |
| Chácara | Chácara Rural   | Padrão | Chácara |
| Sítio | Sítio Rural   | Padrão | Sítio |


### Observações

Orientamos que as fotos precisam estar obrigatoriamente no tamanho igual ou superior a 260 x 350 pixels, além de formato compatível (JPG ou PNG).

O formato do encoding do arquivo a ser enviado deverá ser UTF8:

```xml
<?xml version="1.0" encoding="utf-8"?>
```

## Dúvidas e sugestões

Em caso de dúvidas sobre o processo de importação via XML na OLX, entre em contato com suporteintegrador@olxbr.com.

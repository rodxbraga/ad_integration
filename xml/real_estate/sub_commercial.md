### Subcategoria `Comércio e indústria`

Para esta subcategoria, é necessário preencher o parâmetro `<SubTipoImovel>` com os seguintes valores:

| `<SubTipoImovel>` | Título do anúncio |
|---------------------------------------|-------------------------|
| `Andar` | Escritório |
| `Casa Comercial` | Escritório |
| `Conjunto Comercial` | Escritório |
| `Conjunto Comercial / Sala` | Escritório |
| `Laje Comercial` | Escritório |
| `Salão Comercial` | Escritório |
| `Sobrado Comercial` | Escritório |
| `Área Comercial` | Galpão/Depósito/Armazém |
| `Galpão / Depósito / Armazém`   | Galpão/Depósito/Armazém |
| `Galpão / Depósito / Barracão`  | Galpão/Depósito/Armazém |
| `Galpão Comercial` | Galpão/Depósito/Armazém |
| `Indústria` | Galpão/Depósito/Armazém |
| `Box Garagem` | Garagem/vaga |
| `Hotel` | Hotel |
| `Hotel Residencial` | Hotel |
| `Motel` | Hotel |
| `Pousada / Chalé` | Hotel |
| `Barracão Comercial` | Loja Comercial |
| `Centro Comercial` | Loja Comercial |
| `Comercial` | Loja Comercial |
| `Loja` | Loja Comercial |
| `Loja Comercial` | Loja Comercial |
| `Loja de Shopping` | Loja Comercial |
| `Loja de Shopping / Centro Comercial` | Loja Comercial |
| `Loja Salão` | Loja Comercial |
| `Ponto Comercial` | Loja Comercial |
| `Prédio` | Prédio Comercial |
| `Prédio Comercial` | Prédio Comercial |
| `Prédio Inteiro` | Prédio Inteiro |
| `Sala` | Sala Comercial |
| `Sala Comercial` | Sala Comercial |


Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:

| Parâmetro | Valor | Obrigatório | Descrição |
|------------------|---------|------------------|-------------|
| `<SubTipoImovel>` | Consulte tabela anterior | Sim | Define a categoria onde o anúncio estará localizado na OLX |
| `QtdVagas` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | Não | Quantidade de vagas de garagem |



Aqui está um exemplo de XML para inserção ou edição de anúncios na subcategoria `Comércio e indústria`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Carga xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <Imoveis>
        <Imovel>
            <CodigoImovel>17-DU63501</CodigoImovel>
            <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <Cidade>Porto Alegre</Cidade>
            <Bairro>Cidade Baixa</Bairro>
            <CEP>90050250</CEP>
            <PrecoVenda>482745</PrecoVenda>
            <PrecoLocacao>0</PrecoLocacao>
            <PrecoCondominio>1</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>0</QtdVagas>
            <AreaUtil>67</AreaUtil>
            <QtdDormitorios>1</QtdDormitorios>
            <Observacao>Residencial projetado para você em cada detalhe.\nPrédio com Piscina.\nMuito legal, você deveria visitar!</Observacao>
            <Piscina>1</Piscina>
            <Fotos>
                <Foto>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal.jpg</URLArquivo>
                </Foto>
                <Foto>
                    <Principal>1</Principal>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal2.jpg</URLArquivo>
                </Foto>
            </Fotos>
        </Imovel>
        <Imovel>
            <CodigoImovel>17-DU65009</CodigoImovel>
            <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
            <TipoImovel>Apartamento</TipoImovel>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <CategoriaImovel>Padrão</CategoriaImovel>
            <Cidade>Porto Alegre</Cidade>
            <Bairro>Auxiliadora</Bairro>
            <CEP>90540041</CEP>
            <PrecoVenda>536485</PrecoVenda>
            <PrecoCondominio>1000</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>2</QtdVagas>
            <QtdBanheiros>2</QtdBanheiros>
            <AreaUtil>60</AreaUtil>
            <QtdDormitorios>2</QtdDormitorios>
            <Observacao>Apartamentos com dois dormitórios, suíte e vaga dupla e 1 dormitório com vaga e lavabo.\nAcabamento muito acima da média, apartamentos entregues com porcelanato nas áreas frias e laminado na sala e quartos, medidores de água e gás instalados, gesso, mármore e granito nos banheiros e cozinha. Todos os apartamentos possuem churrasqueira na cozinha. - Ref.: 17-DU65009</Observacao>
            <Fotos>
                <Foto>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal.jpg</URLArquivo>
                </Foto>
                <Foto>
                    <Principal>1</Principal>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal2.jpg</URLArquivo>
                </Foto>
            </Fotos>
        </Imovel>
        <Imovel>
            <CodigoImovel>17-DU63821</CodigoImovel>
            <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
            <TipoImovel>Apartamento</TipoImovel>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <CategoriaImovel>Padrão</CategoriaImovel>
            <Cidade>Porto Alegre</Cidade>
            <Bairro>Jardim Botânico</Bairro>
            <CEP>90670030</CEP>
            <PrecoLocacao>5000</PrecoLocacao>
            <PrecoCondominio>1000</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>0</QtdVagas>
            <AreaUtil>42</AreaUtil>
            <QtdDormitorios>1</QtdDormitorios>
            <Observacao>Apartamentos de 42m2 a 68m2, 1 e 2 dormitórios com suíte ou sem suíte e 1 vaga de garagem. Apartamentos com excelente orientação solar. Localizado no Bairro Jardim Botânico, próximo ao Shopping Bourbon Ipiranga, PUC e a todos os recursos do bairro. Condomínio conta, ainda com elevador, salão de festas, água quente e gás central. - Ref.: 17-DU63821</Observacao>
            <Fotos>
                <Foto>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal.jpg</URLArquivo>
                </Foto>
                <Foto>
                    <Principal>1</Principal>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal2.jpg</URLArquivo>
                </Foto>
            </Fotos>
        </Imovel>
        <Imovel>
            <CodigoImovel>17-DU65007</CodigoImovel>
            <TituloAnuncio>Apartamento espaçoso</TituloAnuncio>
            <SubTipoImovel>Apartamento Padrão</SubTipoImovel>
            <Cidade>Porto Alegre</Cidade>
            <Bairro>Auxiliadora</Bairro>
            <CEP>90540041</CEP>
            <PrecoVenda>367387</PrecoVenda>
            <PrecoCondominio>1000</PrecoCondominio>
            <ValorIPTU>500</ValorIPTU>
            <QtdVagas>0</QtdVagas>
            <AreaUtil>39</AreaUtil>
            <QtdDormitorios>1</QtdDormitorios>
            <Observacao>Apartamentos com dois dormitórios, suíte e vaga dupla e 1 dormitório com vaga e lavabo. Acabamento muito acima da média, Apartamentos entregues com porcelanato nas áreas frias e laminado na sala e quartos, medidores de água e gás instalados, gesso, mármore e granito nos banheiros e cozinha. Todos os apartamentos possuem churrasqueira na cozinha. - Ref.: 17-DU65007</Observacao>
            <Fotos>
                <Foto>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal.jpg</URLArquivo>
                </Foto>
                <Foto>
                    <Principal>1</Principal>
                    <URLArquivo> http://www.site_da_imobiliaria.com/foto_legal2.jpg</URLArquivo>
                </Foto>
            </Fotos>
        </Imovel>
    </Imoveis>
</Carga>
```
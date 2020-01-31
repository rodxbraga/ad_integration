### Subcategoria `Terrenos, sítios e fazendas`

Para esta subcategoria, é necessário preencher o parâmetro `<SubTipoImovel>` com os seguintes valores:

| `<SubTipoImovel>` | Título do anúncio |
|-------------------------|-----------------------|
| `Loteamento Condomínio` | Loteamento/condomínio |
| `Loteamento Padrão` | Loteamento/condomínio |
| `Sítio` | Sítio |
| `Sítio Chácara` | Sítio |
| `Sítio Rural` | Sítio |
| `Terreno` | Terreno |
| `Terreno Padrão` | Terreno |
| `Chácara` | Chácara |
| `Chácara Rural` | Chácara |
| `Fazenda` | Chácara |
| `Fazenda Rural` | Chácara |
| `Haras` | Chácara |
| `Haras Rural` | Chácara |

Caso não seja enviado nenhum valor para `<TituloAnuncio>`, será montado um título para o anúncio baseado no `<SubTipoImovel>` e outros atributos, como número de quartos, localização, etc. 


Aqui está um exemplo de XML para inserção ou edição de anúncios na subcategoria `Terrenos, sítios e fazendas`:

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
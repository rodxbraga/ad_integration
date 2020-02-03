### Subcategoria `Casas`

Para esta subcategoria, é necessário preencher o parâmetro `<SubTipoImovel>` com os seguintes valores:

| `<SubTipoImovel>` | Título do anúncio |
|-----------------------|--------------------|
| `Casa` | Casa |
| `Casa de Rua` | Casa |
| `Casa Padrão` | Casa |
| `Casa Padrão Térrea` | Casa |
| `Casa Residencial` | Casa |
| `Sobrado` | Casa |
| `Sobrado Residencial` | Casa |
| `Village Residencial` | Casa |
| `Casa de Condomínio` | Casa de condomínio |
| `Casa em Condomínio` | Casa de condomínio |
| `Casa de Vila` | Casa de vila |

Além disso, há parâmetros específicos para esta subcategoria, que devem constar dentro do parâmetro `params` e preenchidos conforme a tabela a seguir:


| Parâmetro | Valor | Obrigatório | Descrição |
|------------------|---------|------------------|-------------|
| `<SubTipoImovel>` | Consulte tabela anterior | Sim | Define a categoria onde o anúncio estará localizado na OLX |
| `<QtdDormitorios>` | `0` para 0 quartos<br> `1` para 1 quarto<br> `2` para 2 quartos<br> `3` para 3 quartos<br> `4` para 4 quartos<br> `5` para 5 ou mais quartos<br> | Sim | Quantidade de quartos |
| `<QtdBanheiros>` | `0` para 0 banheiros<br>`1` para 1 banheiro<br> `2` para 2 banheiros<br> `3` para 3 banheiros<br> `4` para 4 banheiros<br> `5` para 5 ou mais banheiros<br> | Não | Quantidade de banheiros |
| `<QtdVagas>` | `0` para 0 vagas<br> `1` para 1 vaga<br> `2` para 2 vagas<br> `3` para 3 vagas<br> `4` para 4 vagas<br> `5` para 5 ou mais vagas<br> | Não | Quantidade de vagas de garagem |

Aqui está um exemplo de XML para inserção ou edição de anúncios na subcategoria `Casas`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Carga xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <Imoveis>
        <Imovel>
            <CodigoImovel>CASA001</CodigoImovel>
            <TituloAnuncio>Casa Agradável No Melhor Bairro da Cidade</TituloAnuncio>
            <SubTipoImovel>Casa Residencial</SubTipoImovel>
            <Cidade>São Paulo</Cidade>
            <Bairro>Perdizes</Bairro>
            <CEP>05018000</CEP>
            <PrecoVenda>500000</PrecoVenda>
            <ValorIPTU>500</ValorIPTU>
            <QtdDormitorios>3</QtdDormitorios>
            <QtdVagas>2</QtdVagas>
            <QtdBanheiros>2</QtdBanheiros>
            <AreaUtil>67</AreaUtil>
            <Observacao>A melhor casa do bairro, prontinha para você morar!\nFica perto de um parque bem grande, cheio de árvore.\nMuito legal, você deveria visitar!</Observacao>
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
# Documentação da API de Integração de Anúncios da OLX 

A nova versão API de Integração de Anúncios da OLX está em construção. A documentação será escrita e disponibilizada nesse repositório, mas por enquanto vamos já alinhando sobre as primeiras mudanças necessárias.

## Ajuste inicial de chamadas da nova API

Nós estamos trabalhando para melhorar a experiência de integração com a OLX. Estamos ajustando nossa API para garantir uma maior disponibilidade e performance para o gerênciamento do seu anúncio. A API tem como objetivo dar maior transparência do status do seu anúncio, assim como facilitar a manipulação do mesmo.

Nesse primeiro momento precisamos uniformizar as chamadas que são feitas para a API. A versão atualmente aceita chamadas feitas incorretamente e, para avançarmos na nova versão, precisamos ajustar esse ponto. Os endpoints que podem ser utilizados para a importação e consulta de status deverão receber chamadas seguindo o padrão:

### Inserção e deleção
`PUT /autoupload/import`<br>
header: `Content-type: application/json`
### Status
`POST /autoupload/import/{id}`<br>
header: `Content-type: application/json`

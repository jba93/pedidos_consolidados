# Pedidos Consolidados

### Tecnologias utilizadas
Pentaho Data Integration e Excel

### Desafio
https://arrudaconsulting.com.br/

### Descrição
Pipeline de dados criado com o Pentaho Data Integration (Spoon) realizado no treinamento Pentaho + Excel oferecido pelo Arruda Consulting, com diversas modificações feitas por mim.

O arquivo "transformacao.ktr" é uma transformação do Pentaho que inicia lendo os dados de três planilhas do Excel, localizadas dentro da pasta "planilhas": 
- Clientes.xlsx: com informações do cliente como id, nome, endereço, telefone;
- Pedidos.xlsx: com id do cliente, id do vendedor, datas de pedido e entrega, tipo e peso de frete;
- Pedidos_Detalhados.xlsx: com id de pedido, id de produto, preço unitário, quantidade e desconto.

A transformação junta os dados desses três arquivos em uma única tabela e trata seus dados através de algumas ações:
- Formatação de datas;
- Identificação de rua e número para formar um campo de endereço padronizado;
- Remoção de caracteres especiais de strings;
- Padroniza o nome de países;
- Troca campos nulos por valores padrão;
- Calcula o tempo (em dias) da data do pedido até a data de entrega do produto e classifica o atraso (se houver) em quatro níveis;
- Calcula o valor total do pedido, levando em consideração o preço unitário do produto, a quantidade de produtos e também o desconto percentual.

Sendo assim, são gerados três novos arquivos:
- PedidosFalhos.xlsx: onde estão os pedidos que não tiveram data de entrega preenchida corretamente;
- ConsolidacaoPedidos.xlsx: onde estão todos os pedidos válidos juntamente com as informações dos produtos que estavam em cada pedido (pedidos atrasados e não atrasados);
- PedidosAtrasados.xlsx: onde estão apenas os pedidos que sofreram atrasos, juntamente com o nível do atraso.

Através desses três novos arquivos, é possível realizar análises, como:
- Quais vendedores tiveram mais pedidos consolidados?
- Quais produtos são mais vendidos?
- Dentre os pedidos que sofreram atraso, qual é o tipo de frete mais comum?

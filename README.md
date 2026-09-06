# **H&M Analytics**
 
## Sobre o projeto
 
Este projeto aplica Customer e Product Analytics aos dados transacionais da H&M, buscando entender a recorrência dos clientes e sua relação com as características dos consumidores, os grupos de produtos e os canais comerciais.
 
O objetivo é identificar quais combinações de clientes, produtos e canais devem ser priorizadas em ações de CRM e em decisões de produto.
 
## Perguntas do projeto
 
A análise é orientada pelas seguintes perguntas:
 
- Qual é o nível de recorrência dos clientes e como ele evolui no período observado?
- Quanto os clientes recorrentes representam do volume de itens e do valor transacionado observado?
- Quais características e coortes de primeira compra observada apresentam maior recorrência, frequência e valor?
- Quais grupos de produtos estão associados à primeira compra observada e às compras posteriores?
- Como os canais comerciais se relacionam com recorrência, frequência, valor e preferência por produtos?

## Fonte dos dados
 
Os dados são provenientes da competição [H&M Personalized Fashion Recommendations](https://www.kaggle.com/competitions/h-and-m-personalized-fashion-recommendations/data), disponibilizada pela H&M no Kaggle.

Foram utilizadas três bases:

- `articles.csv`: atributos e classificações dos artigos;
- `customers.csv`: características cadastrais dos clientes;
- `transactions_train.csv`: histórico de itens comprados entre setembro de 2018 e setembro de 2020.
 
## Inspeção dos dados
 
Cada base foi avaliada quanto ao tamanho, aos tipos de coluna, à cardinalidade, aos valores ausentes, aos registros repetidos e aos relacionamentos entre as tabelas.
 
### Principais resultados:

- Todos os clientes e artigos presentes nas transações possuem correspondência em suas respectivas bases;
- Articles possui 105.542 registros;
- Customers possui 1.371.980 registros;
- Transactions possui 31.788.324 registros de itens comprados;
- As transações abrangem o período de setembro de 2018 a setembro de 2020;
- Em relação aos valores ausentes e duplicados: Articles não possui valores ausentes ou duplicados. As ausências encontradas nos dados dos clientes foram preservadas, e os registros repetidos de transactions foram mantidos, pois podem representar múltiplas unidades compradas.
 
## Limpeza e padronização
 
As principais transformações aplicadas foram:
 
- remoção de detail_desc, que não será utilizada na análise;
- remoção de postal_code, já que o conteúdo anonimizado não permite interpretação geográfica;
- conversão dos identificadores de artigos e produtos para texto;
- conversão dos códigos de classificação para variáveis categóricas;
- padronização de FN e Active em letras minúsculas;
- padronização de club_member_status e fashion_news_frequency em letras maiúsculas;
- conversão de age para inteiro anulável;
- conversão de t_dat para data;
- preservação dos valores ausentes, das categorias oficiais e dos registros repetidos.
- Preservação das linhas durante o processo.
 
## Validação das bases processadas
 
As três bases tratadas foram exportadas em Parquet com compressão Snappy e validadas por meio dos metadados:
 
| Arquivo | Linhas | Colunas | Tamanho aproximado |
|---|---|---|---|
| articles_clean.parquet | 105.542 | 24 | 2,91 MB |
| customers_clean.parquet | 1.371.980 | 6 | 80,64 MB |
| transactions_clean.parquet | 31.788.324 | 5 | 736,01 MB

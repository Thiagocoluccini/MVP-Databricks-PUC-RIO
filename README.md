# Steam Games Analytics – Projeto de Engenharia de Dados e Analytics

## Visão Geral do Projeto

Este projeto tem como objetivo realizar uma análise analítica sobre jogos disponíveis na plataforma Steam, explorando informações relacionadas a avaliações dos usuários, preços, gêneros, publishers, developers e métricas externas como o Metacritic.

O trabalho foi desenvolvido com foco em conceitos de engenharia de dados, arquitetura em camadas (Bronze, Silver e Gold) e modelagem analítica utilizando um Data Warehouse em modelo estrela, com o objetivo de preparar os dados para consumo em ferramentas de Business Intelligence, como o Power BI.

---

## Objetivos do Projeto

- Construir um pipeline de dados organizado e escalável  
- Realizar a ingestão, tratamento e padronização de dados brutos  
- Criar métricas analíticas confiáveis para avaliação de jogos  
- Estruturar um modelo dimensional (tabela fato e dimensões)  
- Disponibilizar os dados para análise e visualização em ferramentas de BI  

---

## Fonte dos Dados

Os dados utilizados neste projeto foram obtidos a partir do Kaggle:

Steam Games Dataset  
https://www.kaggle.com/datasets/artermiloff/steam-games-dataset

O dataset contém informações como:
- Nome do jogo  
- Avaliações positivas e negativas da Steam  
- Preço  
- Data de lançamento  
- Gêneros  
- Developer e Publisher  
- Nota do Metacritic  
- Compatibilidade com sistemas operacionais  

---

## Arquitetura do Projeto

O projeto segue a arquitetura conhecida como Medallion Architecture, dividida nas camadas Bronze, Silver e Gold.

### Camada Bronze

A camada Bronze é responsável pela ingestão dos dados brutos a partir do arquivo CSV.  
Nessa etapa foram realizadas análises exploratórias iniciais com o objetivo de compreender a estrutura dos dados, identificar problemas de qualidade e mapear possíveis ajustes necessários para as próximas etapas do pipeline.

O objetivo principal dessa camada é preservar os dados em seu formato original, garantindo rastreabilidade e possibilitando reprocessamentos futuros.

---

### Camada Silver

Na camada Silver foram aplicadas transformações para limpeza, padronização e enriquecimento dos dados.  
Entre as principais atividades realizadas estão:

- Tratamento de valores inválidos ou inconsistentes  
- Padronização de campos textuais  
- Criação de novas colunas analíticas, como:
  - Ano de lançamento  
  - Total de avaliações  
  - Percentual de aprovação  
  - Aprovação ponderada (weighted rating)  
- Tratamento avançado de gêneros, incluindo separação, normalização e identificação de jogos indie  
- Normalização de publishers e developers  
- Consolidação dos dados em uma tabela analítica confiável  

O objetivo dessa camada é fornecer dados consistentes e preparados para modelagem analítica.

---

### Camada Gold

A camada Gold tem como foco a modelagem analítica dos dados, estruturando-os em um modelo de Data Warehouse no formato estrela.

Foram criadas as seguintes tabelas dimensão:
- DIM_JOGO  
- DIM_TEMPO  
- DIM_GENRE  
- DIM_PUBLISHER  
- DIM_DEVELOPER  

Além disso, foi construída a tabela fato central contendo as principais métricas agregadas, com relacionamento às dimensões por meio de chaves substitutas.

Ao final do processo, foi criada uma view analítica consolidada, projetada para facilitar o consumo dos dados em ferramentas de BI.

---

## Modelagem Dimensional

O modelo adotado segue o padrão estrela, com uma tabela fato central e tabelas dimensão ao redor.

As principais métricas disponíveis incluem:
- Total de avaliações  
- Percentual de aprovação  
- Aprovação ponderada  
- Preço médio  
- Nota do Metacritic  

Essa estrutura permite análises como:
- Jogos mais bem avaliados  
- Relação entre preço e avaliação  
- Comparação entre avaliações da Steam e do Metacritic  
- Análises por gênero, publisher, developer e período de lançamento  

---

## Visualização e Análises

Os dados da camada Gold foram consumidos no Power BI, possibilitando a criação de dashboards e análises interativas, incluindo rankings, análises comparativas e segmentações por diferentes dimensões do modelo.

---

## Tecnologias Utilizadas

- Databricks  
- Apache Spark (PySpark e SQL)  
- Delta Lake  
- Power BI  
- Git e GitHub  

---

## Como Navegar pelo Projeto

1. Iniciar pelo notebook da camada Bronze  
2. Avançar para o notebook da camada Silver  
3. Finalizar com o notebook da camada Gold  
4. Utilizar a view final para consumo em ferramentas de BI
5. Utilizar o arquivo em PDF de documentação de evidência do MVP, caso queira visualizar a documentação e resposta das pautas levantadas no começo do notebook bronze

Cada notebook contém comentários e explicações sobre as transformações realizadas.

---

## Considerações Finais

Este projeto foi desenvolvido com foco em boas práticas de engenharia de dados, organização, clareza e escalabilidade.  
A estrutura adotada permite fácil manutenção, expansão e reutilização do pipeline, podendo ser adaptada para novas fontes de dados, métricas adicionais ou atualizações incrementais.

---

Autor: Thiago Coluccini
Linkedin: www.linkedin.com/in/thiago-coluccini
Projeto acadêmico / portfólio

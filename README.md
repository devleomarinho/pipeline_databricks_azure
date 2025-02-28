# Projeto ETL com Azure Databricks, Data Factory e integração com Github

## Visão Geral
Este projeto implementa uma solução completa de ETL utilizando serviços Azure para processar dados imobiliários em uma arquitetura medalhão, com integração contínua via GitHub.

## Arquitetura
![diagrama_projeto](https://github.com/user-attachments/assets/269f04e3-9277-492f-aa74-f54ca70c15ec)


### Componentes Principais:
- **Azure Data Lake Storage Gen2**: Armazenamento dos dados em camadas (landing, bronze, silver)
- **Azure Databricks**: Transformação dos dados utilizando PySpark
- **Azure Data Factory**: Orquestração dos pipelines e definição de gatilhos
- **GitHub**: Versionamento de código e integração contínua

### Fluxo de Dados
1. Ingestão de dados brutos (formato JSON) na camada **landing**
2. Transformação inicial e conversão para formato Delta na camada **bronze**
3. Transformações adicionais e conversão para Parquet na camada **silver**

## Estrutura do Data Lake
```
data-lake/
├── landing/    # Dados brutos em JSON
├── bronze/     # Dados convertidos em formato Delta
└── silver/     # Dados transformados em formato Parquet
```

## Configuração do Ambiente

### Pré-requisitos
- Conta Azure com acesso aos serviços:
  - Azure Databricks
  - Azure Data Factory
  - Azure Data Lake Storage Gen2
- Conta GitHub para integração e versionamento

### Passos para Configuração
1. Provisionamento dos recursos na Azure
2. Configuração das permissões e autenticação entre serviços, incluindo criação dos tokens necessários
3. Configuração da integração com GitHub
4. Implementação dos notebooks Databricks

## Notebooks Databricks
Os notebooks estão organizados da seguinte forma:

- `landing_to_bronze.ipynb`: Transformação de JSON para Delta
- `bronze_to_silver.ipynb`: Transformações adicionais e conversão para Parquet

## Pipelines do Azure Data Factory
Foi desenvolvido um pipeline para automatizar o fluxo de dados entre as camadas:

- Pipeline de Ingestão e processamento: Carrega dados na camada landing e orquestra a execução dos notebooks Databricks


### Gatilhos
- Gatilho programado: Execução agendada para cada hora, a partir da primeira execução.
- Gatilho por evento: Ativado quando novos arquivos são detectados

## Integração com GitHub
Todos os artefatos do projeto são versionados no GitHub:
- Notebooks Databricks
- Definições de pipeline do Data Factory
- Scripts de infraestrutura
- Documentação

## Como Executar o Projeto

### Execução Manual
1. Acesse o Azure Data Factory
2. Selecione o pipeline principal
3. Clique em "Executar"

### Depuração Local
1. Clone o repositório
2. Configure as credenciais locais
3. Execute os notebooks individualmente no Databricks

## Monitoramento e Troubleshooting

### Logs
- Logs de execução disponíveis no Azure Data Factory
- Logs detalhados dos notebooks Databricks e no Databricks workflows

### Alertas
- Configurados para falhas nos pipelines
- Monitoramento de performance e custos

## Próximos Passos
- Implementação de testes automatizados
- Criação da camada gold para dados agregados
- Dashboard de monitoramento em tempo real





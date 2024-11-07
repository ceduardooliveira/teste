
``` mermaid
sequenceDiagram
    participant Execucao as Script de Execução
    participant Banco as Banco de Dados (BigQuery)
    participant Log as Procedimento de Log

    Execucao->>Banco: Solicita Log do Processo Anterior
    Banco-->>Execucao: Retorna Log do Processo

    Execucao->>Banco: Calcula Contagem de Linhas Anterior<br/>da Tabela cobranca_assessoria

    Execucao->>Banco: Consulta Dados com UNNEST
    Banco-->>Execucao: Retorna Dados Consultados

    Execucao->>Banco: Insere Dados na Tabela cobranca_assessoria

    Execucao->>Banco: Calcula Contagem de Linhas Atual<br/>da Tabela cobranca_assessoria

    Execucao->>Banco: Calcula Última Data Processada<br/>com max(dat_referencia)

    Execucao->>Log: Grava Log do Processo Atual<br/>com Dados de Execução
    Log-->>Execucao: Log Gravado

    Execucao->>Execucao: Fim do Processo
``` 

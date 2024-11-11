
``` mermaid
sequenceDiagram
    participant A as Sistema ETL
    participant B as Banco de Dados
    participant C as Log de Processamento
    participant D as Tabela de Destino

    A->>C: Inicia execução do processo
    A->>B: Busca dados de transações, cotas, funcionários, clientes e estabelecimentos
    A->>D: Processa e insere os dados na tabela "termometro"
    A->>C: Finaliza o log e registra o sucesso



``` 

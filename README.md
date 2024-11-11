
``` mermaid
sequenceDiagram
    participant A as Sistema ETL
    participant B as Banco de Dados
    participant C as Log de Processamento
    participant D as Tabela Termômetro
    participant E as Parâmetros
    participant F as Transações
    participant G as Cotas
    participant H as Funcionários
    participant I as Clientes
    participant J as Estabelecimentos

    A->>C: Inicia execução do processo
    A->>B: Recupera dados de "etl_trans_adesao_flex_multiplo"
    A->>B: Recupera dados de "etl_transacao_pfin_ind_cartao"
    A->>B: Recupera dados de "v_cota_produto_financeiro"
    A->>B: Recupera dados de "produto_cartao"
    A->>B: Recupera dados de "produtos_financeiros"
    A->>B: Recupera dados de "funcionarios"
    A->>B: Recupera dados de "cliente"
    A->>B: Recupera dados de "estabelecimento"

    A->>E: Consulta parâmetros para 'cod_indicador = 5004'
    A->>F: Aplica joins com transações e cotas
    A->>G: Aplica joins com dados de cotas de venda
    A->>H: Aplica joins com dados de vendedores
    A->>I: Aplica joins com dados de clientes
    A->>J: Aplica joins com dados de estabelecimentos

    A->>D: Gera e insere dados na tabela "termometro"
    D->>B: Insere dados na tabela de destino "flex_multiplo"
    A->>C: Atualiza log de execução
    A->>B: Finaliza execução e coleta estatísticas
    A->>C: Finaliza log de processamento


``` 

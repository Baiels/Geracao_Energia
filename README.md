# Geracao_Energia
Criação e Gestão de um Banco de Dados de um Sistema de Gestão de Geração de Energia

estrutura.sql: Script responsável pela criação das tabelas, definição de restrições (chaves primárias, estrangeiras e constraints adicionais) e índices no banco de dados Oracle.
dados.sql: Script para inserção de dados representativos nas tabelas, garantindo que respeitem os relacionamentos e restrições definidas no modelo.

1. Criação do Banco de Dados (estrutura.sql)

Funcionalidades:
Cria o esquema e todas as tabelas necessárias.

Define as restrições, como:
Chaves primárias para identificação única de registros.
Chaves estrangeiras para garantir integridade referencial entre as tabelas.
Índices únicos para evitar duplicação de valores em campos específicos.
Implementa ações de exclusão em cascata (ON DELETE CASCADE) para manter a consistência do banco de dados.

Exemplo de criação de tabela:

CREATE TABLE GERACAO_ENERGIA.USINAS (
    USINA_ID NUMBER NOT NULL,
    NOME VARCHAR2(100) NOT NULL,
    TIPO VARCHAR2(50),
    CAPACIDADE_GERACAO NUMBER(10,2),
    LOCALIZACAO VARCHAR2(100),
    CONSTRAINT PK_USINAS PRIMARY KEY (USINA_ID)
);

Índices adicionais:
IDX_USINAS_NOME: Garante que o nome de cada usina seja único.
IDX_MEDIDORES_NUMERO_SERIE: Garante unicidade do número de série dos medidores.

2. Inserção de Dados Representativos (dados.sql)

Funcionalidades:
Popula as tabelas com dados fictícios que respeitam as regras de integridade e os relacionamentos.

Exemplos de dados inseridos:
USINAS:
INSERT INTO GERACAO_ENERGIA.USINAS (USINA_ID, NOME, TIPO, CAPACIDADE_GERACAO, LOCALIZACAO)
VALUES (1, 'Usina Solar Norte', 'Solar', 500.50, 'Fortaleza - CE');

LEITURAS_ENERGIA:
INSERT INTO GERACAO_ENERGIA.LEITURAS_ENERGIA (LEITURA_ID, MEDIDOR_ID, DATA_LEITURA, CONSUMO)
VALUES (1001, 101, TO_TIMESTAMP('2024-12-01 08:00:00', 'YYYY-MM-DD HH24:MI:SS'), 1

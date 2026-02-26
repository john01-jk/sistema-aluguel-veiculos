# sistema-aluguel-veiculos ## 📌 Apresentação do Projeto

Este projeto tem como objetivo desenvolver a estrutura inicial de um banco de dados relacional para um aplicativo de aluguel de carros voltado para motoristas de aplicativos.

O sistema será implementado utilizando PostgreSQL e tem como foco a organização das principais entidades e seus relacionamentos.
## 🚀 Versão Inicial

Estrutura atual do repositório:

aluguel-carros-app/
│
└── README.md
Versão atual: v0.1.0

Esta versão contém:
- Estrutura inicial do repositório
- Modelo conceitual do banco de dados
- Diagrama entidade-relacionamento em MERMAID

 ## 🗄 Modelo de Dados

```mermaid
erDiagram

    MOTORISTA {
        int id
        string nome
        string cpf
        date data_nascimento
        string cnh
        date validade_cnh
        string telefone
        string email
        string endereco
        string status
        datetime criado_em
    }

    VEICULO {
        int id
        string modelo
        string placa
        int ano
        string chassi
        string cor
        int categoria_id
        int status_id
        decimal valor_diaria
        int quilometragem
        datetime criado_em
    }

    ALUGUEL {
        int id
        int motorista_id
        int veiculo_id
        int funcionario_id
        date data_inicio
        date data_fim
        decimal valor_total
        string status
        int forma_pagamento_id
        datetime criado_em
    }

    PAGAMENTO {
        int id
        int aluguel_id
        decimal valor
        date data_pagamento
        string status
        string comprovante_url
    }

    MANUTENCAO {
        int id
        int veiculo_id
        string descricao
        date data_inicio
        date data_fim
        decimal custo
        string tipo
    }

    MULTA {
        int id
        int aluguel_id
        string descricao
        decimal valor
        date data_multa
        string status
    }

    CATEGORIA_VEICULO {
        int id
        string nome
        string descricao
    }

    STATUS_VEICULO {
        int id
        string nome
    }

    FORMA_PAGAMENTO {
        int id
        string nome
    }

    FUNCIONARIO {
        int id
        string nome
        string cargo
        string email
        string senha
        string nivel_acesso
    }

    MOTORISTA ||--o{ ALUGUEL : realiza
    VEICULO ||--o{ ALUGUEL : alugado_em
    VEICULO ||--o{ MANUTENCAO : possui
    ALUGUEL ||--o{ PAGAMENTO : gera
    ALUGUEL ||--o{ MULTA : pode_ter
    CATEGORIA_VEICULO ||--o{ VEICULO : classifica
    STATUS_VEICULO ||--o{ VEICULO : define
    FORMA_PAGAMENTO ||--o{ ALUGUEL : utiliza
    FUNCIONARIO ||--o{ ALUGUEL : registra

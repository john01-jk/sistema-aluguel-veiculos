# sistema-aluguel-veiculos ## 📌 Apresentação do Projeto

🚗 Aluguel de Carros para Motoristas de Aplicativo

Sistema de banco de dados relacional desenvolvido para gerenciar uma plataforma de aluguel de veículos voltada para motoristas de aplicativos.

O projeto tem como objetivo estruturar, modelar e organizar as entidades principais de um sistema real de locação, utilizando PostgreSQL como SGBD.

📌 Objetivo do Projeto

Desenvolver a base estrutural de um banco de dados que permita:

Cadastro e gerenciamento de motoristas

Controle completo de veículos

Gestão de aluguéis

Controle de pagamentos

Registro de multas e manutenções

Organização de funcionários do sistema

Este projeto representa a camada inicial de dados para um futuro aplicativo completo.

🛠 Tecnologias Utilizadas

🐘 PostgreSQL

🧩 Modelagem Relacional

📊 Diagrama ER com Mermaid

📂 Versionamento com Git

📦 Estrutura do Repositório
aluguel-carros-app/
│
├── README.md
└── database/
    └── modelo_er.mmd

📌 Versão atual: v0.1.0

🗄 Modelo de Dados

O banco de dados foi modelado utilizando boas práticas de normalização, garantindo:

Integridade referencial

Escalabilidade

Organização lógica das entidades

Preparação para futura implementação de API

📊 Diagrama Entidade-Relacionamento (ER)
🧠 Principais Entidades
👤 MOTORISTA

Armazena informações pessoais e documentação do motorista.

🚘 VEICULO

Contém dados técnicos e operacionais dos veículos disponíveis para aluguel.

📄 ALUGUEL

Registra as transações de locação entre motorista e veículo.

💳 PAGAMENTO

Controla os pagamentos vinculados a cada aluguel.

🔧 MANUTENCAO

Permite registrar custos e histórico de manutenção dos veículos.

📈 Próximas Implementações

 Scripts SQL completos (CREATE TABLE)

 Seeds para dados de teste

 Controle de autenticação de funcionários

 API REST integrada

 Sistema de versionamento do banco

 Deploy em ambiente cloud

🎯 Visão de Futuro

Este projeto poderá evoluir para:

Backend completo (Node.js / Java / Python)

Aplicativo mobile

Painel administrativo

Sistema SaaS para locadoras

📚 Status do Projeto

🚧 Em desenvolvimento — Fase inicial de modelagem de dados.
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
        int atendentes_id
        int clientes_id
        date data_inicio
        date data_fim
        decimal valor_total
        string status
        int forma_pagamento_id
        datetime criado_em
    }

    CONTRATOS {
        int id
        int aluguel_id
        int cliente_id
        int veiculos_id
        decimal valor
        date data_pagamento
        string status
        string comprovante_url

    }

PERIODO DE CONTRATO {
        int id
        date  data_contrato_inicial
        date  data_contrato_final
        string nome
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

    ATENDENTES{
        int id
        string nome
        string cpf
        string email
        string senha
        string nivel_acesso
    }
CLIENTES{
        int id
        string nome
        string cpf
        string email
       
    }

    MOTORISTA ||--o{ ALUGUEL : realiza
    VEICULO ||--o{ ALUGUEL : alugado_em
    VEICULO ||--o{ MANUTENCAO : possui
    ALUGUEL ||--o{ CONTRATOS : gera
    ALUGUEL ||--o{ MULTA : pode_ter
    CATEGORIA_VEICULO ||--o{ VEICULO : classifica
    STATUS_VEICULO ||--o{ VEICULO : define
    FORMA_PAGAMENTO ||--o{ CONTRATOS : gera
    ATENDENTES  ||--o{ ALUGUEL : registra
    CLIENTES  ||--o{ ALUGUEL : registra
    CONTRATOS  ||--o{ PERIODO DE CONTRATO : registra

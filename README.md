# sistema-aluguel-veiculos ## 📌 Apresentação do Projeto

Este projeto tem como objetivo desenvolver a estrutura inicial de um banco de dados relacional para um aplicativo de aluguel de carros voltado para motoristas de aplicativos.

O sistema será implementado utilizando PostgreSQL e tem como foco a organização das principais entidades e seus relacionamentos.
## 🚀 Versão Inicial

Estrutura inicial do projeto






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
        string telefone
    }

    VEICULO {
        int id
        string modelo
        string placa
        int ano
        string status
    }

    ALUGUEL {
        int id
        date data_inicio
        date data_fim
        int motorista_id
        int veiculo_id
    }

    MOTORISTA ||--o{ ALUGUEL : realiza
    VEICULO ||--o{ ALUGUEL : possui

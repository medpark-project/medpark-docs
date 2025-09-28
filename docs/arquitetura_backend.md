# Arquitetura do Backend - MedPark

A arquitetura do backend do MedPark segue um padrão de **separação de camadas (ou responsabilidades)**, inspirado em designs de software limpos e escaláveis. O objetivo é garantir que cada parte do código tenha um propósito bem definido, facilitando a manutenção, testabilidade e o crescimento do projeto.

## Estrutura de Pastas Principal

medpark-backend/
├── app/                  
│   ├── api/              # Camada de API (os "endpoints" ou rotas)
│   ├── core/             # Configurações do projeto
│   ├── crud/             # Lógica de acesso ao banco de dados (CRUD)
│   ├── db/               # Configuração da conexão com o banco de dados
│   ├── models/           # Modelos do banco de dados (SQLAlchemy)
│   └── schemas/          # Modelos de dados da API (Pydantic)
│   └── main.py           # Ponto de entrada da aplicação FastAPI
│
├── tests/                # Pasta para os testes automatizados
├── .gitignore
├── Dockerfile            # Receita para construir a imagem da aplicação
├── docker-compose.yml    # Orquestrador que sobe a aplicação e o banco
└── requirements.txt      # Lista de pacotes Python necessários


## Responsabilidade de Cada Camada

- **`app/main.py`** Inicia a aplicação e registra os diferentes routers de endpoints.

- **`app/api/`** Contém os endpoints. Eles recebem requisições HTTP, validam com schemas e chamam o CRUD.

- **`app/schemas/` - (Pydantic):** Define a estrutura e as regras dos dados que entram e saem da API. Garante que nenhum dado inválido seja processado.

- **`app/crud/`** Contém a lógica de negócio e de interação com o banco de dados. Sabe como criar, ler, atualizar e deletar registros.

- **`app/models/` - (SQLAlchemy):** Descreve a estrutura das tabelas no banco de dados.

- **`app/db/`** Gerencia a configuração e as sessões de conexão com o banco de dados.

## Histórico de Versões

<div align="center">
  <table class="md-table">
    <thead>
      <tr>
        <th align="left">Versão</th>
        <th align="left">Data</th>
        <th align="left">Autor(es)</th>
        <th align="left">Descrição das Alterações</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td align="left">1.0</td>
        <td align="left">28/09/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Criação do documento.</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 1: Histórico de versões do documento de arquitetura do backend.</p>
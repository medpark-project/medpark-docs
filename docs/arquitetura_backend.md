# Arquitetura do Backend - MedPark

A arquitetura do backend do MedPark foi refatorada para seguir um padrão de **Agrupamento por Funcionalidade** (também conhecido como "Feature-based" ou "Vertical Slices").

O objetivo desta arquitetura é promover alta coesão e baixo acoplamento, agrupando todos os arquivos relacionados a uma única entidade de negócio (como `Usuario` ou `TipoVeiculo`) em um mesmo módulo. Isso torna o projeto mais organizado, escalável e fácil de manter à medida que novas funcionalidades são adicionadas.

## Estrutura de Pastas Principal

A estrutura atual organiza o código dentro de um diretório `src/`, com submódulos para cada funcionalidade de negócio.

medpark-backend/

medpark-backend/

├── .github/              # Automação de CI/CD com GitHub Actions

├── src/                  # Diretório raiz do código-fonte da aplicação

│   ├── db/               # Configuração da conexão e dependências do banco

│   ├── plano_mensalista/   # Módulo da funcionalidade "Plano Mensalista"

│   ├── tipo_veiculo/     # Módulo da funcionalidade "Tipo de Veículo"

│   ├── usuario/          # Módulo da funcionalidade "Usuário"

│   ├── __init__.py       # Torna 'src' um pacote Python

│   ├── conftest.py       # Configuração central para os testes (Pytest)

│   └── main.py           # Ponto de entrada da aplicação FastAPI

│

├── .gitignore

├── Dockerfile

├── docker-compose.yml

└── requirements.txt

## Estrutura de um Módulo de Funcionalidade

Cada módulo de funcionalidade (ex: `src/tipo_veiculo/`) contém toda a lógica para aquela entidade, dividida em camadas:

└── tipo_veiculo/

├── __init__.py

├── model.py         # Camada de Dados: Modelo da tabela (SQLAlchemy)

├── schema.py        # Camada de Apresentação: Contratos da API (Pydantic)

├── repository.py    # Camada de Acesso a Dados: Funções CRUD (ex-crud)

├── router.py        # Camada de Apresentação: Endpoints da API (ex-api)

├── test_integracao.py # Teste de Integração para o router

└── test_unitario.py # Teste Unitário para o repository


## Responsabilidade de Cada Arquivo

- **`src/main.py`**: O ponto de entrada principal. É responsável por criar a aplicação FastAPI e incluir os `router.py` de cada módulo de funcionalidade.

- **`src/db/`**: Um módulo compartilhado que contém a lógica de conexão com o banco de dados (`session.py`) e a dependência `get_db` (`dependencies.py`) usada pelos routers.

- **Dentro de cada módulo (ex: `src/usuario/`)**:
    - **`model.py`**: Define a estrutura da tabela do banco de dados usando SQLAlchemy.
    - **`schema.py`**: Define os contratos de dados para a API usando Pydantic.
    - **`repository.py`**: Contém a lógica de negócio e as funções para interagir com o banco de dados (Create, Read, Update, Delete).
    - **`router.py`**: Define os endpoints da API (`@router.get`, `@router.post`, etc.). Ele recebe as requisições HTTP, usa os `schema.py` para validação e chama as funções do `repository.py`.
    - **`test_*.py`**: Arquivos de teste co-localizados, que validam o comportamento do módulo.

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
        <td align="left">Criação inicial do documento com arquitetura por camada.</td>
      </tr>
      <tr>
        <td align="left">2.0</td>
        <td align="left">03/10/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Refatoração completa para arquitetura por funcionalidade (feature-based), seguindo novas diretrizes.</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 1: Histórico de versões do documento de arquitetura do backend.</p>

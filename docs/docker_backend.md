# Ambiente de Desenvolvimento Backend com Docker

O ambiente de desenvolvimento do MedPark é totalmente containerizado usando Docker e Docker Compose. Isso garante um ambiente consistente, replicável e isolado, independentemente do sistema operacional do desenvolvedor.

## `Dockerfile`

Este arquivo é a base para construir a imagem da aplicação FastAPI. Seus principais passos são:
1.  **`FROM python:3.11-slim`**: Usa uma imagem oficial e leve do Python como base.
2.  **`RUN apt-get update ...`**: Aplica atualizações de segurança ao sistema operacional base.
3.  **`WORKDIR /code`**: Define o diretório de trabalho padrão dentro do contêiner.
4.  **`ENV PYTHONPATH=/code`**: Configura o caminho do Python para que as importações funcionem corretamente.
5.  **`COPY requirements.txt ...` e `RUN pip install ...`**: Copia e instala as dependências do Python.
6.  **`COPY ./app /code/app`**: Copia o código-fonte da aplicação para dentro do contêiner.
7.  **`CMD ["uvicorn", ...]`**: Define o comando padrão para iniciar o servidor da API quando o contêiner for executado.

## `docker-compose.yml`

Este arquivo orquestra os serviços, define e conecta dois contêineres:

### 1. Serviço `db` (Banco de Dados)
- **`image: postgres:15-alpine`**: Usa uma imagem oficial e leve do PostgreSQL.
- **`volumes`**: Mapeia uma pasta local (`./postgres_data`) para a pasta de dados do contêiner, garantindo que os dados do banco **persistam** mesmo que o contêiner seja recriado.
- **`environment`**: Configura o usuário, a senha e o nome do banco de dados que será criado automaticamente.
- **`ports: - "5432:5432"`**: Expõe a porta do PostgreSQL para a máquina local, permitindo a conexão com clientes de BD como o DBeaver.

### 2. Serviço `backend` (API)
- **`build: .`**: Instrui o Compose a construir a imagem usando o `Dockerfile` presente na pasta raiz.
- **`ports: - "8000:8000"`**: Expõe a porta da API para a máquina local.
- **`volumes: - ./app:/code/app`**: Cria uma sincronização em tempo real ("live sync") entre a pasta `app` local e a pasta correspondente no contêiner. Isso permite que alterações no código sejam refletidas instantaneamente sem a necessidade de reconstruir a imagem.
- **`environment`**: Passa a URL de conexão do banco de dados para a aplicação. Note que o host é `db`, o nome do serviço do banco de dados, pois os contêineres se enxergam por seus nomes de serviço na rede interna do Docker.
- **`depends_on: - db`**: Garante que o contêiner do banco de dados seja iniciado antes do contêiner do backend.

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

<p class="caption">Tabela 1: Histórico de versões do documento de Docker.</p>
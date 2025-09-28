# Testes Backend

Para garantir a qualidade e a confiabilidade da API do MedPark, utilizamos uma estratégia de testes de integração automatizados.

## Ferramentas

- **`Pytest`**: Framework principal para escrever e executar testes.
- **`HTTPX`**: Usado junto com o `TestClient` do FastAPI para fazer requisições HTTP reais à API durante os testes.

## Banco de Dados de Teste

A prática mais importante da estratégia é o **isolamento**. Os testes **NUNCA** são executados utilizando o banco de dados de desenvolvimento (`medpark_db`).

Utiliza-se um **banco de dados SQLite em memória** para cada sessão de teste. Isso é configurado no arquivo `tests/conftest.py`.

### Vantagens:
- **Velocidade:** Testes em memória são mais rápidos que testes que acessam um banco de dados via rede.
- **Isolamento Total:** Cada execução de teste começa com um banco de dados 100% novo e vazio. Ao final, ele é completamente destruído. Isso garante que os testes sejam independentes e seus resultados, consistentes.

## Como Executar os Testes

Existem duas maneiras de rodar a suíte de testes:

### 1. Automaticamente ao Iniciar
O arquivo `docker-compose.yml` está configurado para executar os testes antes de iniciar o servidor da API:

```yaml
command: sh -c "pytest && uvicorn app.main:app --host 0.0.0.0 --port 8000"
```

Se qualquer teste falhar, o && impede que a segunda parte (iniciar o servidor) seja executada, garantindo que a aplicação não suba com código quebrado.

### 2. Manualmente

Para rodar os testes a qualquer momento em um contêiner que já está em execução, use o seguinte comando no terminal:

```bash
docker compose exec backend pytest
```

Isso abrirá um terminal dentro do contêiner backend e executará o pytest nele.

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

<p class="caption">Tabela 1: Histórico de versões do documento de testes do backend.</p>
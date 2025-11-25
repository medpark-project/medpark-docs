# MedPark API - Backend

<div align="center">

![MedPark Logo](./assets/logo.png) 

</div>

## Introdução

Bem-vindo à documentação do **MedPark**, um sistema completo de gerenciamento de estacionamento hospitalar. 

O sistema foi projetado para gerenciar tanto o fluxo de veículos avulsos quanto a gestão completa de clientes mensalistas, desde a solicitação inicial até a assinatura de planos e o controle de pagamentos.

## Visão Geral das Funcionalidades

O MedPark oferece funcionalidades para suportar as operações do estacionamento, refletidas nas telas do protótipo do sistema.

### Gestão do Pátio
* **Registro de Entrada e Saída:** Endpoints para registrar a entrada de veículos (avulsos ou mensalistas) e processar a saída, calculando o valor a ser pago.
* **Visualização em Tempo Real:** Uma rota para listar todos os veículos que estão atualmente no pátio, permitindo o controle operacional.

### Gestão de Mensalistas
* **Fluxo de Onboarding Completo:**
    * **Solicitação:** Um endpoint público para que novos clientes possam solicitar um plano de mensalista, enviando seus dados e documentos.
    * **Aprovação:** Rotas protegidas para que operadores possam visualizar e aprovar ou recusar as solicitações pendentes.
    * **Criação Automática:** Ao aprovar uma solicitação, o sistema automaticamente cria o registro do `Mensalista`, do seu `Veiculo` e da sua `AssinaturaPlano`, integrando todos os módulos.
* **CRUD de Mensalistas:** Endpoints completos para criar (manualmente), ler, atualizar e deletar os dados dos clientes mensalistas.

### Finanças e Planos
* **Gestão de Planos e Tarifas:** CRUDs protegidos para que administradores possam gerenciar os planos de assinatura mensal e as tarifas por hora para cada tipo de veículo.
* **Gestão de Assinaturas:** Endpoints para criar e gerenciar os "contratos" que vinculam um mensalista a um plano.
* **Histórico de Pagamentos:** CRUD para gerenciar o histórico de "faturas" de cada assinatura, permitindo registrar pagamentos e consultar o histórico.

### Autenticação
* **Arquitetura Híbrida:** O sistema utiliza um repositório separado (`medpark-auth-api`) para a geração de tokens, enquanto a gestão de usuários (CRUD) e a validação de credenciais permanecem centralizadas no backend principal.
* **Controle de Acesso:** A maioria das rotas de gestão (qualquer operação que não seja de leitura pública) é protegida e exige um token de autenticação JWT válido.

## Arquitetura e Tecnologia

O projeto foi construído seguindo uma arquitetura modular e utilizando tecnologias modernas para garantir escalabilidade e manutenibilidade.

* **Linguagem:** Python 3.11
* **Framework:** FastAPI
* **Banco de Dados:** PostgreSQL, gerenciado via Docker.
* **ORM:** SQLAlchemy, com um padrão de `repository` para abstrair as interações com o banco.
* **Validação de Dados:** Pydantic, com validações customizadas para regras de negócio (ex: formato de CPF e placa).
* **Contêineres:** Docker e Docker Compose, garantindo um ambiente de desenvolvimento e produção consistente.

### Estrutura de Pastas
O código-fonte está organizado em uma arquitetura "por funcionalidade", onde cada entidade de negócio (ex: `usuario`, `veiculo`, `plano_mensalista`) possui sua própria pasta contendo `model.py`, `schema.py`, `repository.py`, `router.py` e seus próprios testes.

## Qualidade e CI/CD

A qualidade do código é garantida por uma suíte de automação completa:

* **Linting:** `Ruff` para garantir um padrão de código limpo e consistente.
* **Testes:** A suíte de testes inclui:
    * **Testes Unitários:** Para validar regras de negócio isoladas.
    * **Testes de Integração:** Para validar o fluxo completo de cada CRUD e endpoint da API.
    * **Testes Parametrizados:** Para testar múltiplos cenários de erro e validação de forma eficiente.
* **CI/CD com GitHub Actions:** Todo `push` para o branch `main` aciona um workflow que automaticamente executa o linter e a suíte de testes completa em um ambiente limpo, garantindo que nenhum código com falhas seja integrado ao projeto.

## Links do Projeto MedPark

Para acessar o site, [clique aqui](https://medpark-frontend.vercel.app/).

Para acessar o repositório do back-end, [clique aqui](https://github.com/medpark-project/medpark-backend/).

Para acessar o repositório do front-end, [clique aqui](https://github.com/medpark-project/medpark-frontend/).

Para acessar o repositório de autenticação, [clique aqui](https://github.com/medpark-project/medpark-auth-api/).

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
        <td align="left">28/10/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Criação do documento.</td>
      </tr>
      <tr>
        <td align="left">1.1</td>
        <td align="left">25/11/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Adiciona links do projeto.</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 1: Histórico de versões da página inicial.</p>

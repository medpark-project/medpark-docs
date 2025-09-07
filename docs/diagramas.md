# Diagramas UML

## Diagrama de Classes

```mermaid

classDiagram
    %% --- Definição de todas as Classes e seus Atributos ---
    class Usuario {
        +int id
        +string nome
        +string email
        +string senha_hash
        +Enum perfil
    }
    class Mensalista {
        +int id
        +string nome_completo
        +string email
        +string cpf
        +string rg
        +string telefone
        +string path_doc_pessoal
        +string path_doc_comprovante
    }
    class Veiculo {
        +string placa (PK)
        +string modelo
        +string cor
        +int mensalista_id (FK)
        +int tipo_veiculo_id (FK)
    }
    class TipoVeiculo {
        +int id (PK)
        +string nome
        +float tarifa_hora
    }
    class RegistroEstacionamento {
        +int id (PK)
        +datetime hora_entrada
        +datetime hora_saida
        +float valor_pago
        +string veiculo_placa (FK)
    }
    class PlanoMensalista {
        +int id (PK)
        +string nome
        +float preco_mensal
        +string descricao
    }
    class SolicitacaoMensalista {
        +int id (PK)
        +string nome_completo
        +string email
        +string cpf
        +string rg
        +string placa_veiculo
        +string path_doc_pessoal
        +string path_doc_comprovante
        +Enum status
        +int plano_id (FK)
    }
    class AssinaturaPlano {
        +int id (PK)
        +date data_inicio
        +date data_fim
        +Enum status
        +int mensalista_id (FK)
        +int plano_id (FK)
    }
    class PagamentoMensalidade {
        +int id (PK)
        +date data_pagamento
        +date data_vencimento
        +float valor_pago
        +int mes_referencia
        +Enum status
        +int assinatura_id (FK)
    }

    %% --- Definição de todos os Relacionamentos ---
    Mensalista "1" -- "1..*" Veiculo : possui
    Mensalista "1" -- "0..*" AssinaturaPlano : contrata

    Veiculo "1" -- "1" TipoVeiculo : é do tipo
    Veiculo "1" -- "0..*" RegistroEstacionamento : registra

    PlanoMensalista "1" -- "0..*" AssinaturaPlano : é o plano de
    PlanoMensalista "1" -- "0..*" SolicitacaoMensalista : é o plano solicitado em

    AssinaturaPlano "1" -- "0..*" PagamentoMensalidade : tem

```

<p class="caption">Diagrama 1: Diagrama de Classes.</p>

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
        <td align="left">07/09/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Criação do documento e inserção do Diagrama de Classes.</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 1: Histórico de versões do documento de escopo do projeto MedPark.</p>
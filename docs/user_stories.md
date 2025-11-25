# User Stories

## Usuários do Sistema (Atores)

O sistema foi desenhado para atender aos seguintes perfis de usuários:

- **Administrador:** Gerencia todo o sistema, incluindo tarifas, planos, usuários e relatórios.
- **Operador de Caixa/Pátio:** Realiza as operações do dia a dia, como registrar entrada e saída de veículos avulsos e processar pagamentos.
- **Mensalista (Funcionário do Hospital):** Usuário com plano fixo que necessita de acesso facilitado e gestão de sua mensalidade.
- **Usuário Avulso (Paciente/Visitante):** Ator externo que utiliza o estacionamento de forma esporádica e interage com o sistema através do Operador ou de um portal de autoatendimento.

## Backlog - Histórias de Usuário

### Administrador

- Como um administrador, eu quero acessar uma tela de "Planos e Tarifas" para cadastrar, editar e remover os diferentes planos de mensalistas e definir as tarifas por hora para cada tipo de veículo avulso, para que o sistema de cobrança esteja sempre atualizado com as regras de negócio.

- Como um administrador, eu quero acessar uma página de "Relatórios" com filtros de data, visualizando KPIs e gráficos sobre faturamento e ocupação, para que eu possa tomar decisões informadas sobre a saúde financeira e operacional do estacionamento.

- Como um administrador, eu quero ter a capacidade de supervisionar e, se necessário, intervir no processo de aprovação, recusa e cadastro de mensalistas, para que eu possa garantir a conformidade e corrigir possíveis erros da equipe de operação.

### Operador de Caixa

- Como um operador, eu quero registrar a entrada e saída de veículos avulsos no "Controle de Pátio", para que o faturamento seja feito de forma correta e eu tenha controle sobre a ocupação.

- Como um operador, eu quero, no momento da saída de um veículo avulso, processar o pagamento selecionando o método (Dinheiro, Cartão, Pix) e, no caso de Pix, exibir um QR Code para o cliente escanear, para que o checkout seja rápido e flexível.

- Como um operador, eu quero visualizar os detalhes das solicitações de mensalistas pendentes e ter a permissão para Aprová-las ou Recusá-las, para que eu possa agilizar o processo de novos cadastros.

- Como um operador, eu quero poder cadastrar um novo mensalista manualmente no sistema, preenchendo seus dados e anexando seus documentos, para que eu possa atender a um funcionário que venha ao guichê.

- Como um operador, ao visualizar os detalhes de um mensalista, eu quero poder acionar o envio do seu histórico de pagamentos para o seu e-mail cadastrado, para que eu possa atender às solicitações dos clientes de forma segura e eficiente.

### Mensalista (Funcionário)

- Como um funcionário do hospital, eu quero poder preencher um formulário de aplicação online, informando meus dados pessoais (incluindo CPF/RG), selecionando um plano e anexando meus documentos, para que minha solicitação para ser mensalista seja analisada.

- Como um mensalista, eu quero poder consultar o status da minha assinatura na página inicial do site informando minha placa e, se houver uma fatura em aberto, pagá-la online (via Pix ou Cartão), para que eu possa manter minha situação regularizada de forma autônoma.

- Como um mensalista, eu quero que minha entrada e saída do estacionamento sejam, idealmente, registradas automaticamente pela leitura da placa, para que minha experiência seja fluida e sem atritos.

### Usuário Avulso (Paciente/Visitante)

- Como um usuário avulso (paciente/visitante), eu quero poder ir até um guichê de pagamento, informar a placa do meu veículo ao operador e realizar o pagamento com cartão, dinheiro ou Pix, para que eu tenha um processo de pagamento assistido e seguro.

- Como um usuário avulso, eu quero acessar um site, digitar a placa do meu carro e efetuar o pagamento online, sendo apresentado a um modal interativo com opções de pagamento (PIX e Cartão) e seguindo o fluxo específico para cada um, para que o processo de autoatendimento seja completo e moderno.

- Como um usuário avulso (paciente/visitante), eu quero que, ao informar minha placa, seja no site ou para o operador, o sistema me mostre claramente o tempo de permanência e o valor exato a ser pago, para que eu tenha total transparência sobre a cobrança.

## Matriz de Responsabilidades

Esta tabela define as permissões e as responsabilidades primárias para cada perfil de usuário no sistema MedPark.

**Legenda:**

**Papel Primário**: Indica o perfil de usuário que é o principal responsável por executar a tarefa no cotidiano da operação.

**Também tem Permissão**: Indica um perfil que, embora não seja o principal executor, possui permissão para realizar a tarefa (geralmente em casos de supervisão, suporte ou exceção).


<div align="center">
  <table class="md-table">
    <thead>
      <tr>
        <th align="left">Funcionalidade</th>
        <th align="center">Papel Primário (Quem faz no dia a dia)</th>
        <th align="center">Também tem Permissão</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td align="left"><strong>Gerenciar Planos e Tarifas</strong></td>
        <td align="center">Administrador</td>
        <td align="center">-</td>
      </tr>
      <tr>
        <td align="left"><strong>Ver Relatórios Financeiros e Gráficos</strong></td>
        <td align="center">Administrador</td>
        <td align="center">Operador</td>
      </tr>
      <tr>
        <td align="left"><strong>Aprovar ou Recusar Solicitações</strong></td>
        <td align="center">Operador</td>
        <td align="center">Administrador</td>
      </tr>
      <tr>
        <td align="left"><strong>Cadastrar Mensalista Manualmente</strong></td>
        <td align="center">Administrador</td>
        <td align="center">-</td>
      </tr>
      <tr>
        <td align="left"><strong>Operar o Pátio (Entrada/Saída de Avulsos)</strong></td>
        <td align="center">Operador</td>
        <td align="center">Administrador</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 1: Matriz de responsabilidades.</p>


## Planejado vs. Implementado

Devido a restrições de prazo e decisões de arquitetura, algumas funcionalidades foram ajustadas.

### Administrador

- "Como um administrador, eu quero acessar uma tela de "Planos e Tarifas" para cadastrar, editar e remover os diferentes planos de mensalistas e definir as tarifas por hora para cada tipo de veículo avulso, para que o sistema de cobrança esteja sempre atualizado com as regras de negócio." 

*Modificações*: Não foi possível implementar em tempo hábil a criação das tarifas no front-end. Apesar de ser possível pelo back-end, foi atribuído por default o id 1 (Carro) para todos os veículos cadastrados no sistema.


- "Como um administrador, eu quero acessar uma página de "Relatórios" com filtros de data, visualizando KPIs e gráficos sobre faturamento e ocupação, para que eu possa tomar decisões informadas sobre a saúde financeira e operacional do estacionamento."

*Modificações*: Não foi possível implementar em tempo hábil um filtro manipulável pelo usuário. Os dados mostrados nos gráficos são diários, dos últimos 7 dias ou dos últimos 30 dias. Além disso, as páginas de Dashboard e Reports foram condensadas em uma página só para centralizar a visualização de dados estacionamento.


- "Como um administrador, eu quero ter a capacidade de supervisionar e, se necessário, intervir no processo de aprovação, recusa e cadastro de mensalistas, para que eu possa garantir a conformidade e corrigir possíveis erros da equipe de operação."

*Modificações*: Implementado sem modificações.


### Operador de Caixa

- "Como um operador, eu quero registrar a entrada e saída de veículos avulsos no "Controle de Pátio", para que o faturamento seja feito de forma correta e eu tenha controle sobre a ocupação."

*Modificações*: Implementado sem modificações.


- "Como um operador, eu quero, no momento da saída de um veículo avulso, processar o pagamento selecionando o método (Dinheiro, Cartão, Pix) e, no caso de Pix, exibir um QR Code para o cliente escanear, para que o checkout seja rápido e flexível."

*Modificações*: Implementado sem modificações.


- "Como um operador, eu quero visualizar os detalhes das solicitações de mensalistas pendentes e ter a permissão para Aprová-las ou Recusá-las, para que eu possa agilizar o processo de novos cadastros."

*Modificações*: Implementado sem modificações.


- "Como um operador, eu quero poder cadastrar um novo mensalista manualmente no sistema, preenchendo seus dados e anexando seus documentos, para que eu possa atender a um funcionário que venha ao guichê."

*Modificações*: Foi implementado, no entanto, o operador não tem permissão para realizar essa operação, só o administrador.


- "Como um operador, ao visualizar os detalhes de um mensalista, eu quero poder acionar o envio do seu histórico de pagamentos para o seu e-mail cadastrado, para que eu possa atender às solicitações dos clientes de forma segura e eficiente."

*Modificações*: Não foi possível implementar em tempo hábil o envio de histório de pagamentos por email. A função foi removida do deploy.


### Mensalista (Funcionário)

- "Como um funcionário do hospital, eu quero poder preencher um formulário de aplicação online, informando meus dados pessoais (incluindo CPF/RG), selecionando um plano e anexando meus documentos, para que minha solicitação para ser mensalista seja analisada."

*Modificações*: O envio de documentos foi removido.


- "Como um mensalista, eu quero poder consultar o status da minha assinatura na página inicial do site informando minha placa e, se houver uma fatura em aberto, pagá-la online (via Pix ou Cartão), para que eu possa manter minha situação regularizada de forma autônoma."

*Modificações*: Implementado sem modificações.


- "Como um mensalista, eu quero que minha entrada e saída do estacionamento sejam, idealmente, registradas automaticamente pela leitura da placa, para que minha experiência seja fluida e sem atritos."

*Modificações*: Implementado sem modificações. O mensalista não é cobrado na saída.


### Usuário Avulso (Paciente/Visitante)

- "Como um usuário avulso (paciente/visitante), eu quero poder ir até um guichê de pagamento, informar a placa do meu veículo ao operador e realizar o pagamento com cartão, dinheiro ou Pix, para que eu tenha um processo de pagamento assistido e seguro."

*Modificações*: Implementado sem modificações.


- "Como um usuário avulso, eu quero acessar um site, digitar a placa do meu carro e efetuar o pagamento online, sendo apresentado a um modal interativo com opções de pagamento (PIX e Cartão) e seguindo o fluxo específico para cada um, para que o processo de autoatendimento seja completo e moderno."

*Modificações*: Implementado sem modificações.

- "Como um usuário avulso (paciente/visitante), eu quero que, ao informar minha placa, seja no site ou para o operador, o sistema me mostre claramente o tempo de permanência e o valor exato a ser pago, para que eu tenha total transparência sobre a cobrança."

*Modificações*: Implementado sem modificações.


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
        <td align="left">04/09/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Criação do documento.</td>
      </tr>
      <tr>
        <td align="left">1.1</td>
        <td align="left">07/09/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Atualiza histórias de usuário conforme novas regras de negócio.</td>
      </tr>
      <tr>
        <td align="left">1.2</td>
        <td align="left">25/11/2025</td>
        <td align="left">Brunna Louise</td>
        <td align="left">Adiciona a seção de Planejado vs. Implementado e atualiza a matriz de responsabilidades, refletindo a atual regra de negócio do sistema.</td>
      </tr>
    </tbody>
  </table>
</div>

<p class="caption">Tabela 2: Histórico de versões do documento de escopo do projeto MedPark.</p>

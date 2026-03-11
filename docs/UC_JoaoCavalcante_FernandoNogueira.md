# Documentação de Casos de Uso – FitPass Gym Management

Este documento detalha os 20 casos de uso do sistema FitPass, conforme os requisitos funcionais, não funcionais e regras de negócio estabelecidos.

### UC01 — Cadastrar Aluno

* **Ator Principal:** Recepcionista
* **Objetivo:** Registrar um novo aluno no sistema.
* **Pré-condições:** Recepcionista autenticado.
* **Pós-condições:** Aluno cadastrado e apto a contratar planos.
* **Fluxo Principal:**
1. O recepcionista acessa o menu de cadastro de alunos.
2. O sistema exibe o formulário de dados (nome, CPF, endereço, contato).
3. O recepcionista preenche as informações.
4. O sistema valida os dados e a unicidade do CPF.
5. O sistema confirma a criação do perfil do aluno.


* **Fluxos Alternativos:**
* **A1 — Dados Inválidos:** O sistema sinaliza campos obrigatórios vazios ou CPF inválido e solicita correção.


* **RF Relacionados:** RF01
* **RNF Relacionados:** RNF02, RNF04
* **RN Relacionadas:** RN06

---

### UC02 — Gerenciar Tipos de Planos

* **Ator Principal:** Gerente
* **Objetivo:** Criar, editar ou desativar os planos oferecidos pela academia.
* **Pré-condições:** Gerente autenticado.
* **Pós-condições:** Tabela de planos atualizada para novas matrículas.
* **Fluxo Principal:**
1. O gerente acessa a área de configuração de planos.
2. O gerente define o nome do plano (ex: Musculação), valor, periodicidade e status.
3. O sistema salva as configurações.


* **Fluxos Alternativos:**
* **A1 — Desativar Plano:** O gerente desativa um plano; o sistema impede novas matrículas nele.


* **RF Relacionados:** RF02
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN06

---

### UC03 — Registrar Pagamento de Mensalidade

* **Ator Principal:** Recepcionista
* **Objetivo:** Quitar débitos financeiros do aluno na recepção.
* **Pré-condições:** Aluno possuir uma conta/plano ativo.
* **Pós-condições:** Mensalidade baixada e acesso liberado.
* **Fluxo Principal:**
1. O recepcionista localiza o cadastro do aluno.
2. O recepcionista seleciona a parcela em aberto.
3. O recepcionista escolhe a forma de pagamento (Dinheiro, Cartão ou PIX).
4. O sistema processa o pagamento e emite recibo.


* **Fluxos Alternativos:**
* **A1 — Pagamento Parcial:** O sistema bloqueia a operação informando que o valor deve ser integral (RN04).


* **RF Relacionados:** RF03, RF04
* **RNF Relacionados:** RNF02
* **RN Relacionadas:** RN04, RN07

---

### UC04 — Validar Acesso via RFID (Catraca)

* **Ator Principal:** Sistema de Catraca (API)
* **Objetivo:** Autorizar a entrada física do aluno na academia.
* **Pré-condições:** Aluno possuir tag RFID cadastrada.
* **Pós-condições:** Giro da catraca liberado e registro de log de acesso.
* **Fluxo Principal:**
1. O aluno aproxima a tag do leitor da catraca.
2. O Sistema de Catraca envia o ID via API JSON para o software central.
3. O sistema verifica se a mensalidade está em dia ou com atraso menor que 5 dias.
4. O sistema retorna o comando de liberação para a catraca.


* **Fluxos Alternativos:**
* **A1 — Bloqueio por Inadimplência:** Se o atraso for superior a 5 dias, o acesso é negado (RN01).


* **RF Relacionados:** RF04, RF05
* **RNF Relacionados:** RNF03, RNF06
* **RN Relacionadas:** RN01

---

### UC05 — Agendar Aula Coletiva

* **Ator Principal:** Aluno
* **Objetivo:** Reservar vaga em aulas de horário marcado.
* **Pré-condições:** Aluno regular e ativo.
* **Pós-condições:** Reserva confirmada no sistema.
* **Fluxo Principal:**
1. O aluno acessa a grade de horários pelo aplicativo mobile.
2. O aluno seleciona a aula desejada e clica em "Agendar".
3. O sistema verifica se há vagas disponíveis (RN02).
4. O sistema confirma a reserva e envia notificação.


* **Fluxos Alternativos:**
* **A1 — Aula Lotada:** O sistema informa que o limite foi atingido e bloqueia a reserva.


* **RF Relacionados:** RF06, RF10
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN02

---

### UC06 — Cancelar Reserva de Aula

* **Ator Principal:** Aluno
* **Objetivo:** Desistir de uma vaga previamente reservada.
* **Pré-condições:** Aluno possuir reserva ativa.
* **Pós-condições:** Vaga liberada na grade de aulas.
* **Fluxo Principal:**
1. O aluno acessa seus agendamentos no sistema.
2. O aluno solicita o cancelamento da aula.
3. O sistema valida se o pedido ocorre com mais de 1 hora de antecedência.
4. O sistema confirma o cancelamento.


* **Fluxos Alternativos:**
* **A1 — Fora do Prazo:** O sistema impede o cancelamento se faltar menos de 1 hora (RN03).


* **RF Relacionados:** RF06
* **RNF Relacionados:** RNF04
* **RN Relacionadas:** RN03

---

### UC07 — Registrar Presença em Aula

* **Ator Principal:** Instrutor
* **Objetivo:** Confirmar a presença dos alunos agendados.
* **Pré-condições:** Instrutor autenticado; aula em horário de realização.
* **Pós-condições:** Lista de frequência atualizada.
* **Fluxo Principal:**
1. O instrutor abre a lista de alunos agendados para a aula atual.
2. O instrutor marca o check-in dos alunos que compareceram.
3. O sistema salva a lista de presença para fins de relatório.


* **RF Relacionados:** RF07
* **RN Relacionadas:** RN06

---

### UC08 — Realizar Avaliação Física

* **Ator Principal:** Instrutor
* **Objetivo:** Cadastrar medidas e dados biométricos do aluno.
* **Pré-condições:** Aluno regular e ativo (RN05).
* **Pós-condições:** Dados da avaliação salvos no perfil do aluno.
* **Fluxo Principal:**
1. O instrutor inicia o módulo de avaliação física.
2. O instrutor insere peso, altura, IMC e percentual de gordura.
3. O sistema valida se o aluno está apto para a avaliação.
4. O sistema salva os dados e gera o resultado.


* **Fluxos Alternativos:**
* **A1 — Aluno Inativo/Irregular:** O sistema impede a gravação conforme RN05.


* **RF Relacionados:** RF08
* **RNF Relacionados:** RNF02
* **RN Relacionadas:** RN05, RN06

---

### UC09 — Emitir Relatório de Inadimplência

* **Ator Principal:** Gerente
* **Objetivo:** Listar alunos com pagamentos em atraso.
* **Pré-condições:** Gerente autenticado.
* **Pós-condições:** Relatório consolidado gerado na tela.
* **Fluxo Principal:**
1. O gerente seleciona o relatório de inadimplência no painel.
2. O sistema filtra os alunos com mensalidades vencidas.
3. O sistema exibe nome, telefone e dias de atraso.


* **RF Relacionados:** RF09
* **RN Relacionadas:** RN06

---

### UC10 — Enviar Notificação de Vencimento

* **Ator Principal:** Sistema
* **Objetivo:** Alertar o aluno sobre o prazo de pagamento da mensalidade.
* **Pré-condições:** Data de vencimento se aproximando.
* **Pós-condições:** Notificação enviada ao dispositivo do aluno.
* **Fluxo Principal:**
1. O sistema verifica as faturas que vencem em 3 dias.
2. O sistema dispara automaticamente uma notificação push.


* **RF Relacionados:** RF10
* **RNF Relacionados:** RNF05

---

### UC11 — Editar Cadastro de Aluno

* **Ator Principal:** Recepcionista
* **Objetivo:** Atualizar informações de endereço ou contato do aluno.
* **Fluxo Principal:**
1. O recepcionista busca o aluno pelo CPF.
2. O sistema exibe os dados atuais.
3. O recepcionista altera os campos e salva.


* **RF Relacionados:** RF01

---

### UC12 — Gerar Boleto para Pagamento Online

* **Ator Principal:** Aluno
* **Objetivo:** Emitir cobrança para pagamento via internet.
* **Fluxo Principal:**
1. O aluno acessa o módulo financeiro no aplicativo.
2. O aluno seleciona a mensalidade vigente.
3. O sistema gera o boleto ou chave PIX.


* **RF Relacionados:** RF03

---

### UC13 — Consultar Histórico de Acessos

* **Ator Principal:** Gerente
* **Objetivo:** Monitorar o fluxo de alunos na unidade.
* **Fluxo Principal:**
1. O gerente filtra o relatório por data e horário.
2. O sistema lista os logs gerados pela catraca.


* **RF Relacionados:** RF09

---

### UC14 — Visualizar Resultados de Avaliação Física

* **Ator Principal:** Aluno
* **Objetivo:** Acompanhar o progresso físico através do aplicativo.
* **Fluxo Principal:**
1. O aluno acessa a aba "Avaliações".
2. O sistema exibe os dados cadastrados pelo instrutor e arquivos anexos.


* **RF Relacionados:** RF08, RF10

---

### UC15 — Emitir Relatório de Ocupação de Aulas

* **Ator Principal:** Gerente
* **Objetivo:** Analisar a lotação das turmas.
* **Fluxo Principal:**
1. O gerente solicita o relatório de ocupação.
2. O sistema compara as vagas totais (RN02) com os agendamentos realizados.


* **RF Relacionados:** RF09

---

### UC16 — Anexar Exames à Avaliação

* **Ator Principal:** Instrutor
* **Objetivo:** Salvar arquivos externos no prontuário do aluno.
* **Fluxo Principal:**
1. Durante a avaliação física, o instrutor seleciona "Anexar Arquivo".
2. O sistema faz o upload e vincula o arquivo à avaliação.


* **RF Relacionados:** RF08
* **RNF Relacionados:** RNF02

---

### UC17 — Notificar Confirmação de Agendamento

* **Ator Principal:** Sistema
* **Objetivo:** Confirmar a vaga do aluno via push/e-mail.
* **Fluxo Principal:**
1. Após o sucesso do UC05, o sistema envia mensagem automática de confirmação.


* **RF Relacionados:** RF10

---

### UC18 — Consultar Lista de Alunos Ativos

* **Ator Principal:** Gerente
* **Objetivo:** Visualizar o total de matrículas vigentes.
* **Fluxo Principal:**
1. O gerente solicita o relatório de alunos ativos.
2. O sistema extrai a lista de alunos com contratos não expirados.


* **RF Relacionados:** RF09

---

### UC19 — Matricular Aluno em Plano

* **Ator Principal:** Recepcionista
* **Objetivo:** Vincular um aluno a um plano de pagamento específico.
* **Fluxo Principal:**
1. O recepcionista seleciona o aluno e o plano escolhido.
2. O sistema gera as faturas recorrentes e libera o acesso.


* **RF Relacionados:** RF01, RF02

---

### UC20 — Atualização Automática de Regularidade

* **Ator Principal:** Sistema
* **Objetivo:** Sincronizar o status de acesso imediatamente após o pagamento.
* **Fluxo Principal:**
1. O sistema detecta o pagamento via PIX/Cartão.
2. O sistema altera o status do aluno para "Regular" instantaneamente (RN07).


* **RF Relacionados:** RF04
* **RN Relacionadas:** RN07


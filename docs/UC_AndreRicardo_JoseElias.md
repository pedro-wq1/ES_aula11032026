
## UC01 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário acesse o sistema com suas credenciais.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso e usuário redirecionado para a área correspondente ao seu perfil.

### Fluxo Principal
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais.
4. O sistema autentica o usuário e redireciona para a tela inicial do seu perfil.

### Fluxos Alternativos
- **A1 — Credenciais inválidas:**  
  O sistema exibe mensagem de erro informando que e-mail ou senha estão incorretos.

- **A2 — Conta inativa/bloqueada:**  
  O sistema impede o login e exibe mensagem orientando o usuário a contatar a recepção.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema com todos os dados necessários para matrícula.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O aluno não deve possuir cadastro anterior ativo.

### Pós-condições
- Aluno cadastrado com sucesso e vinculado a um plano.
- Cartão/tag RFID associado ao aluno para controle de acesso.

### Fluxo Principal
1. A recepcionista acessa o módulo de cadastro de alunos.
2. A recepcionista preenche os dados pessoais do aluno (nome, CPF, data de nascimento, contato, endereço).
3. A recepcionista seleciona o plano contratado.
4. O sistema valida os dados informados.
5. O sistema registra o aluno e associa o RFID ao cadastro.
6. O sistema exibe confirmação do cadastro realizado.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:**  
  O sistema alerta que o CPF já possui cadastro e impede duplicidade.

- **A2 — Dados obrigatórios não preenchidos:**  
  O sistema destaca os campos faltantes e solicita correção antes de prosseguir.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC03 — Editar Dados do Aluno

### Ator Principal
Recepcionista

### Objetivo
Atualizar os dados cadastrais de um aluno já registrado no sistema.

### Pré-condições
- Recepcionista deve estar autenticada.
- O aluno deve possuir cadastro ativo no sistema.

### Pós-condições
- Dados do aluno atualizados com sucesso no sistema.

### Fluxo Principal
1. A recepcionista acessa o módulo de alunos e pesquisa pelo aluno desejado.
2. O sistema exibe os dados cadastrais do aluno.
3. A recepcionista altera os campos desejados.
4. O sistema valida os novos dados.
5. O sistema salva as alterações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**  
  O sistema informa que nenhum cadastro foi localizado com os dados de pesquisa informados.

- **A2 — Dados inválidos:**  
  O sistema destaca os campos com erros e solicita correção.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC04 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar, ativar e desativar planos disponíveis na academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Plano criado, editado, ativado ou desativado conforme a ação realizada.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente opta por criar um novo plano ou seleciona um plano existente para edição.
3. O gerente preenche ou altera as informações: nome, tipo, duração, valor e modalidades inclusas.
4. O sistema valida os dados informados.
5. O sistema salva as configurações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Desativar plano com alunos ativos:**  
  O sistema alerta que existem alunos vinculados ao plano e solicita confirmação antes de desativá-lo.

- **A2 — Dados obrigatórios não preenchidos:**  
  O sistema destaca os campos faltantes e impede o salvamento.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC05 — Registrar Pagamento

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade de um aluno, atualizando sua situação de regularidade.

### Pré-condições
- Recepcionista deve estar autenticada.
- O aluno deve possuir cadastro ativo no sistema.

### Pós-condições
- Pagamento registrado com sucesso.
- Situação do aluno atualizada para regular.

### Fluxo Principal
1. A recepcionista acessa o módulo de pagamentos e pesquisa o aluno.
2. O sistema exibe a situação financeira atual do aluno.
3. A recepcionista seleciona a forma de pagamento (dinheiro, cartão ou PIX).
4. A recepcionista confirma o valor integral da mensalidade.
5. O sistema registra o pagamento e atualiza imediatamente a regularidade do aluno.
6. O sistema exibe confirmação e emite comprovante.

### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:**  
  O sistema bloqueia a operação e informa que somente pagamento integral é aceito.

- **A2 — Falha na operação de cartão:**  
  O sistema informa o erro e orienta a recepcionista a tentar novamente ou usar outra forma de pagamento.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade

---

## UC06 — Verificar Regularidade do Aluno

### Ator Principal
Sistema (automático)

### Objetivo
Verificar automaticamente se o aluno está com a mensalidade em dia e bloquear o acesso caso esteja inadimplente.

### Pré-condições
- O aluno deve possuir cadastro ativo no sistema.

### Pós-condições
- Situação do aluno atualizada para inadimplente, se aplicável.
- Acesso bloqueado para alunos inadimplentes há mais de 5 dias.

### Fluxo Principal
1. O sistema verifica diariamente a data de vencimento das mensalidades.
2. O sistema identifica alunos com mensalidade vencida há mais de 5 dias.
3. O sistema bloqueia o acesso desses alunos.
4. O sistema registra o status de inadimplência no cadastro do aluno.
5. O sistema envia notificação ao aluno informando sobre o bloqueio.

### Fluxos Alternativos
- **A1 — Pagamento realizado após bloqueio:**  
  Ao registrar o pagamento, o sistema reativa o acesso imediatamente conforme RN07.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC07 — Validar Acesso pela Catraca

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Validar a entrada do aluno na academia por meio de leitura RFID na catraca.

### Pré-condições
- Aluno deve possuir cadastro ativo e RFID registrado.
- A integração com a API da catraca deve estar ativa.

### Pós-condições
- Acesso liberado e entrada registrada no histórico do aluno (se regular).
- Acesso negado e tentativa registrada (se inadimplente ou inativo).

### Fluxo Principal
1. O aluno aproxima o cartão/tag RFID da catraca.
2. A catraca envia o ID do RFID ao sistema via API REST.
3. O sistema consulta o cadastro do aluno pelo RFID recebido.
4. O sistema verifica se o aluno está regular e ativo.
5. O sistema retorna resposta de liberação à catraca.
6. A catraca libera a passagem e o sistema registra o acesso.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**  
  O sistema retorna negativa à catraca e a passagem é bloqueada.

- **A2 — RFID não encontrado:**  
  O sistema retorna erro à catraca; recepcionista deve verificar o cadastro.

- **A3 — Falha na comunicação com a API:**  
  O sistema registra o erro; a catraca pode operar em modo local (offline) temporariamente.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance
- RNF06 — Integração

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

---

## UC08 — Visualizar Horários de Aulas

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize os horários e modalidades das aulas disponíveis.

### Pré-condições
- Aluno deve estar autenticado no sistema.

### Pós-condições
- Aluno visualiza a grade de horários atualizada.

### Fluxo Principal
1. O aluno acessa o módulo de aulas.
2. O sistema exibe a grade de horários com modalidades, instrutores, horários e vagas disponíveis.
3. O aluno filtra as aulas por modalidade, dia ou horário, se desejar.
4. O sistema atualiza a exibição conforme os filtros aplicados.

### Fluxos Alternativos
- **A1 — Nenhuma aula disponível:**  
  O sistema exibe mensagem informando que não há aulas cadastradas para o filtro selecionado.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas

---

## UC09 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Reservar uma vaga em uma aula disponível na academia.

### Pré-condições
- Aluno deve estar autenticado e com situação regular.
- A aula deve possuir vagas disponíveis.

### Pós-condições
- Reserva registrada com sucesso.
- Vaga descontada do total disponível na aula.
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno acessa o módulo de aulas e visualiza os horários disponíveis.
2. O aluno seleciona a aula desejada.
3. O sistema verifica a disponibilidade de vagas.
4. O aluno confirma o agendamento.
5. O sistema registra a reserva e reduz o número de vagas disponíveis.
6. O sistema envia notificação de confirmação ao aluno.

### Fluxos Alternativos
- **A1 — Aula sem vagas:**  
  O sistema informa que a aula está lotada e impede o agendamento.

- **A2 — Aluno inadimplente:**  
  O sistema bloqueia o agendamento e orienta o aluno a regularizar sua situação.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN02 — Limite de vagas

---

## UC10 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Cancelar uma reserva previamente realizada em uma aula.

### Pré-condições
- Aluno deve estar autenticado.
- O aluno deve possuir uma reserva ativa para a aula.
- O cancelamento deve ser solicitado com pelo menos 1 hora de antecedência.

### Pós-condições
- Reserva cancelada e vaga devolvida ao total disponível.

### Fluxo Principal
1. O aluno acessa o módulo de agendamentos e visualiza suas reservas ativas.
2. O aluno seleciona a reserva que deseja cancelar.
3. O sistema verifica se o cancelamento está dentro do prazo permitido (mais de 1 hora antes da aula).
4. O aluno confirma o cancelamento.
5. O sistema cancela a reserva e devolve a vaga à aula.
6. O sistema exibe confirmação do cancelamento.

### Fluxos Alternativos
- **A1 — Cancelamento fora do prazo:**  
  O sistema informa que o prazo para cancelamento já expirou (menos de 1 hora antes da aula) e impede a operação.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN03 — Cancelamento de agendamento

---

## UC11 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar a presença dos alunos em uma aula ministrada.

### Pré-condições
- Instrutor deve estar autenticado no sistema.
- A aula deve estar em andamento ou recém-finalizada.

### Pós-condições
- Presença dos alunos registrada no sistema para a aula selecionada.

### Fluxo Principal
1. O instrutor acessa o módulo de aulas e seleciona a aula em andamento.
2. O sistema exibe a lista dos alunos com reserva na aula.
3. O instrutor marca os alunos presentes.
4. O instrutor confirma o registro de presença.
5. O sistema salva as presenças e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno presente sem agendamento:**  
  O instrutor pode registrar a presença avulsa, e o sistema vincula ao histórico do aluno.

- **A2 — Aula não encontrada:**  
  O sistema informa que nenhuma aula foi localizada para o período selecionado.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC12 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar os dados da avaliação física de um aluno ativo e regular.

### Pré-condições
- Instrutor deve estar autenticado.
- O aluno deve estar ativo e regular (sem inadimplência).

### Pós-condições
- Avaliação física registrada no histórico do aluno.
- Notificação enviada ao aluno informando a disponibilidade da nova avaliação.

### Fluxo Principal
1. O instrutor acessa o módulo de avaliações e pesquisa o aluno.
2. O sistema verifica se o aluno está ativo e regular.
3. O instrutor preenche os dados da avaliação: peso, altura, IMC, percentual de gordura e observações.
4. O instrutor anexa arquivos complementares, se necessário.
5. O sistema salva a avaliação e exibe confirmação.
6. O sistema envia notificação ao aluno informando a disponibilidade da nova avaliação.

### Fluxos Alternativos
- **A1 — Aluno inadimplente ou inativo:**  
  O sistema impede o registro e informa que a avaliação só pode ser realizada com alunos regulares.

- **A2 — Dados obrigatórios ausentes:**  
  O sistema destaca os campos faltantes e impede o salvamento.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física
- RN06 — Acesso restrito por perfil

---

## UC13 — Visualizar Histórico de Avaliações Físicas

### Ator Principal
Aluno

### Objetivo
Consultar o histórico de avaliações físicas registradas ao longo do tempo.

### Pré-condições
- Aluno deve estar autenticado.
- Deve existir ao menos uma avaliação física registrada para o aluno.

### Pós-condições
- Aluno visualiza seu histórico de avaliações com evolução dos indicadores.

### Fluxo Principal
1. O aluno acessa o módulo de avaliações físicas.
2. O sistema exibe a lista de avaliações realizadas em ordem cronológica.
3. O aluno seleciona uma avaliação para visualizar os detalhes.
4. O sistema exibe os dados completos da avaliação selecionada.

### Fluxos Alternativos
- **A1 — Nenhuma avaliação registrada:**  
  O sistema exibe mensagem informando que ainda não há avaliações no histórico.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física

---

## UC14 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a lista de alunos inadimplentes para controle financeiro da academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de inadimplência gerado e disponível para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de inadimplência.
3. O gerente aplica filtros opcionais (período, unidade, plano).
4. O sistema processa os dados e exibe o relatório com nome do aluno, plano, valor devido e dias em atraso.
5. O gerente pode exportar o relatório em PDF ou planilha.

### Fluxos Alternativos
- **A1 — Nenhum aluno inadimplente:**  
  O sistema exibe mensagem informando que não há inadimplências no período selecionado.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN06 — Acesso restrito por perfil

---

## UC15 — Emitir Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a listagem de todos os alunos ativos na academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de alunos ativos gerado e disponível para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de alunos ativos.
3. O gerente aplica filtros opcionais (plano, modalidade, período de matrícula).
4. O sistema processa os dados e exibe o relatório com nome, plano, data de matrícula e situação.
5. O gerente pode exportar o relatório em PDF ou planilha.

### Fluxos Alternativos
- **A1 — Nenhum aluno ativo no filtro:**  
  O sistema informa que não há alunos ativos para os critérios selecionados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC16 — Emitir Relatório de Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Gerar relatório com o histórico de entradas dos alunos na academia via catraca.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de histórico de acessos gerado e disponível para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de histórico de acessos.
3. O gerente define o período desejado e aplica filtros opcionais (aluno específico ou unidade).
4. O sistema processa os registros de acesso e exibe o relatório com data, hora e nome do aluno.
5. O gerente pode exportar o relatório em PDF ou planilha.

### Fluxos Alternativos
- **A1 — Nenhum acesso no período:**  
  O sistema informa que não há registros de acesso para o período selecionado.

### RF Relacionados
- RF05 — Controle de Acesso
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC17 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a taxa de ocupação de cada aula, identificando modalidades mais e menos procuradas.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Relatório de ocupação gerado e disponível para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de ocupação de aulas.
3. O gerente define o período e aplica filtros por modalidade ou instrutor.
4. O sistema processa os dados de agendamentos e presenças e exibe o relatório com percentual de ocupação por aula.
5. O gerente pode exportar o relatório em PDF ou planilha.

### Fluxos Alternativos
- **A1 — Nenhuma aula no período:**  
  O sistema informa que não há dados de aulas para o período selecionado.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF07 — Lista de Presença
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN02 — Limite de vagas
- RN06 — Acesso restrito por perfil

---

## UC18 — Enviar Notificação de Vencimento de Mensalidade

### Ator Principal
Sistema (automático)

### Objetivo
Notificar o aluno sobre o vencimento próximo ou ocorrido da mensalidade para evitar inadimplência.

### Pré-condições
- O aluno deve possuir cadastro ativo com contato registrado.

### Pós-condições
- Notificação de vencimento enviada ao aluno com sucesso.

### Fluxo Principal
1. O sistema verifica diariamente os vencimentos de mensalidades.
2. O sistema identifica alunos com vencimento nos próximos 3 dias ou já vencidos.
3. O sistema gera a notificação com o valor devido e a data de vencimento.
4. O sistema envia a notificação ao aluno pelo canal cadastrado (e-mail, SMS ou push).
5. O sistema registra o envio da notificação no histórico do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio:**  
  O sistema registra o erro e tenta reenviar na próxima execução do ciclo.

- **A2 — Aluno sem contato registrado:**  
  O sistema registra a pendência para que a recepcionista atualize os dados de contato.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC19 — Recuperar Senha

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário recupere o acesso ao sistema em caso de esquecimento de senha.

### Pré-condições
- O usuário deve possuir e-mail cadastrado e ativo no sistema.

### Pós-condições
- Usuário recebe as instruções de redefinição de senha e consegue acessar o sistema com nova senha.

### Fluxo Principal
1. O usuário acessa a tela de login e clica em "Esqueci minha senha".
2. O usuário informa o e-mail cadastrado.
3. O sistema valida o e-mail e envia um link de redefinição de senha.
4. O usuário acessa o link recebido e informa a nova senha.
5. O sistema valida a nova senha conforme as regras de segurança.
6. O sistema atualiza a senha e confirma a alteração.

### Fluxos Alternativos
- **A1 — E-mail não encontrado:**  
  O sistema informa que o e-mail não está cadastrado.

- **A2 — Link expirado:**  
  O sistema informa que o link de redefinição expirou e orienta o usuário a solicitar um novo.

- **A3 — Nova senha inválida:**  
  O sistema destaca os critérios não atendidos (mínimo de caracteres, uso de números etc.) e solicita nova tentativa.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC20 — Desativar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Desativar o cadastro de um aluno que solicitou cancelamento da matrícula na academia.

### Pré-condições
- Recepcionista deve estar autenticada.
- O aluno deve possuir cadastro ativo no sistema.
- O aluno não deve possuir pendências financeiras em aberto.

### Pós-condições
- Cadastro do aluno marcado como inativo.
- Acesso à catraca revogado.
- Histórico do aluno preservado no sistema para consultas futuras.

### Fluxo Principal
1. A recepcionista acessa o módulo de alunos e pesquisa o aluno.
2. O sistema exibe os dados do aluno e sua situação financeira.
3. A recepcionista verifica que não há pendências financeiras e seleciona a opção de desativação.
4. O sistema solicita confirmação da operação.
5. A recepcionista confirma a desativação.
6. O sistema desativa o cadastro, revoga o acesso RFID e registra o motivo/data do encerramento.
7. O sistema exibe confirmação da desativação.

### Fluxos Alternativos
- **A1 — Aluno com pendência financeira:**  
  O sistema bloqueia a desativação e informa que há débitos em aberto que devem ser quitados antes do encerramento.

- **A2 — Cancelamento da operação:**  
  O sistema permanece com o cadastro ativo sem alterações.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF03 — Controle de Pagamentos
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN04 — Pagamento parcial
- RN06 — Acesso restrito por perfil

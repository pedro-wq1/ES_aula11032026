## UC01 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir que a recepcionista registre um novo aluno no sistema com seus dados pessoais e plano contratado.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- O plano a ser atribuído deve estar ativo no sistema.

### Pós-condições
- Aluno cadastrado com situação "ativo" no sistema.
- Cartão RFID vinculado ao aluno.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas.
2. O sistema exibe o formulário de cadastro.
3. A recepcionista preenche os dados pessoais, de contato e endereço do aluno.
4. A recepcionista seleciona o plano contratado.
5. O sistema valida os dados informados.
6. O sistema registra o aluno e vincula o cartão RFID.
7. O sistema exibe confirmação de cadastro realizado com sucesso.

### Fluxos Alternativos
- **A1 — Dados obrigatórios não preenchidos:**
  O sistema exibe mensagem de erro indicando os campos ausentes e aguarda a correção.

- **A2 — Plano selecionado está inativo:**
  O sistema alerta que o plano não está disponível e solicita a seleção de outro.

### RF Relacionados
- RF01 — Cadastro de Alunos
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF02 — Segurança (dados armazenados de forma criptografada)
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Recepcionista realiza matrículas)

---

## UC02 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente crie, edite, ative ou desative planos oferecidos pela academia.

### Pré-condições
- Gerente deve estar autenticado no sistema.

### Pós-condições
- Plano criado, alterado ou com status atualizado no sistema.

### Fluxo Principal
1. O gerente acessa o módulo de gerenciamento de planos.
2. O sistema exibe a lista de planos cadastrados e seus status.
3. O gerente seleciona a ação desejada: criar, editar, ativar ou desativar.
4. O sistema exibe o formulário correspondente à ação.
5. O gerente preenche ou altera as informações do plano.
6. O sistema valida e salva as alterações.
7. O sistema exibe confirmação da operação realizada.

### Fluxos Alternativos
- **A1 — Tentativa de desativar plano com alunos vinculados:**
  O sistema alerta que existem alunos ativos no plano e solicita confirmação para prosseguir.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Gerente configura planos)

---

## UC03 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor ou Gerente)

### Objetivo
Permitir que o usuário acesse o sistema autenticando-se com suas credenciais.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso.
- Sistema redireciona o usuário para a tela inicial correspondente ao seu perfil.

### Fluxo Principal
1. O usuário acessa a tela de login do sistema.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais informadas.
4. O sistema identifica o perfil do usuário (Aluno, Recepcionista, Instrutor ou Gerente).
5. O sistema inicia a sessão e redireciona para a tela inicial do perfil correspondente.

### Fluxos Alternativos
- **A1 — Credenciais inválidas:**
  O sistema exibe mensagem de erro e permite nova tentativa.

- **A2 — Conta bloqueada ou inativa:**
  O sistema impede o login e orienta o usuário a contatar a recepção.

### RF Relacionados
- RF04 — Regularidade do Aluno (verificação de situação ao autenticar)

### RNF Relacionados
- RNF02 — Segurança (dados de autenticação criptografados)
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC04 — Editar Cadastro de Aluno

### Ator Principal
Recepcionista

### Objetivo
Permitir a atualização dos dados pessoais, de contato ou de plano de um aluno já cadastrado.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Dados do aluno atualizados e salvos no sistema.

### Fluxo Principal
1. A recepcionista acessa o módulo de matrículas e busca o aluno pelo nome ou CPF.
2. O sistema exibe os dados atuais do aluno.
3. A recepcionista seleciona a opção de edição.
4. O sistema exibe o formulário preenchido com os dados existentes.
5. A recepcionista altera os campos desejados.
6. O sistema valida os dados informados.
7. O sistema salva as alterações e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

- **A2 — Dados inválidos:**
  O sistema exibe mensagem de erro indicando os campos com problema e aguarda a correção.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil (somente Recepcionista edita cadastros)

---

## UC05 — Verificar Regularidade do Aluno

### Ator Principal
Recepcionista

### Objetivo
Consultar a situação financeira e de cadastro de um aluno para fins de atendimento ou suporte.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Situação do aluno exibida na tela (regular, inadimplente ou inativo).

### Fluxo Principal
1. A recepcionista acessa o módulo de consulta de alunos.
2. A recepcionista busca o aluno pelo nome ou CPF.
3. O sistema localiza o aluno e exibe seu status atual: regular, inadimplente ou inativo.
4. O sistema exibe também o histórico de pagamentos e a data do próximo vencimento.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC06 — Registrar Pagamento de Mensalidade

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade de um aluno e atualizar sua situação de regularidade.

### Pré-condições
- Recepcionista deve estar autenticada no sistema.
- Aluno deve estar cadastrado no sistema.

### Pós-condições
- Pagamento registrado no histórico do aluno.
- Situação do aluno atualizada para "regular".

### Fluxo Principal
1. A recepcionista busca o aluno pelo nome ou CPF.
2. O sistema exibe os dados do aluno e o valor da mensalidade em aberto.
3. A recepcionista seleciona a forma de pagamento (dinheiro, cartão ou PIX).
4. O sistema registra o pagamento pelo valor integral.
5. O sistema atualiza imediatamente a situação do aluno para "regular".
6. O sistema exibe confirmação do pagamento.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema informa que o aluno não foi localizado e retorna à tela de busca.

- **A2 — Tentativa de pagamento parcial:**
  O sistema bloqueia a operação e exibe mensagem informando que apenas pagamento integral é permitido.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade

---

## UC07 — Gerar Cobrança Online

### Ator Principal
Aluno

### Objetivo
Gerar boleto ou link de pagamento online para que o aluno quite sua mensalidade de forma remota.

### Pré-condições
- Aluno deve estar cadastrado e ativo no sistema.
- Mensalidade deve estar em aberto.

### Pós-condições
- Cobrança gerada e enviada ao aluno pelo canal configurado (e-mail ou app).

### Fluxo Principal
1. O sistema identifica os alunos com mensalidade em aberto.
2. O sistema gera o boleto ou o link de pagamento para cada aluno elegível.
3. O sistema envia a cobrança ao aluno pelo canal configurado.
4. O sistema registra a geração da cobrança no histórico do aluno.
5. Após o pagamento confirmado, o sistema atualiza a situação do aluno para "regular".

### Fluxos Alternativos
- **A1 — Falha na geração da cobrança:**
  O sistema registra o erro e agenda nova tentativa de geração.

- **A2 — Pagamento não confirmado até a data de vencimento:**
  O sistema mantém a situação do aluno como inadimplente e aciona o bloqueio de acesso conforme RN01.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN04 — Pagamento parcial não permitido
- RN07 — Atualização automática da regularidade

---

## UC08 — Enviar Notificação de Vencimento de Mensalidade

### Ator Principal
Aluno

### Objetivo
Notificar automaticamente o aluno sobre o próximo vencimento de sua mensalidade, a fim de evitar inadimplência.

### Pré-condições
- Aluno deve estar cadastrado e ativo no sistema.
- Data de vencimento da mensalidade deve estar configurada.

### Pós-condições
- Notificação enviada ao aluno com as informações de vencimento.

### Fluxo Principal
1. O sistema verifica diariamente as datas de vencimento das mensalidades.
2. O sistema identifica os alunos com vencimento próximo (conforme regra de antecedência configurada).
3. O sistema gera a notificação com os dados do valor e da data de vencimento.
4. O sistema envia a notificação ao aluno pelo canal configurado (e-mail ou app).
5. O sistema registra o envio da notificação no histórico do aluno.

### Fluxos Alternativos
- **A1 — Falha no envio da notificação:**
  O sistema registra a falha e realiza nova tentativa de envio no ciclo seguinte.

### RF Relacionados
- RF10 — Notificações (vencimento de mensalidade)

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN01 — Bloqueio por inadimplência (a notificação visa prevenir o bloqueio)

---

## UC09 — Validar Acesso pela Catraca

### Ator Principal
Sistema de Catraca (API externa)

### Objetivo
Verificar se o aluno possui autorização para entrar na academia via leitura do cartão RFID.

### Pré-condições
- O sistema de catraca deve estar integrado via API REST.
- O aluno deve possuir cartão RFID vinculado ao seu cadastro.

### Pós-condições
- Acesso liberado e registrado no histórico do aluno.
- Ou acesso negado com registro da tentativa.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia o código RFID ao sistema via API REST.
3. O sistema identifica o aluno pelo código RFID.
4. O sistema verifica se o aluno está com a mensalidade em dia.
5. O sistema retorna autorização de acesso à catraca.
6. A catraca libera a entrada e o sistema registra o acesso.

### Fluxos Alternativos
- **A1 — Mensalidade vencida há mais de 5 dias:**
  O sistema retorna negação de acesso. A catraca permanece bloqueada.

- **A2 — Cartão RFID não reconhecido:**
  O sistema retorna erro de identificação. O acesso é negado.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF03 — Performance (resposta em até 3 segundos)
- RNF06 — Integração via API REST com JSON

### RN Relacionadas
- RN01 — Bloqueio por inadimplência (vencida há mais de 5 dias)

---

## UC10 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno reserve uma vaga em uma aula disponível.

### Pré-condições
- Aluno deve estar autenticado no sistema.
- Aluno deve estar com situação "regular".
- A aula deve possuir vagas disponíveis.

### Pós-condições
- Reserva registrada para o aluno na aula selecionada.
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno acessa o módulo de agendamento.
2. O sistema exibe a lista de aulas disponíveis com horários e vagas.
3. O aluno seleciona a aula desejada.
4. O sistema verifica a disponibilidade de vagas.
5. O sistema registra a reserva do aluno.
6. O sistema envia notificação de confirmação ao aluno.

### Fluxos Alternativos
- **A1 — Aula sem vagas disponíveis:**
  O sistema informa que a capacidade máxima foi atingida e bloqueia o agendamento.

- **A2 — Aluno inadimplente:**
  O sistema impede o agendamento e orienta o aluno a regularizar a situação.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações (confirmação de agendamento)

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas por aula

---


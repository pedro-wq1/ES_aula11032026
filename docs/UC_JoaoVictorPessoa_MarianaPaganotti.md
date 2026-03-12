# Documento de Casos de Uso — FitPass Gym Management

**Dupla:** João Victor Pessoa e Mariana Paganotti
**Disciplina:** Engenharia de Software

---

## UC01 — Realizar Login

**Ator Principal**
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

**Objetivo**
Permitir que o usuário acesse o sistema com suas credenciais.

**Pré-condições**
Usuário deve possuir cadastro ativo no sistema.

**Pós-condições**
Sessão iniciada com sucesso e usuário redirecionado ao painel correspondente ao seu perfil.

**Fluxo Principal**
1. O usuário informa e-mail e senha na tela de login.
2. O sistema valida as credenciais informadas.
3. O sistema autentica o usuário e redireciona para a tela inicial do seu perfil.

**Fluxos Alternativos**
A1 — Senha incorreta:
O sistema exibe mensagem de erro genérica e permite nova tentativa.

A2 — Conta bloqueada:
O sistema impede o login e instrui o usuário a recuperar o acesso via e-mail.

**RF Relacionados**
RF01, RF09

**RNF Relacionados**
RNF02 (Segurança), RNF03 (Tempo de Resposta)

**RN Relacionadas**
RN06

---

## UC02 — Cadastrar Novo Aluno

**Ator Principal**
Recepcionista

**Objetivo**
Registrar um novo cliente na base de dados da academia.

**Pré-condições**
Recepcionista autenticado no sistema.

**Pós-condições**
Aluno registrado com dados pessoais, endereço e plano inicial vinculado.

**Fluxo Principal**
1. A recepcionista acessa o módulo de matrículas.
2. O sistema solicita dados: Nome, CPF, Endereço, Contato e Plano.
3. A recepcionista preenche as informações.
4. O sistema valida os campos obrigatórios e salva o registro.

**Fluxos Alternativos**
A1 — CPF já cadastrado:
O sistema alerta que o aluno já existe e impede a duplicidade.

**RF Relacionados**
RF01

**RNF Relacionados**
RNF02 (Segurança), RNF04 (Usabilidade)

**RN Relacionadas**
RN06

---

## UC03 — Criar Novo Plano de Academia

**Ator Principal**
Gerente

**Objetivo**
Definir novas modalidades de planos disponíveis para venda (Mensal, Trimestral, Anual etc.).

**Pré-condições**
Gerente autenticado no sistema.

**Pós-condições**
Novo tipo de plano disponível para seleção nas matrículas.

**Fluxo Principal**
1. O gerente acessa "Configurações de Planos".
2. O gerente define o nome, valor, duração e modalidades incluídas.
3. O sistema armazena a nova configuração e disponibiliza o plano.

**Fluxos Alternativos**
A1 — Valor inválido:
O sistema solicita correção de valores negativos ou zerados.

**RF Relacionados**
RF02

**RNF Relacionados**
RNF05 (Escalabilidade)

**RN Relacionadas**
RN06

---

## UC04 — Editar Plano Existente

**Ator Principal**
Gerente

**Objetivo**
Alterar valores ou condições de um plano já cadastrado.

**Pré-condições**
Plano deve estar cadastrado no sistema.

**Pós-condições**
Dados do plano atualizados e válidos para novas vendas.

**Fluxo Principal**
1. O gerente busca o plano desejado.
2. O sistema exibe os dados atuais do plano.
3. O gerente altera as informações necessárias.
4. O sistema valida e salva as alterações.

**Fluxos Alternativos**
A1 — Plano com alunos ativos:
O sistema avisa que a mudança afetará apenas novas adesões, mantendo as condições anteriores para os alunos já vinculados.

**RF Relacionados**
RF02

**RNF Relacionados**
RNF01 (Disponibilidade)

**RN Relacionadas**
RN06

---

## UC05 — Registrar Pagamento Presencial

**Ator Principal**
Recepcionista

**Objetivo**
Registrar a quitação de mensalidade realizada na recepção.

**Pré-condições**
Aluno selecionado e com débito pendente.

**Pós-condições**
Pagamento registrado e situação do aluno atualizada imediatamente (RN07).

**Fluxo Principal**
1. O recepcionista seleciona o aluno e a parcela em aberto.
2. O sistema solicita a forma de pagamento: Dinheiro, Cartão ou PIX.
3. O recepcionista confirma o recebimento do valor integral (RN04).
4. O sistema gera o comprovante e atualiza o status financeiro do aluno imediatamente.

**Fluxos Alternativos**
A1 — Pagamento parcial:
O sistema bloqueia a operação informando que não é permitido pagamento parcial (RN04).

**RF Relacionados**
RF03, RF04

**RNF Relacionados**
RNF03 (Tempo de Resposta)

**RN Relacionadas**
RN04, RN06, RN07

---

## UC06 — Gerar Boleto para Pagamento Online

**Ator Principal**
Recepcionista

**Objetivo**
Emitir documento de cobrança para pagamento remoto pelo aluno.

**Pré-condições**
Integração financeira ativa no sistema.

**Pós-condições**
Boleto gerado e disponibilizado no perfil do aluno.

**Fluxo Principal**
1. O recepcionista solicita a emissão de cobrança para o aluno selecionado.
2. O sistema se comunica com a API bancária.
3. O sistema gera o link do boleto e o salva no perfil do aluno.

**Fluxos Alternativos**
A1 — Falha na API:
O sistema avisa sobre a indisponibilidade e sugere tentar novamente mais tarde.

**RF Relacionados**
RF03

**RNF Relacionados**
RNF06 (Integração)

**RN Relacionadas**
RN06

---

## UC07 — Verificar Regularidade do Aluno (Automático)

**Ator Principal**
Sistema

**Objetivo**
Monitorar diariamente o status financeiro de todos os alunos.

**Pré-condições**
Rotina agendada configurada ou gatilho de acesso ativo.

**Pós-condições**
Status do aluno atualizado para "Inadimplente" ou "Regular" conforme situação.

**Fluxo Principal**
1. O sistema verifica a data de vencimento das parcelas de todos os alunos.
2. O sistema identifica alunos com pagamentos atrasados.
3. Se o atraso for superior a 5 dias, o sistema marca o aluno para bloqueio de acesso (RN01).

**Fluxos Alternativos**
A1 — Pagamento identificado:
O sistema restaura a regularidade do aluno imediatamente (RN07).

**RF Relacionados**
RF04

**RNF Relacionados**
RNF01 (Disponibilidade)

**RN Relacionadas**
RN01, RN07

---

## UC08 — Validar Acesso na Catraca

**Ator Principal**
Sistema de Catraca (API)

**Objetivo**
Liberar ou bloquear a entrada física do aluno via RFID.

**Pré-condições**
Aluno posiciona a tag RFID no leitor da catraca.

**Pós-condições**
Acesso liberado e registro de entrada salvo, ou bloqueio exibido ao aluno.

**Fluxo Principal**
1. O aluno aproxima o cartão/pulseira RFID do leitor.
2. O sistema de catraca envia o ID para o servidor FitPass via API REST (JSON).
3. O sistema verifica a regularidade do aluno (RF04).
4. Se o aluno estiver regular ou com atraso de até 5 dias, o sistema envia sinal de liberação.

**Fluxos Alternativos**
A1 — Inadimplência superior a 5 dias:
O sistema nega o acesso (RN01) e orienta o aluno a dirigir-se à recepção.

A2 — RFID não reconhecido:
O sistema retorna credencial inválida e a catraca permanece bloqueada.

**RF Relacionados**
RF04, RF05

**RNF Relacionados**
RNF03 (Tempo de Resposta: até 3s), RNF06 (Integração via API REST/JSON)

**RN Relacionadas**
RN01

---

## UC09 — Consultar Grade de Aulas

**Ator Principal**
Aluno

**Objetivo**
Visualizar horários, modalidades e vagas disponíveis nas aulas.

**Pré-condições**
Aluno autenticado no aplicativo ou portal.

**Pós-condições**
Informações de horários exibidas ao aluno.

**Fluxo Principal**
1. O aluno acessa o módulo de "Agendamentos".
2. O sistema exibe a lista de aulas com horários, instrutores e vagas disponíveis.

**Fluxos Alternativos**
A1 — Nenhuma aula cadastrada:
O sistema informa que não há horários disponíveis para a data selecionada.

**RF Relacionados**
RF06

**RNF Relacionados**
RNF04 (Usabilidade)

**RN Relacionadas**
Nenhuma

---

## UC10 — Agendar Aula Coletiva

**Ator Principal**
Aluno

**Objetivo**
Reservar uma vaga em uma aula específica.

**Pré-condições**
Aluno deve estar regular e a aula deve ter vagas disponíveis.

**Pós-condições**
Reserva confirmada e vaga subtraída do total disponível.

**Fluxo Principal**
1. O aluno seleciona a aula desejada na grade de horários.
2. O sistema verifica o limite de vagas (RN02).
3. O sistema confirma a reserva e envia notificação de confirmação ao aluno (RF10).

**Fluxos Alternativos**
A1 — Aula lotada:
O sistema informa que não há mais vagas disponíveis e bloqueia a reserva (RN02).

A2 — Aluno inadimplente:
O sistema impede o agendamento até regularização financeira (RN01).

**RF Relacionados**
RF06, RF10

**RNF Relacionados**
RNF04 (Usabilidade)

**RN Relacionadas**
RN01, RN02

---

## UC11 — Cancelar Reserva de Aula

**Ator Principal**
Aluno

**Objetivo**
Desistir da participação em uma aula previamente agendada.

**Pré-condições**
Reserva ativa no sistema.

**Pós-condições**
Vaga liberada para outros alunos.

**Fluxo Principal**
1. O aluno acessa seus agendamentos e solicita o cancelamento da reserva.
2. O sistema verifica se o horário atual é pelo menos 1 hora antes do início da aula (RN03).
3. O sistema confirma o cancelamento e libera a vaga.

**Fluxos Alternativos**
A1 — Fora do prazo:
O sistema impede o cancelamento pois falta menos de 1 hora para o início da aula (RN03).

**RF Relacionados**
RF06

**RNF Relacionados**
RNF04 (Usabilidade)

**RN Relacionadas**
RN02, RN03

---

## UC12 — Registrar Presença em Aula

**Ator Principal**
Instrutor

**Objetivo**
Confirmar a participação dos alunos presentes na aula.

**Pré-condições**
Aula em andamento ou recém-finalizada.

**Pós-condições**
Lista de presença salva e atualizada no histórico de cada aluno.

**Fluxo Principal**
1. O instrutor acessa a aula agendada no sistema.
2. O sistema exibe a lista de alunos que reservaram vaga.
3. O instrutor marca os alunos presentes.
4. O sistema salva as informações com data e hora.

**Fluxos Alternativos**
A1 — Aluno não agendado presente:
O instrutor pode adicionar o aluno manualmente, se houver vaga disponível na turma.

**RF Relacionados**
RF07

**RNF Relacionados**
RNF01 (Disponibilidade)

**RN Relacionadas**
RN06

---

## UC13 — Registrar Avaliação Física

**Ator Principal**
Instrutor

**Objetivo**
Cadastrar as métricas corporais do aluno no sistema.

**Pré-condições**
Aluno deve estar ativo e regular (RN05).

**Pós-condições**
Avaliação salva no perfil do aluno e disponível para consulta.

**Fluxo Principal**
1. O instrutor inicia a avaliação física do aluno.
2. O sistema verifica o status do aluno (RN05).
3. O instrutor insere peso, altura, dobras cutâneas e demais medidas.
4. O sistema calcula o IMC e demais indicadores e salva a avaliação.

**Fluxos Alternativos**
A1 — Aluno irregular:
O sistema bloqueia o início da avaliação física e informa a pendência (RN05).

**RF Relacionados**
RF08

**RNF Relacionados**
RNF02 (Segurança), RNF04 (Usabilidade)

**RN Relacionadas**
RN05, RN06

---

## UC14 — Anexar Arquivos à Avaliação Física

**Ator Principal**
Instrutor

**Objetivo**
Adicionar fotos ou laudos externos ao registro de avaliação do aluno.

**Pré-condições**
Avaliação física aberta para edição no sistema.

**Pós-condições**
Arquivos vinculados ao perfil do aluno e à avaliação correspondente.

**Fluxo Principal**
1. O instrutor seleciona a opção "Anexar Arquivos" na avaliação.
2. O instrutor escolhe as imagens ou PDFs desejados.
3. O sistema realiza o upload e vincula os arquivos à avaliação atual.

**Fluxos Alternativos**
A1 — Arquivo com tamanho acima do limite:
O sistema rejeita o arquivo e solicita um arquivo menor conforme o limite estabelecido.

**RF Relacionados**
RF08

**RNF Relacionados**
RNF02 (Segurança)

**RN Relacionadas**
RN06

---

## UC15 — Gerar Relatório de Inadimplência

**Ator Principal**
Gerente

**Objetivo**
Identificar todos os alunos com pagamentos atrasados para tomada de ação.

**Pré-condições**
Gerente autenticado com perfil gerencial.

**Pós-condições**
Lista de inadimplentes exibida e disponível para exportação.

**Fluxo Principal**
1. O gerente solicita o relatório de inadimplência no módulo de relatórios.
2. O sistema filtra os pagamentos vencidos e não pagos.
3. O sistema exibe nome, valor em aberto e dias de atraso de cada aluno.

**Fluxos Alternativos**
A1 — Filtro por período:
O gerente pode restringir a busca definindo datas de início e fim.

**RF Relacionados**
RF09

**RNF Relacionados**
RNF01 (Disponibilidade), RNF05 (Escalabilidade)

**RN Relacionadas**
RN01, RN06

---

## UC16 — Gerar Relatório de Alunos Ativos

**Ator Principal**
Gerente

**Objetivo**
Listar todos os alunos com matrículas vigentes para análise de retenção e faturamento.

**Pré-condições**
Gerente autenticado com permissões administrativas.

**Pós-condições**
Relatório gerado com a lista de membros ativos.

**Fluxo Principal**
1. O gerente acessa o menu "Relatórios Gerenciais".
2. O gerente seleciona a opção "Relatório de Alunos Ativos".
3. O sistema consulta a base de dados filtrando alunos com planos ativos e situação regular.
4. O sistema exibe a lista com Nome, Plano, Data de Expiração e Último Acesso.

**Fluxos Alternativos**
A1 — Nenhum registro encontrado:
O sistema informa que não há alunos ativos na base de dados no momento.

**RF Relacionados**
RF09

**RNF Relacionados**
RNF01 (Disponibilidade), RNF05 (Escalabilidade)

**RN Relacionadas**
RN06

---

## UC17 — Gerar Relatório de Ocupação de Aulas

**Ator Principal**
Gerente

**Objetivo**
Analisar a demanda e o desempenho das modalidades coletivas.

**Pré-condições**
Dados de agendamento e presença existentes no sistema.

**Pós-condições**
Relatório com percentuais de ocupação gerado.

**Fluxo Principal**
1. O gerente acessa "Relatórios de Aulas".
2. O sistema processa a média de alunos por aula em relação à capacidade máxima.
3. O sistema gera gráficos e tabelas de desempenho das aulas.

**Fluxos Alternativos**
A1 — Sem dados suficientes:
O sistema informa que não há dados suficientes para o período selecionado.

**RF Relacionados**
RF09

**RNF Relacionados**
RNF01 (Disponibilidade), RNF05 (Escalabilidade)

**RN Relacionadas**
RN02, RN06

---

## UC18 — Consultar Histórico de Acessos

**Ator Principal**
Gerente

**Objetivo**
Monitorar o fluxo de pessoas e a frequência individual dos alunos na academia.

**Pré-condições**
Registros de catraca existentes no sistema (UC08).

**Pós-condições**
Dados de frequência exibidos em tela com detalhamento por aluno ou período.

**Fluxo Principal**
1. O gerente busca por um aluno ou data específica no módulo de relatórios.
2. O sistema recupera todos os registros de entrada e saída do período.
3. O sistema exibe o histórico detalhado com data, hora e status de cada acesso.

**Fluxos Alternativos**
A1 — Acesso negado registrado:
O sistema destaca em vermelho as tentativas de entrada bloqueadas (RN01).

**RF Relacionados**
RF09, RF05

**RNF Relacionados**
RNF02 (Segurança), RNF05 (Escalabilidade)

**RN Relacionadas**
RN01, RN06

---

## UC19 — Notificar Vencimento de Mensalidade

**Ator Principal**
Sistema

**Objetivo**
Alertar o aluno sobre o prazo de pagamento da mensalidade.

**Pré-condições**
Mensalidade próxima do vencimento (padrão: 3 dias antes).

**Pós-condições**
Notificação enviada ao e-mail ou aplicativo do aluno.

**Fluxo Principal**
1. O sistema identifica parcelas que vencem nos próximos 3 dias.
2. O sistema dispara uma notificação automática ao aluno (RF10).
3. O sistema registra o envio no log de comunicações.

**Fluxos Alternativos**
A1 — Falha no envio:
O sistema agenda uma nova tentativa em 4 horas.

**RF Relacionados**
RF10

**RNF Relacionados**
RNF01 (Disponibilidade)

**RN Relacionadas**
RN01

---

## UC20 — Notificar Confirmação de Agendamento

**Ator Principal**
Sistema

**Objetivo**
Confirmar formalmente ao aluno que sua vaga foi reservada com sucesso.

**Pré-condições**
Conclusão bem-sucedida do UC10 (Agendar Aula Coletiva).

**Pós-condições**
Aluno recebe confirmação com os detalhes do agendamento.

**Fluxo Principal**
1. Após a reserva (UC10), o sistema gera uma mensagem de confirmação automática.
2. O sistema envia notificação push ou e-mail para o aluno com dados da aula.
3. O sistema registra o envio no log de comunicações.

**Fluxos Alternativos**
A1 — Aluno desativou notificações:
O sistema mantém apenas o registro interno no portal, sem envio externo.

**RF Relacionados**
RF10

**RNF Relacionados**
RNF01 (Disponibilidade)

**RN Relacionadas**
RN02, RN03

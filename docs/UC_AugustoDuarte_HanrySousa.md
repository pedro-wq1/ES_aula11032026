## UC01 — Cadastro de Alunos

### Ator Principal
Aluno

### Objetivo
Permitir que o usuário crie um cadastro com dados pessoais, contato, endereço e plano contratado.

### Pré-condições
- Aluno não deve possuir cadastro ativo.

### Pós-condições
- Cadastro criado com sucesso.

### Fluxo Principal
1. O usuário informa cpf.
2. O sistema valida se não há cpf igual aos informado já registrado.
3. O sistema autentica o usuário e redireciona para a tela de informações pessoais.
4. O usuário informa as suas informações pessoais como contato, endereço e plano contratado.

### Fluxos Alternativos
- **A1 — Email já registrado:**  
  O sistema exibe mensagem de erro instrui o usuário a realizar o login para o acesso.

- **A2 - Limite de vagas:**
  O sistema informa que não está aceitando novos alunos no momento. Pede para entrar em contato com os gerentes ou tentar novamente mais tarde.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas

## UC02 — Gerenciamento de planos

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize e gerencie os planos.

### Pré-condições
- Aluno deve possuir cadastro ativo.

### Pós-condições
- Valida o pagamento, troca de plano e volta para a tela inicial.

### Fluxo Principal
1. O usuário solicita a visualização dos planos
2. Caso queira, troca um plano
3. Tela de pagamento aparece.
4. Após o pagamento ser validado, atualiza o plano do usuário.


### Fluxos Alternativos
- **A1 — Pagamento bloqueado:**  
  O pagamento foi bloqueado. Informa o usuário o motivo e pede para entrar em contato.


### RF Relacionados
- RF02 — Gerenciamento de Planos
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN04 — Pagamento parcial
- RNF05 — Escalabilidade


## UC03 — Controle de Pagamentos

### Ator Principal
Recepcionista

### Objetivo
Permitir que o recepcionista faça o controle dos pagamentos na recepção, informando a forma de pagamento, valor, data e realizado por quem.

### Pré-condições
- Usuário deve possuir cadastro ativo.

### Pós-condições
- Valida o pagamento. Emite nota fiscal, informando todas as informações relevantes.

### Fluxo Principal
1. Recebe o valor do pagamento.
2. Compara com o valor do plano do usuário.
3. Compara a data de vencimento do pagamento.
4. Informa no sistema que o usuário está com o pagamento em dia.


### Fluxos Alternativos
- **A1 — Pagamento parcial bloqueado:**  
  Caso o pagamento não esteja completo, pagamento é bloqueado.


### RF Relacionados
- RF02 — Gerenciamento de Planos
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RN07 — Atualização automática da regularidade

### RN Relacionadas
- RN04 — Pagamento parcial
- RNF05 — Escalabilidade

## UC04 — Regularidade do Aluno

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente verifique se o aluno está com mensalidade em dia.

### Pré-condições
- Gerente deve possuir cadastro ativo e validado como gerência.

### Pós-condições
- Informa os dados do aluno, incluindo seus planos e pagamentos

### Fluxo Principal
1. Recebe o registro do aluno.
2. Retorna os dados do aluno informado.
3. Verifica a data atual com a data de vencimento do pagamento referente ao plano


### Fluxos Alternativos
- **A1 — Plano com pagamento em dia:**  
- Informa que o pagamento já foi realizado, e libera a catraca para o aluno.

- **A2 — Plano com pagamento em atraso:**  
- Informa que o pagamento está pendente, com no máximo 5 dias de atraso, e bloqueia a catraca para o aluno.


### RF Relacionados
- RF02 — Gerenciamento de Planos
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RNF01 — Disponibilidade

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade
- RN01 — Bloqueio por inadimplência

- ## UC04 — Regularidade do Aluno

### Ator Principal
Gerente

### Objetivo
Permitir que o gerente verifique se o aluno está com mensalidade em dia.

### Pré-condições
- Gerente deve possuir cadastro ativo e validado como gerência.

### Pós-condições
- Informa os dados do aluno, incluindo seus planos e pagamentos

### Fluxo Principal
1. Recebe o registro do aluno.
2. Retorna os dados do aluno informado.
3. Verifica a data atual com a data de vencimento do pagamento referente ao plano


### Fluxos Alternativos
- **A1 — Plano com pagamento em dia:**  
- Informa que o pagamento já foi realizado, e libera a catraca para o aluno.

- **A2 — Plano com pagamento em atraso:**  
- Informa que o pagamento está pendente, com no máximo 5 dias de atraso, e bloqueia a catraca para o aluno.


### RF Relacionados
- RF02 — Gerenciamento de Planos
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RNF01 — Disponibilidade

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade
- RN01 — Bloqueio por inadimplência

- ## UC05 - Controle de acesso
### Ator Principal
Aluno

### Objetivo
Validar a entrada do aluno na academia através da integração com a catraca via RFID, verificando sua situação de cadastro e pagamento.

### Pré-condições
- O aluno deve possuir um cadastro ativo e uma tag RFID vinculada ao seu registro.
- A catraca deve estar devidamente integrada via API ao sistema.

### Pós-condições
- Acesso liberado (catraca destravada) ou negado.
- Registro do log de entrada (data e hora) no histórico do aluno.

### Fluxo Principal
1. O aluno aproxima sua tag RFID do leitor da catraca.
2. O sistema de catraca envia o ID da tag para o software FitPass via API REST.
3. O sistema identifica o aluno associado à tag.
4. O sistema verifica se o aluno está com o plano ativo e a mensalidade em dia (conforme UC04).
5. O sistema envia um comando de sucesso para a catraca.
6. A catraca é liberada e o sistema registra o acesso.

### Fluxos Alternativos
- **A1 — Aluno Inadimplente (RN01):**
- Caso o pagamento esteja atrasado há mais de 5 dias, o sistema nega a liberação, mantém a catraca travada e exibe uma mensagem no visor da catraca/monitor da recepção instruindo o aluno a regularizar a situação.

- **A2 — Tag não reconhecida:**
-  Se o ID da tag não estiver vinculado a nenhum aluno, o sistema nega o acesso e alerta a recepção sobre uma tentativa com tag inválida.

- ** A3 — Falha de Comunicação (RNF06): **
Caso a API não responda dentro do tempo limite, o sistema aciona um log de erro e o acesso deve ser validado manualmente pelo recepcionista.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF02 — Segurança (Dados da tag criptografados)
- RNF03 — Performance (Validação em até 3 segundos)
- RNF06 — Integração (API REST / JSON)

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN06 — Acesso restrito por perfil (Apenas alunos e funcionários autorizados)
- RN07 — Atualização automática da regularidade


## - UC06 — Agendamento de Aulas
### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize a grade de horários e reserve sua vaga nas aulas coletivas ou específicas da academia.

### Pré-condições
- Aluno deve possuir cadastro ativo.
- Aluno deve estar com a situação financeira regular (sem débitos pendentes há mais de 5 dias).

### Pós-condições
- Reserva confirmada no sistema.
- O número de vagas disponíveis para a aula é atualizado (decrementado).
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno acessa a funcionalidade de agendamento no sistema.
2. O sistema exibe a lista de aulas disponíveis, contendo: nome da aula, instrutor, horário e vagas restantes.
3. O aluno seleciona a aula e o horário desejado.
4. O sistema valida se o aluno está regular e se ainda há vagas disponíveis (RN02).
5. O aluno confirma a reserva da vaga.
6. O sistema registra o agendamento e emite uma notificação de confirmação (RF10).

### Fluxos Alternativos
- ** A1 — Limite de vagas atingido (RN02): **
- Caso a aula selecionada já tenha atingido o número máximo de alunos, o sistema impede a reserva.
- O sistema exibe mensagem informando que a turma está lotada e sugere outros horários.

- **A2 — Aluno irregular (RN05): **
- Caso o aluno tente agendar e não esteja com o status "Ativo/Regular", o sistema bloqueia a ação.
- O sistema instrui o aluno a procurar a recepção para regularizar sua situação.

- **A3 — Cancelamento de agendamento (RN03): **
- O aluno solicita o cancelamento de uma aula já agendada.
- O sistema verifica se o horário atual é superior a 1 hora do início da aula.
- Se estiver dentro do prazo, o sistema cancela a reserva e libera a vaga para outros alunos.
- Se faltar menos de 1 hora, o sistema informa que o cancelamento não é mais permitido via app.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações

### RNF Relacionados
- RNF04 — Usabilidade

- RNF03 — Performance

### RN Relacionadas
- RN02 — Limite de vagas
- RN03 — Cancelamento de agendamento
- RN05 — Avaliação física (dependência de status ativo/regular)

## UC07 — Lista de Presença
### Ator Principal
Instrutor

### Objetivo
Permitir que o instrutor registre a presença dos alunos que compareceram às aulas agendadas para fins de controle de frequência e ocupação.

### Pré-condições
- Usuário deve estar logado com perfil de Instrutor (RN06).
- A aula deve ter sido previamente cadastrada no sistema.

### Pós-condições
- Lista de presença atualizada no banco de dados.
- Dados consolidados para consulta no relatório de ocupação de aulas (RF09).

### Fluxo Principal
1. O instrutor acessa a funcionalidade "Lista de Presença".
2. O sistema exibe as aulas sob responsabilidade do instrutor no dia atual.
3. O instrutor seleciona a aula desejada.
4. O sistema apresenta a lista de alunos que realizaram o agendamento prévio (UC06).
5. O instrutor marca os alunos que estão fisicamente presentes na sala.
6. O instrutor confirma o registro da chamada.
7. O sistema salva as informações e exibe mensagem de sucesso.

## Fluxos Alternativos
** A1 — Aluno presente sem agendamento: **
- Caso um aluno esteja na aula mas seu nome não conste na lista de agendados, o instrutor pode buscar o aluno pelo nome/CPF.
- O sistema valida se o aluno está com a mensalidade em dia (RF04).
- Se regular, o instrutor adiciona o aluno manualmente à lista (respeitando a lotação máxima da sala, se aplicável).

** A2 — Ninguém compareceu: **
- O instrutor sinaliza que a aula não teve quórum.
- O sistema registra "Aula realizada sem alunos" para fins estatísticos.

### RF Relacionados
- RF07 — Lista de Presença
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF04 — Usabilidade
- RNF02 — Segurança (Acesso restrito)

### RN Relacionadas
- RN06 — Acesso restrito por perfil
- RN07 — Atualização automática da regularidade

## UC08 — Avaliação Física
### Ator Principal
Instrutor

### Objetivo
Permitir que o instrutor registre medidas biométricas, cálculos de composição corporal e anexe documentos de evolução física do aluno.

### Pré-condições
- Aluno deve estar com cadastro ativo e situação de pagamento regular (RN05).
- Usuário deve estar logado com perfil de Instrutor (RN06).

### Pós-condições
= Avaliação física registrada no histórico do aluno.
- Notificação de liberação de laudo enviada para o aluno (RF10).

Fluxo Principal
1. O instrutor busca o aluno pelo nome, CPF ou matrícula.
2. O sistema valida se o aluno está ativo e sem pendências financeiras (RN05).
3. O instrutor seleciona a opção "Nova Avaliação Física".
4. O instrutor insere os dados coletados (Peso, Altura, Dobras Cutâneas, Circunferências).
5. O sistema calcula automaticamente o IMC, Percentual de Gordura e Massa Magra.
6. O instrutor anexa arquivos (fotos de evolução ou exames laboratoriais), se necessário.
7. O instrutor salva o registro.
8. O sistema disponibiliza o resultado para o aluno no portal/app.

### Fluxos Alternativos
** A1 — Aluno Irregular (RN05): **
- O sistema identifica que o aluno está inadimplente ou inativo.
- O sistema bloqueia o preenchimento da avaliação e exibe mensagem: "Avaliação não permitida para alunos em situação irregular".

** A2 — Erro no upload de arquivo: **
- Caso o arquivo anexado exceda o limite de tamanho ou formato não suportado, o sistema exibe alerta e solicita novo arquivo.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança (Dados sensíveis de saúde criptografados)
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física
- RN06 — Acesso restrito por perfil

## UC09 — Relatórios Gerenciais
### Ator Principal
Gerente

### Objetivo
Permitir que o gerente emita relatórios analíticos para acompanhar a saúde financeira e operacional da academia.

### Pré-condições
- Usuário deve estar logado com perfil de Gerente (RN06).

### Pós-condições
- Relatório gerado em tela com opção para exportação ou impressão.

### Fluxo Principal
1. O gerente acessa o módulo de "Relatórios Gerenciais".
2. O sistema apresenta as opções de relatórios disponíveis:
3. Inadimplência (Alunos com pagamentos atrasados).
4. Alunos Ativos (Total de matriculados por plano).
5. Histórico de Acessos (Frequência por horário/catraca).
6. Ocupação das Aulas (Relação de agendamentos vs. vagas).
7. O gerente seleciona o tipo de relatório desejado.
8. O gerente define os filtros necessários (Ex: período de data, unidade da rede, tipo de plano).
9. O sistema processa os dados e exibe o relatório formatado.
10. O gerente seleciona a opção de exportar (PDF/Excel) ou imprimir.

### Fluxos Alternativos
** A1 — Filtro sem resultados: **
- Caso os critérios selecionados não retornem nenhum registro, o sistema exibe a mensagem: "Nenhum dado encontrado para os filtros aplicados".

** A2 — Acesso negado: *
- Caso um usuário com perfil de Recepcionista ou Instrutor tente acessar a URL/módulo de relatórios, o sistema bloqueia a visualização e exibe erro de permissão.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF02 — Segurança
- RNF05 — Escalabilidade (Processamento de dados de múltiplas unidades)

### RN Relacionadas
- RN06 — Acesso restrito por perfil

## UC10 — Notificações ao Aluno
Ator Principal
Sistema (Automático)

### Objetivo
Manter o aluno informado sobre eventos importantes, como vencimentos, confirmações de agendamento e novas avaliações.

### Pré-condições
- O aluno deve ter um cadastro ativo com e-mail ou dispositivo móvel vinculado.
- O evento gatilho (vencimento, agendamento ou nova avaliação) deve ter ocorrido no sistema.

### Pós-condições
- Notificação enviada com sucesso e registrada no log de comunicações.

### Fluxo Principal
1. O sistema identifica um evento gatilho:
2. Gatilho 1: Mensalidade próxima do vencimento (3 dias antes).
3. Gatilho 2: Confirmação de reserva em aula coletiva (UC06).
4. Gatilho 3: Finalização de novo laudo de avaliação física (UC08).
5. O sistema recupera os dados de contato do aluno.
6. O sistema gera a mensagem personalizada com base no modelo (template) correspondente.
7. O sistema dispara a notificação via e-mail, SMS ou Push Notification.
8. O sistema registra a data e o tipo de notificação enviada no perfil do aluno.

### Fluxos Alternativos
** A1 — Falha no envio: **
- Caso o serviço de mensageria retorne erro, o sistema tenta realizar o reenvio após 30 minutos.
- Se a falha persistir, o erro é registrado para verificação do administrador.

** A2 — Aluno sem dados de contato: **
- Caso o cadastro do aluno não possua e-mail ou telefone válido, o sistema ignora o envio e gera um alerta no painel da recepção.

### RF Relacionados
- RF10 — Notificações
- RF03 — Controle de Pagamentos
- RF06 — Agendamento de Aulas
- RF08 — Avaliação Física

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança

### RN Relacionadas
- RN07 — Atualização automática da regularidade (Gatilho para notificações de pagamento)

## UC11 — Bloqueio por inadimplência (Alunos com mensalidade vencida há mais de 5 dias não podem entrar na academia.)

### Ator Principal
Usuário (Aluno)

### Objetivo
Bloqueio por inadimplência.

### Pré-condições
- Usuário deve possuir cadastro.

### Pós-condições
- Carregar tela com bloqueio.

### Fluxo Principal
1. O usuário loga no sistema.
2. O sistema mostra tela de bloqeuio.
3. O sistema avisa sobre a mensalidade vencida.

 

### Fluxos Alternativos
- **A1 — tela de bloqueio:**  
  O sistema exibe tela de bloqueio.

- **A2 — Conta bloqueada:**  
  O sistema impede a entrada.

### RF Relacionados
- RF01 — Validação de Status
- RF02 — Cálculo de Atraso
- RF03 — Exibição de Alerta
- RF04 — Redirecionamento de Pagamento (Opcional, mas recomendado)

### RNF Relacionados
- RNF01 — Desempenho
- RNF02 — Integração
- RNF03 — Privacidade/Usabilidade

### RN Relacionadas
- RN01 — Prazo de Tolerância
- RN02 — Liberação de Acesso
- RN03 — Exceção de Bloqueio

---------------------------------------------------------------------------------------------

## UC12 — Limite de vagas (Cada aula possui número máximo de alunos; ao atingir o limite, novos agendamentos devem ser bloqueados.)

### Ator Principal
Usuário (Aluno)

### Objetivo
Limitar vagas.

### Pré-condições
- Sistema deve estar com as vagas máximas.

### Pós-condições
- Erro ao carregar novos afendamentos.

### Fluxo Principal
1. O usuário tenta agendar.
2. O sistema mostra limite de vagas.
3. O sistema avisa que não é possivel agendar.

 

### Fluxos Alternativos
- **A1 — Aviso de limite atingido:**  
  O sistema exibe aviso de limite máximo.

- **A2 — Erro ao agendar:**  
  O sistema impede agendar.

### RF Relacionados
- RF01 — Contagem de Vagas
- RF02 — Exibição de Disponibilidade
- RF03 — Bloqueio de Agendamento
- RF04 — Fila de Espera

### RNF Relacionados
- RNF01 — Controle de Concorrência
- RNF02 — Atualização em Tempo Real
- RNF03 — Usabilidade

### RN Relacionadas
- RN01 — Limites Personalizados
- RN02 — Liberação por Cancelamento
- RN03 — Zero Overbooking

---------------------------------------------------------------------------------------------

## UC13 — Cancelamento de agendamento (O aluno pode cancelar uma reserva até 1 hora antes do início da aula.)

### Ator Principal
Usuário (Aluno)

### Objetivo
Permitir o cancelamento do agendamento de uma aula, liberando a vaga no sistema.

### Pré-condições
- O usuário deve estar logado no sistema.
- O usuário deve possuir um agendamento ativo para uma aula futura.

### Pós-condições
- O status da reserva passa a ser "Cancelado".
- A vaga correspondente é disponibilizada novamente no sistema.

### Fluxo Principal
1. O usuário acessa a tela de "Meus Agendamentos".

2. O sistema exibe a lista de aulas reservadas pelo usuário.

3. O usuário seleciona a aula desejada e clica na opção "Cancelar Reserva".

4. O sistema valida o horário atual em relação ao horário de início da aula (verificando se há pelo menos 1 hora de antecedência).

5. O sistema solicita a confirmação do cancelamento.

6. O usuário confirma a ação.

7. O sistema efetiva o cancelamento, atualiza o número de vagas disponíveis para a aula e exibe uma mensagem de sucesso.

 

### Fluxos Alternativos
- **A1 — Tentativa de cancelamento fora do prazo (Menos de 1 hora):**  
  No passo 4, se o sistema identificar que falta menos de 1 hora para o início da aula, ele bloqueia a ação e exibe a mensagem: "Não é possível cancelar. O prazo limite de 1 hora de antecedência foi ultrapassado." O fluxo é encerrado.

- **A2 — Desistência do cancelamento:**  
 No passo 6, o usuário decide não confirmar a ação (clica em "Voltar" ou "Não"). O sistema fecha o aviso e o agendamento permanece ativo.

### RF Relacionados
- RF01 — Validação de Tempo
- RF02 — Alteração de Status
- RF03 — Atualização de Vagas

### RNF Relacionados
- RNF01 — Processamento em Tempo Real
- RNF02 — Feedback Visual


### RN Relacionadas
- RN01 — Prazo Limite para Cancelamento
- RN02 — Destino da Vaga

---------------------------------------------------------------------------------------------

## UC14 — Pagamento parcial (Não é permitido pagamento parcial da mensalidade; o valor deve ser integral.)

### Ator Principal
Usuário (Aluno ou Recepcionista)

### Objetivo
Realizar o pagamento da mensalidade garantindo a cobrança do valor integral, bloqueando qualquer tentativa de pagamento parcial.

### Pré-condições
- O usuário deve ter uma fatura/mensalidade com status "Em aberto" ou "Vencida".
- O sistema de pagamentos (gateway) deve estar ativo e integrado.

### Pós-condições
- A mensalidade é quitada em sua totalidade (status "Pago") ou a transação é cancelada/negada.

### Fluxo Principal
1. O usuário acessa a área de pagamentos do sistema.

2. O sistema exibe a fatura em aberto com o valor total travado (sem opção de edição).

3. O usuário seleciona a forma de pagamento (Cartão, PIX, Boleto, etc.).

4. O sistema envia a requisição de cobrança para o gateway de pagamento com o valor exato e integral da fatura.

5. O pagamento é aprovado.

6. O sistema atualiza o status da fatura para "Pago" e emite o comprovante.

 

### Fluxos Alternativos
- **A1 — Tentativa de edição de valor (Bloqueio)**  
  No passo 2 ou 3, se o usuário tentar alterar o valor a ser pago (ex: inserindo um valor menor no caixa presencial ou tentando manipular o link de pagamento online), o sistema bloqueia a ação imediatamente e exibe o erro: "Não é permitido pagamento parcial. O valor deve ser integral."

- **A2 - Saldo insuficiente no cartão**  
 No passo 4, se o cartão do usuário não tiver limite para o valor total da mensalidade, o gateway recusa a transação. O sistema não tenta cobrar um valor menor, apenas exibe a mensagem de "Pagamento recusado" e mantém a fatura "Em aberto".

### RF Relacionados
- RF01 — Bloqueio de Edição
- RF02 — Validação de Transação
- RF03 — Geração de Cobrança Fechada

### RNF Relacionados
- RNF01 — Segurança de API
- RNF02 — Clareza de Interface (Usabilidade)


### RN Relacionadas
- RN01 — Pagamento Exclusivamente Integral
- RN02 — Incidência de Juros (Acréscimos)

---------------------------------------------------------------------------------------------

## UC15 — Avaliação física (Uma avaliação física só pode ser realizada se o aluno estiver ativo e regular.)

### Ator Principal
Usuário (Professor ou Avaliador)

### Objetivo
Realizar o registro da avaliação física de um aluno, garantindo que ele esteja ativo e sem pendências.

### Pré-condições
- O usuário (avaliador) deve estar logado no sistema.
- O aluno deve estar previamente cadastrado.

### Pós-condições
- A avaliação física é salva no histórico do aluno.

### Fluxo Principal
1. O avaliador acessa a área de avaliações físicas.

2. O sistema exibe o campo de busca de alunos.

3. O avaliador busca pelo aluno desejado (por nome, CPF ou matrícula).

4. O sistema valida o status do aluno como "Ativo" e "Regular" (mensalidades em dia).

5. O sistema libera o formulário de avaliação física.

6. O avaliador preenche os dados da avaliação e clica em salvar.

7. O sistema registra a avaliação e exibe mensagem de sucesso.

 

### Fluxos Alternativos
- **A1 — Aluno irregular ou inativo (Bloqueio)**  
  No passo 4, se o sistema identificar que o aluno possui mensalidades em atraso ou está com a matrícula inativa, ele bloqueia o acesso ao formulário e exibe a mensagem: "Aluno irregular. Não é possível iniciar a avaliação física."

- **A2 — Cancelamento da avaliação**  
  No passo 6, se o avaliador decidir cancelar a operação, o sistema descarta as informações preenchidas e retorna à tela de busca sem salvar a avaliação.

### RF Relacionados
- RF01 — Validação de Status do Aluno
- RF02 — Busca de Alunos
- RF03 — Registro de Avaliação Física

### RNF Relacionados
- RNF01 — Integração com Módulo Financeiro e Cadastral
- RNF02 — Controle de Acesso (Perfil Avaliador)

### RN Relacionadas
- RN01 — Bloqueio por Irregularidade Cadastral/Financeira
- RN02 — Exclusividade de Registro

---------------------------------------------------------------------------------------------

## UC16 — Acesso restrito por perfil (Cada perfil possui permissão específica: Recepcionista: matrículas e pagamentos / Instrutor: aulas e avaliações / Gerente: relatórios e configuração de planos)

### Ator Principal
Usuário (Recepcionista, Instrutor ou Gerente)

### Objetivo
Garantir que cada usuário acesse apenas os módulos e funcionalidades compatíveis com o seu cargo e nível de permissão no sistema.

### Pré-condições
- O usuário deve possuir uma conta ativa com um perfil de acesso definido.
- O sistema de autenticação deve estar operante.

### Pós-condições
- O sistema carrega a interface (menus e botões) exclusivamente com as opções permitidas para o perfil do usuário logado.

### Fluxo Principal
1. O usuário insere suas credenciais na tela de login e aciona o botão de entrar.

2. O sistema autentica o usuário e identifica o seu perfil (Recepcionista, Instrutor ou Gerente).

3. O sistema carrega o painel principal (dashboard) customizado.

4. O sistema exibe no menu apenas os módulos autorizados para aquele perfil.

5. O usuário navega e utiliza as funcionalidades liberadas para o seu cargo de forma segura.

 

### Fluxos Alternativos
- **A1 — Tentativa de acesso a URL restrita (Bloqueio)**  
  No passo 5, se o usuário tentar acessar diretamente pelo navegador um link de um módulo não permitido para o seu perfil (ex: um instrutor forçando a URL da tela de pagamentos), o sistema bloqueia o acesso, exibe a mensagem de erro: "Acesso negado: você não tem permissão para visualizar esta página" e o redireciona para a tela inicial.

- **A2 — Usuário sem perfil definido**  
  No passo 2, se o sistema identificar que o usuário logado por algum erro não possui um perfil atribuído no banco de dados, ele exibe o alerta: "Erro de permissão. Contate o gerente do sistema." e desloga o usuário.

### RF Relacionados
- RF01 — Autenticação e Identificação de Perfil
- RF02 — Renderização Dinâmica de Menus e Telas
- RF03 — Proteção de Rotas/URLs (Controle de Acesso)

### RNF Relacionados
- RNF01 — Segurança de Autorização (Níveis de Acesso)
- RNF02 — Usabilidade (Ocultar funcionalidades restritas da interface)

### RN Relacionadas
- RN01 — Permissões de Recepcionista (Matrículas e Pagamentos)
- RN02 — Permissões de Instrutor (Aulas e Avaliações)
- RN03 — Permissões de Gerente (Relatórios e Configuração de Planos)

---------------------------------------------------------------------------------------------

## UC17 — Atualização automática da regularidade (Ao registrar um pagamento, o sistema deve atualizar imediatamente a situação do aluno.)

### Ator Principal
Sistema (Módulo Financeiro / Gateway de Pagamento)

### Objetivo
Garantir que o status do aluno seja atualizado para regular de forma automática e imediata assim que um pagamento for confirmado, removendo quaisquer bloqueios.

### Pré-condições
- O aluno deve estar com o status "Irregular" ou "Bloqueado" devido a atraso.
- O pagamento da mensalidade pendente deve ter sido aprovado ou baixado no sistema.

### Pós-condições
- O status cadastral do aluno é alterado para "Regular".
- O acesso do aluno à catraca e ao aplicativo é imediatamente restabelecido.

### Fluxo Principal
1. O sistema (ou o gateway de pagamento) confirma a quitação integral da mensalidade do aluno.

2. O sistema localiza automaticamente o cadastro do aluno vinculado àquela fatura.

3. O sistema altera o status da matrícula de "Irregular/Bloqueado" para "Regular/Ativo".

4. O sistema registra a data e a hora da regularização no histórico do aluno.

5. O sistema envia imediatamente o comando de liberação para a catraca física e desbloqueia as funções do aplicativo (como agendamento de aulas).

 

### Fluxos Alternativos
- **A1 — Compensação pendente (Ex: Boleto Bancário)**  
  Se o pagamento for realizado por métodos que não têm baixa instantânea (como boleto), o sistema mantém o status de "Irregular" até receber o retorno positivo da rede bancária (webhook). A atualização automática da regularidade só ocorre no momento em que o sistema recebe esse aviso oficial.

- **A2 — Falha na sincronização com a catraca**  
  No passo 5, se o sistema atualizar o banco de dados para "Regular", mas houver uma falha de rede que impeça a comunicação com a catraca física da academia, o sistema gera um alerta visual no painel da recepção para que a liberação de entrada daquele dia seja feita de forma manual pelo funcionário.

### RF Relacionados
- RF01 — Processamento de Confirmação de Pagamento (Baixa Automática)
- RF02 — Atualização de Status de Matrícula
- RF03 — Integração e Comunicação com Controle de Acesso (Catraca/App)

### RNF Relacionados
- RNF01 — Desempenho e Processamento em Tempo Real (Instantâneo para Cartão/PIX)
- RNF02 — Confiabilidade (Tratamento de falhas na integração de rede)

### RN Relacionadas
- RN01 — Liberação Imediata Pós-Pagamento
- RN02 — Manutenção de Bloqueio até Compensação Confirmada

---------------------------------------------------------------------------------------------

## UC18 — Usabilidade (A interface deve ser intuitiva e responsiva, adequada para desktop e mobile.)

### Ator Principal
Usuário (Qualquer perfil: Aluno, Recepcionista, Instrutor ou Gerente)

### Objetivo
Navegar e interagir com o sistema de forma clara, eficiente e sem quebras de layout, independentemente do dispositivo utilizado (computador, tablet ou smartphone).

### Pré-condições
- O sistema deve estar acessível via navegador web ou aplicativo.
- O dispositivo do usuário deve possuir conexão com a internet e um navegador/sistema operacional compatível.

### Pós-condições
- O usuário conclui suas tarefas com sucesso, visualizando a interface adaptada perfeitamente à resolução de sua tela.

### Fluxo Principal
1. O usuário acessa o sistema ou aplicativo através de um dispositivo (ex: smartphone ou desktop).

2. O sistema detecta automaticamente a resolução, orientação e o tamanho da tela do dispositivo.

3. O sistema renderiza a interface ajustando os elementos visuais de forma dinâmica (ex: menus viram "hambúrguer" no celular, botões ficam com área de toque maior, fontes continuam legíveis).

4. O usuário interage com o sistema (toca/clica em botões, preenche formulários, rola a tela) de forma fluida e intuitiva.

5. O sistema responde às ações do usuário fornecendo feedback visual imediato e claro (ex: botões mudam de cor ao serem clicados, mensagens de sucesso ou erro aparecem na tela).

 

### Fluxos Alternativos
- **A1 — Mudança de orientação da tela (Mobile)**  
  No passo 4, se o usuário rotacionar o dispositivo móvel (de retrato para paisagem ou vice-versa), o sistema reajusta o layout da tela automaticamente em tempo real, reorganizando os elementos sem perder os dados que já foram preenchidos em formulários.

- **A2 — Tempo de carregamento (Feedback visual)**  
  No passo 5, se o processamento de uma ação (como buscar uma lista de alunos) demorar mais que o normal devido à rede, o sistema exibe imediatamente um indicador de carregamento (ex: *spinner* ou barra de progresso) e desabilita o botão clicado para evitar que o usuário clique várias vezes por engano.

### RF Relacionados
- RF01 — Detecção Automática de Dispositivo e Resolução
- RF02 — Adaptação Dinâmica de Layout (Grid Responsivo)
- RF03 — Geração de Feedbacks Visuais (Alertas, Loadings, Modais)

### RNF Relacionados
- RNF01 — Usabilidade e Experiência do Usuário (UX/UI intuitiva)
- RNF02 — Acessibilidade (Contraste de cores, tamanho de fontes e áreas de clique)
- RNF03 — Compatibilidade Multiplataforma e Cross-browser (iOS, Android, Chrome, Safari, etc.)

### RN Relacionadas
- RN01 — Padronização Visual (Uso obrigatório das cores, tipografia e identidade visual da academia em todas as telas)

---------------------------------------------------------------------------------------------

## UC19 — Escalabilidade (O sistema deve ser capaz de suportar múltiplas unidades da rede FitPass.)

### Ator Principal
Usuário (Aluno ou Gerente de Rede)

### Objetivo
Permitir a interação, o gerenciamento e o acesso a diferentes unidades físicas da academia na mesma plataforma, garantindo que o sistema suporte o aumento de dados e acessos sem lentidão.

### Pré-condições
- A infraestrutura do sistema deve estar hospedada em um ambiente de nuvem escalável.
- As diferentes unidades da rede devem estar previamente cadastradas no sistema.

### Pós-condições
- As ações (agendamentos, matrículas, pagamentos) são registradas e separadas corretamente por unidade no banco de dados.

### Fluxo Principal
1. O usuário acessa o aplicativo ou painel administrativo.

2. O sistema exibe um seletor solicitando que o usuário escolha a unidade de interesse (ex: "FitPass Centro" ou "FitPass Zona Sul").

3. O usuário seleciona a unidade desejada.

4. O sistema filtra e carrega apenas as informações daquela unidade (quadro de horários, limite de vagas da sala, professores disponíveis).

5. O usuário realiza a sua ação no sistema (ex: agendar uma aula ou tirar um relatório financeiro).

6. O sistema processa a requisição, salva os dados atrelados ao identificador (ID) daquela filial específica e exibe a mensagem de sucesso.

 

### Fluxos Alternativos
- **A1 — Visão Global (Gerente de Rede)**  
  No passo 2, se o usuário logado for um "Gerente Geral/Dono", o sistema oferece a opção "Todas as Unidades". Ao selecionar essa opção, o sistema consolida os dados de toda a rede FitPass e exibe um painel de resultados e relatórios unificados.

- **A2 — Pico de acessos simultâneos (Auto-scaling)**  
  Durante o uso do sistema (ex: horário de pico às 18h em todas as unidades)

---------------------------------------------------------------------------------------------

## UC20 — Integração (A comunicação com o sistema de catraca deve ocorrer via API REST utilizando JSON.)

### Ator Principal
Sistema (Backend FitPass) e Sistema de Catraca (Hardware)

### Objetivo
Validar e registrar a entrada física do aluno na academia de forma rápida e segura, através de uma comunicação padronizada entre o software e o hardware da catraca.

### Pré-condições
- A catraca deve estar conectada à internet/rede local e configurada com a chave de autenticação da API.
- O servidor do sistema (backend) deve estar online e apto a receber requisições HTTP.

### Pós-condições
- A catraca é destravada (ou mantida bloqueada) e o log de acesso do aluno é gravado no banco de dados.

### Fluxo Principal
1. O aluno interage com a catraca física (aproxima a biometria, cartão RFID ou lê o QR Code do app).

2. O hardware da catraca monta um pacote de dados e envia uma requisição via **API REST** para o servidor da academia, enviando as informações do aluno em formato **JSON** (ex: `{"id_aluno": "12345", "unidade": "01"}`).

3. O sistema FitPass recebe o JSON, processa a identificação e consulta o status financeiro e cadastral do aluno.

4. O sistema gera uma resposta também em formato JSON (ex: `{"status": "liberado", "mensagem": "Bem-vindo"}`) e a devolve para a catraca.

5. A catraca recebe a resposta JSON, interpreta o comando de "liberado", acende a luz verde e destrava o braço giratório.

6. O aluno passa pela catraca e o sistema registra o horário exato da entrada (check-in físico).

 

### Fluxos Alternativos
- **A1 — Acesso Negado (Bloqueio retornado via API)**  
  No passo 4, se o sistema identificar que o aluno está com a mensalidade atrasada (UC11) ou inativo, ele retorna um JSON com comando de bloqueio (ex: `{"status": "bloqueado", "motivo": "inadimplencia"}`). A catraca interpreta o comando, acende a luz vermelha, emite um bipe de erro e mantém o braço travado.

- **A2 — Falha de comunicação (Timeout da API)**  
  No passo 2, se a internet da academia cair ou o servidor estiver fora do ar, a catraca não recebe o retorno do JSON dentro do tempo limite (ex: 3 segundos). A catraca exibe "Erro de Conexão" no visor e a entrada precisa ser tratada manualmente pela recepcionista.

### RF Relacionados
- RF01 — Recepção e Processamento de Requisições de Hardware
- RF02 — Validação de Acesso Físico
- RF03 — Geração e Armazenamento de Logs de Entrada/Saída

### RNF Relacionados
- RNF01 — Arquitetura de Integração (Obrigatório o uso de API REST e formato JSON)
- RNF02 — Baixa Latência (O ciclo de envio e resposta da API deve ocorrer em menos de 1 segundo para evitar filas)
- RNF03 — Segurança de Endpoint (A API deve exigir autenticação via Token ou API Key para aceitar requisições da catraca)

### RN Relacionadas
- RN01 — Padronização de Dados (Qualquer catraca de diferentes fabricantes comprada pela rede FitPass deve ser capaz de enviar e receber comandos no padrão JSON estipulado pelo sistema)
- RN02 — Registro de Frequência (A abertura da catraca via API conta automaticamente como presença confirmada do aluno no dia)

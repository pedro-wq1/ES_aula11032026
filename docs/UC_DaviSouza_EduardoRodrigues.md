## UC01 --- Realizar Login

### Ator Principal

Usuário

### Objetivo

Permitir que o usuário acesse o sistema.

### Pré-condições

-   Usuário deve possuir cadastro ativo.

### Pós-condições

-   Sessão iniciada com sucesso.

### Fluxo Principal

1.  O usuário informa e-mail e senha.
2.  O sistema valida as credenciais.
3.  O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos

-   **A1 --- Senha incorreta:**\
    O sistema exibe mensagem de erro.

-   **A2 --- Conta bloqueada:**\
    O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados

-   RF01

### RNF Relacionados

-   RNF02
-   RNF04

### RN Relacionadas

-   RN06

## UC02 --- Cadastrar Aluno

### Ator Principal

Recepcionista

### Objetivo

Registrar um novo aluno no sistema.

### Pré-condições

-   Recepcionista deve estar autenticado no sistema.

### Pós-condições

-   Aluno cadastrado no sistema.

### Fluxo Principal

1.  O recepcionista acessa a opção de cadastro de alunos.
2.  O sistema exibe o formulário de cadastro.
3.  O recepcionista preenche os dados pessoais, contato e endereço.
4.  O recepcionista seleciona um plano.
5.  O sistema salva o cadastro do aluno.

### Fluxos Alternativos

-   **A1 --- Dados incompletos:**\
    O sistema solicita preenchimento dos campos obrigatórios.

### RF Relacionados

-   RF01

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN06

## UC03 --- Atualizar Dados do Aluno

### Ator Principal

Recepcionista

### Objetivo

Permitir atualizar informações cadastrais do aluno.

### Pré-condições

-   Aluno deve estar cadastrado no sistema.

### Pós-condições

-   Dados atualizados no sistema.

### Fluxo Principal

1.  O recepcionista busca o aluno pelo nome ou CPF.
2.  O sistema exibe os dados cadastrados.
3.  O recepcionista altera as informações necessárias.
4.  O sistema salva as alterações.

### Fluxos Alternativos

-   **A1 --- Aluno não encontrado:**\
    O sistema informa que não existe cadastro.

### RF Relacionados

-   RF01

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN06

## UC04 --- Criar Plano

### Ator Principal

Gerente

### Objetivo

Criar novos planos de academia.

### Pré-condições

-   Gerente autenticado no sistema.

### Pós-condições

-   Novo plano disponível para contratação.

### Fluxo Principal

1.  O gerente acessa a área de planos.
2.  O sistema exibe formulário de criação.
3.  O gerente informa nome, valor e duração do plano.
4.  O sistema registra o plano.

### Fluxos Alternativos

-   **A1 --- Dados inválidos:**\
    O sistema solicita correção dos dados.

### RF Relacionados

-   RF02

### RNF Relacionados

-   RNF04
-   RNF05

### RN Relacionadas

-   RN06

## UC05 --- Editar Plano

### Ator Principal

Gerente

### Objetivo

Modificar informações de um plano existente.

### Pré-condições

-   Plano cadastrado no sistema.

### Pós-condições

-   Plano atualizado.

### Fluxo Principal

1.  O gerente seleciona um plano existente.
2.  O sistema exibe os dados do plano.
3.  O gerente altera as informações.
4.  O sistema salva as alterações.

### Fluxos Alternativos

-   **A1 --- Plano inexistente:**\
    O sistema informa erro.

### RF Relacionados

-   RF02

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN06

## UC06 --- Registrar Pagamento

### Ator Principal

Recepcionista

### Objetivo

Registrar pagamento da mensalidade.

### Pré-condições

-   Aluno deve possuir plano ativo.

### Pós-condições

-   Pagamento registrado.

### Fluxo Principal

1.  O recepcionista seleciona o aluno.
2.  O sistema exibe mensalidade pendente.
3.  O recepcionista registra o pagamento.
4.  O sistema atualiza a situação do aluno.

### Fluxos Alternativos

-   **A1 --- Valor incorreto:**\
    O sistema impede registro.

### RF Relacionados

-   RF03

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN04
-   RN07

## UC07 --- Verificar Regularidade do Aluno

### Ator Principal

Sistema

### Objetivo

Verificar se o aluno está com pagamentos em dia.

### Pré-condições

-   Aluno cadastrado.

### Pós-condições

-   Status de regularidade atualizado.

### Fluxo Principal

1.  O sistema consulta o histórico de pagamentos.
2.  O sistema verifica a data de vencimento.
3.  O sistema define o status do aluno.

### Fluxos Alternativos

-   **A1 --- Mensalidade vencida:**\
    O sistema marca o aluno como inadimplente.

### RF Relacionados

-   RF04

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN01

## UC08 --- Validar Entrada na Academia

### Ator Principal

Aluno

### Objetivo

Permitir entrada utilizando RFID.

### Pré-condições

-   Aluno deve possuir cartão RFID.

### Pós-condições

-   Entrada liberada ou negada.

### Fluxo Principal

1.  O aluno aproxima o cartão RFID da catraca.
2.  O sistema verifica o cadastro.
3.  O sistema verifica a regularidade do aluno.
4.  A catraca é liberada.

### Fluxos Alternativos

-   **A1 --- Aluno inadimplente:**\
    A catraca permanece bloqueada.

### RF Relacionados

-   RF05

### RNF Relacionados

-   RNF03
-   RNF06

### RN Relacionadas

-   RN01

## UC09 --- Visualizar Aulas Disponíveis

### Ator Principal

Aluno

### Objetivo

Permitir consulta de horários de aulas.

### Pré-condições

-   Aluno autenticado no sistema.

### Pós-condições

-   Lista de aulas exibida.

### Fluxo Principal

1.  O aluno acessa a área de aulas.
2.  O sistema lista horários disponíveis.
3.  O aluno escolhe uma aula.

### Fluxos Alternativos

-   **A1 --- Nenhuma aula disponível:**\
    O sistema informa indisponibilidade.

### RF Relacionados

-   RF06

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN02

## UC10 --- Agendar Aula

### Ator Principal

Aluno

### Objetivo

Reservar vaga em uma aula.

### Pré-condições

-   Aula disponível.

### Pós-condições

-   Reserva registrada.

### Fluxo Principal

1.  O aluno seleciona uma aula.
2.  O sistema verifica disponibilidade.
3.  O sistema confirma o agendamento.

### Fluxos Alternativos

-   **A1 --- Aula lotada:**\
    O sistema bloqueia o agendamento.

### RF Relacionados

-   RF06

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN02

## UC11 --- Cancelar Agendamento

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno cancele uma reserva de aula.

### Pré-condições

-   O aluno deve possuir um agendamento ativo.

### Pós-condições

-   Reserva cancelada no sistema.

### Fluxo Principal

1.  O aluno acessa a lista de agendamentos.
2.  O aluno seleciona a aula agendada.
3.  O aluno escolhe cancelar.
4.  O sistema remove a reserva.

### Fluxos Alternativos

-   **A1 --- Prazo expirado:**\
    O sistema impede o cancelamento.

### RF Relacionados

-   RF06

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN03

## UC12 --- Registrar Presença em Aula

### Ator Principal

Instrutor

### Objetivo

Registrar presença dos alunos nas aulas.

### Pré-condições

-   Aula em andamento.

### Pós-condições

-   Presença registrada.

### Fluxo Principal

1.  O instrutor abre a lista da aula.
2.  O instrutor marca presença dos alunos.
3.  O sistema salva os registros.

### Fluxos Alternativos

-   **A1 --- Aluno não inscrito:**\
    O sistema impede registro.

### RF Relacionados

-   RF07

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN06

## UC13 --- Registrar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar dados físicos do aluno.

### Pré-condições

-   Aluno ativo.

### Pós-condições

-   Avaliação registrada.

### Fluxo Principal

1.  O instrutor seleciona o aluno.
2.  O instrutor registra peso, IMC e percentual de gordura.
3.  O sistema salva os dados.

### Fluxos Alternativos

-   **A1 --- Aluno irregular:**\
    O sistema impede avaliação.

### RF Relacionados

-   RF08

### RNF Relacionados

-   RNF04

### RN Relacionadas

-   RN05

## UC14 --- Anexar Arquivo à Avaliação

### Ator Principal

Instrutor

### Objetivo

Adicionar documentos ou imagens à avaliação física.

### Pré-condições

-   Avaliação existente.

### Pós-condições

-   Arquivo anexado.

### Fluxo Principal

1.  O instrutor acessa avaliação.
2.  O instrutor seleciona arquivo.
3.  O sistema salva o anexo.

### Fluxos Alternativos

-   **A1 --- Arquivo inválido:**\
    O sistema rejeita upload.

### RF Relacionados

-   RF08

### RNF Relacionados

-   RNF02

### RN Relacionadas

-   RN06

## UC15 --- Gerar Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Visualizar alunos inadimplentes.

### Pré-condições

-   Gerente autenticado.

### Pós-condições

-   Relatório exibido.

### Fluxo Principal

1.  O gerente acessa relatórios.
2.  O gerente seleciona inadimplência.
3.  O sistema gera relatório.

### Fluxos Alternativos

-   **A1 --- Sem dados:**\
    O sistema informa ausência de registros.

### RF Relacionados

-   RF09

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN01

## UC16 --- Gerar Relatório de Alunos Ativos

### Ator Principal

Gerente

### Objetivo

Listar alunos com plano ativo.

### Pré-condições

-   Gerente autenticado.

### Pós-condições

-   Relatório gerado.

### Fluxo Principal

1.  O gerente seleciona relatório de alunos ativos.
2.  O sistema gera a lista.

### Fluxos Alternativos

-   **A1 --- Nenhum aluno ativo:**\
    O sistema informa.

### RF Relacionados

-   RF09

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN06

## UC17 --- Gerar Relatório de Acessos

### Ator Principal

Gerente

### Objetivo

Consultar histórico de entradas na academia.

### Pré-condições

-   Registros de acesso existentes.

### Pós-condições

-   Relatório exibido.

### Fluxo Principal

1.  O gerente seleciona relatório de acessos.
2.  O sistema consulta histórico.
3.  O sistema exibe dados.

### Fluxos Alternativos

-   **A1 --- Sem registros:**\
    O sistema informa.

### RF Relacionados

-   RF09

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN06

## UC18 --- Gerar Relatório de Ocupação de Aulas

### Ator Principal

Gerente

### Objetivo

Analisar participação nas aulas.

### Pré-condições

-   Aulas cadastradas.

### Pós-condições

-   Relatório exibido.

### Fluxo Principal

1.  O gerente seleciona relatório de ocupação.
2.  O sistema analisa presenças.
3.  O sistema gera relatório.

### Fluxos Alternativos

-   **A1 --- Nenhuma aula registrada:**\
    O sistema informa.

### RF Relacionados

-   RF09

### RNF Relacionados

-   RNF05

### RN Relacionadas

-   RN02

## UC19 --- Enviar Notificação de Vencimento

### Ator Principal

Sistema

### Objetivo

Avisar aluno sobre vencimento da mensalidade.

### Pré-condições

-   Aluno com mensalidade ativa.

### Pós-condições

-   Notificação enviada.

### Fluxo Principal

1.  O sistema identifica mensalidade próxima do vencimento.
2.  O sistema envia notificação.

### Fluxos Alternativos

-   **A1 --- Falha no envio:**\
    O sistema registra erro.

### RF Relacionados

-   RF10

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN07

## UC20 --- Enviar Confirmação de Agendamento

### Ator Principal

Sistema

### Objetivo

Confirmar reserva de aula ao aluno.

### Pré-condições

-   Agendamento realizado.

### Pós-condições

-   Notificação enviada.

### Fluxo Principal

1.  O sistema registra o agendamento.
2.  O sistema envia confirmação.

### Fluxos Alternativos

-   **A1 --- Falha no envio:**\
    O sistema registra erro.

### RF Relacionados

-   RF10

### RNF Relacionados

-   RNF03

### RN Relacionadas

-   RN02

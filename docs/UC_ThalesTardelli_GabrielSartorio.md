## UC01 — Realizar Login

### Ator Principal: 
- Usuário (Aluno, Recepcionista, Instrutor ou Gerente)

### Objetivo: 
Permitir acesso ao sistema de acordo com o perfil.

### Pré-condições: 
- Usuário cadastrado e ativo.

### Pós-condições: 
Sessão iniciada.

### Fluxo Principal: 
1. Usuário insere e-mail e senha; 
2. Sistema valida credenciais; 
3. Sistema redireciona conforme perfil (RN06).

### Requisitos Relacionados 
RF: RF01 
RNF: RNF02 
RN: RN06

---

## UC02 — Cadastrar Aluno

### Ator Principal: 
- Recepcionista

### Objetivo: 
Registrar novo aluno e vincular plano.

### Pré-condições: 
- Recepcionista logado.

### Pós-condições: 
- Aluno salvo no banco de dados.

### Fluxo Principal: 
1. Informar dados pessoais; 
2. Selecionar plano (RF02); 
3. Vincular tag RFID; 
4. Salvar.

### Requisitos Relacionados 
RF: RF01, RF02
RNF: RNF03, RNF04
RN: RN06

---

## UC03 — Gerenciar Planos (Criar/Editar)

### Ator Principal: 
- Gerente

### Objetivo: 
Configurar as opções de planos da academia.

### Pré-condições: 
- Gerente logado.

### Pós-condições: 
- Plano disponível para venda.

### Fluxo Principal: 
1. Definir nome, valor e duração; 
2. Salvar configuração.

### Requisitos Relacionados 
RF: RF02 
RNF: RNF04 
RN: RN06

---

## UC04 — Registrar Pagamento (Presencial)

### Ator Principal: 
- Recepcionista

### Objetivo: 
Quitar débitos de mensalidade.

### Pré-condições: 
Aluno selecionado.

### Pós-condições: 
Status financeiro atualizado para "Regular".

### Fluxo Principal: 
1. Selecionar parcela; 
2. Escolher forma de pagamento; 
3. Confirmar valor integral (RN04); 
4. Sistema atualiza status (RN07).

### Requisitos Relacionados 
RF: RF03, RF04 
RNF: RNF03 
RN: RN04, RN07

---

## UC05 — Gerar Cobrança Online

### Ator Principal: 
- Recepcionista / Sistema

### Objetivo: 
Emitir boletos ou links de pagamento.

### Pré-condições: 
- Aluno com plano ativo.

### Pós-condições: 
- Cobrança enviada ao aluno.

### Fluxo Principal: 
1. Sistema gera fatura mensal; 
2. Disponibiliza link/boleto.

### Requisitos Relacionados 
RF: RF03 
RNF: RNF05 
RN: RN04

---

## UC06 — Validar Acesso na Catraca

### Ator Principal: 
- Sistema de Catraca (API)

### Objetivo: 
Liberar entrada física.

### Pré-condições: 
- Aluno aproximar RFID.

### Pós-condições: 
- Acesso liberado ou negado.

### Fluxo Principal: 
1. Leitura do RFID; 
2. Sistema verifica carência de 5 dias (RN01); 
3. Libera giro se regular.

### Requisitos Relacionados 
RF: RF04, RF05 
RNF: RNF03, RNF06 
RN: RN01

---

## UC07 — Visualizar Grade de Aulas

### Ator Principal: 
- Aluno

### Objetivo: 
Ver horários disponíveis.

### Pré-condições: 
- Aluno logado.

### Pós-condições: 
Lista de aulas exibida.

### Fluxo Principal: 
1. Acessar menu "Aulas"; 
2. Filtrar por data/modalidade.

### Requisitos Relacionados 
RF: RF06 
RNF: RNF04 
RN: -

--- 

## UC08 — Realizar Agendamento de Aula

### Ator Principal: 
- Aluno

### Objetivo: 
Reservar vaga em aula coletiva.

### Pré-condições: 
- Aluno regular e aula com vagas.

### Pós-condições: 
- Vaga reservada.

### Fluxo Principal: 
1. Selecionar aula; 
2. Confirmar reserva; 
3. Sistema valida limite (RN02).

### Requisitos Relacionados:

RF: RF06 
RNF: RNF04
RN: RN02

---

## UC09 — Cancelar Agendamento

### Ator Principal: 
- Aluno

### Objetivo: 
Desistir da vaga reservada.

### Pré-condições: 
- Prazo de 1 hora de antecedência (RN03).

### Pós-condições: 
- Vaga liberada para outros.

### Fluxo Principal: 
1. Selecionar aula agendada; 
2. Clicar em cancelar; 
3. Sistema valida tempo limite.

### Requisitos Relacionados:

RF: RF06 
RNF: RNF03 
RN: RN03

--- 

## UC10 — Lançar Presença em Aula

### Ator Principal: 
- Instrutor

### Objetivo: 
Registrar quem compareceu à aula.

### Pré-condições: 
- Instrutor logado e aula iniciada.

### Pós-condições: 
- Lista de presença salva.

### Fluxo Principal: 
1. Listar alunos agendados; 
2. Marcar presença.

### Requisitos Relacionados:

RF: RF07 
RNF: RNF04 
RN: RN06

---

## UC11 — Realizar Avaliação Física

### Ator Principal: 
- Instrutor

### Objetivo: 
Registrar medidas e bioimpedância.

### Pré-condições: 
- Aluno ativo e regular (RN05).

### Pós-condições: 
- Avaliação salva e disponível para o aluno.

### Fluxo Principal: 
1. Inserir peso, IMC, gordura; 
2. Anexar arquivos; 
3. Salvar.

### Requisitos Relacionados:

RF: RF08 
RNF: RNF02 
RN: RN05, RN06

---

## UC12 — Consultar Avaliação Física

### Ator Principal: 
- Aluno

### Objetivo: 
Acompanhar evolução física.

### Pré-condições: 
- Avaliação realizada previamente.

### Pós-condições: 
- Visualização do progresso.

### Fluxo Principal: 
1. Acessar menu "Saúde"; 
2. Abrir PDF/Gráfico da avaliação.

### Requisitos Relacionados:

RF: RF08 
RNF: RNF04 
RN: -

---

## UC13 — Emitir Relatório de Inadimplência

### Ator Principal: 
- Gerente

### Objetivo: 
Identificar alunos com pagamentos atrasados.

### Pré-condições: 
- Gerente logado.

### Pós-condições: 
- Relatório gerado em tela/PDF.

### Fluxo Principal: 
1. Filtrar período; 
2. Sistema lista alunos com débito.

### Requisitos Relacionados: 

RF: RF09 
RNF: RNF03 
RN: RN06

--- 

## UC14 — Emitir Relatório de Alunos Ativos

### Ator Principal: 
- Gerente

### Objetivo: 
Saber o total de alunos pagantes.

### Pré-condições: 
- Gerente logado.

### Pós-condições: 
- Quantitativo exibido.

### Requisitos Relacionados:

RF: RF09 
RNF: RNF05 
RN: RN06

---

## UC15 — Emitir Histórico de Acessos

### Ator Principal: 
- Gerente

### Objetivo: 
Monitorar fluxo de pessoas na catraca.

### Pré-condições: 
- Gerente logado.

### Fluxo Principal: 
1. Selecionar data; 
2. Listar entradas registradas via RFID.

### Requisitos Relacionados: 

RF: RF09 
RNF: RNF03 
RN: RN06

---

## UC16 — Emitir Relatório de Ocupação de Aulas

### Ator Principal: 
- Gerente

### Objetivo: 
Analisar quais aulas são mais populares.

### Fluxo Principal: 
1. Comparar vagas vs. agendamentos.

### Requisitos Relacionados: 

RF: RF09 
RNF: RNF04 
RN: RN02

---

## UC17 — Notificar Vencimento de Mensalidade

### Ator Principal: 
- Sistema (Automático)

### Objetivo: 
Alertar o aluno antes do bloqueio.

### Fluxo Principal: 
1. Verificar data de vencimento; 
2. Enviar push/e-mail.

### Requisitos Relacionados: 

RF: RF10 
RNF: RNF05 
RN: RN01

---

## UC18 — Notificar Confirmação de Agendamento

### Ator Principal: 
- Sistema (Automático)

### Objetivo: 
Confirmar que a reserva foi feita com sucesso.

### Fluxo Principal: 
1. Após UC08, enviar notificação.

### Requisitos Relacionados: 

RF: RF10 
RNF: RNF01 
RN: -

---

## UC19 — Atualizar Cadastro de Aluno

### Ator Principal: 
- Recepcionista

### Objetivo: 
Alterar endereço ou telefone.

### Fluxo Principal: 
1. Buscar aluno; 
2. Editar campos; 
3. Salvar.

### Requisitos Relacionados: 

RF: RF01 
RNF: RNF02 
RN: RN06

---

## UC20 — Inativar Plano

### Ator Principal: 
- Gerente

### Objetivo: 
Retirar plano de circulação sem excluir histórico.

### Fluxo Principal: 
1. Selecionar plano; 
2. Marcar como "Inativo".

### Requisitos Relacionados: 

RF: RF02 
RNF: RNF03 
RN: RN06

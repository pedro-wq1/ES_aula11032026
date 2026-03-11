## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

### Ator Principal

Usuário

### Objetivo

Permitir que o usuário acesse o sistema.

### Pré-condições

- Usuário deve possuir cadastro ativo.

### Pós-condições

- Sessão iniciada com sucesso.

### Fluxo Principal

1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos

- **A1 — Senha incorreta:**
    
    O sistema exibe mensagem de erro.
    
- **A2 — Conta bloqueada:**
    
    O sistema impede o login e instrui o usuário a recuperar o acesso.
    

### RF Relacionados

- RF01, RF05

### RNF Relacionados

- RNF01, RNF02, RNF04

### RN Relacionadas

- RN01, RN06

## UC02 — Cadastrar Aluno

### Ator Principal

Recepcionista

### Objetivo

Registrar um novo aluno no sistema para permitir o acesso e cobrança.

### Pré-condições

- O sistema deve estar operacional.
- O atendente deve estar autenticado.

### Pós-condições

- Registro do aluno salvo no banco de dados.
- Plano vinculado ao perfil do aluno.

### Fluxo Principal

1. O recepcionista solicita os dados pessoais (Nome, CPF, E-mail).
2. O recepcionista seleciona o plano desejado (Mensal, Trimestral, etc.).
3. O sistema valida se o CPF já existe na base.
4. O sistema confirma a criação do cadastro.

### Fluxos Alternativos

- **A1 — CPF já cadastrado:**
O sistema alerta que o aluno já possui registro e sugere a reativação da matrícula.

### RF Relacionados

- RF01

### RNF Relacionados

- RNF02, RNF04

### RN Relacionadas

- RN06

---

## UC03 — Registrar Pagamento Presencial

### Ator Principal

Recepcionista

### Objetivo

Realizar a baixa financeira de uma mensalidade na recepção da academia.

### Pré-condições

- Aluno deve estar cadastrado.
- Existência de uma pendência financeira ou renovação.

### Pós-condições

- Status do aluno atualizado para "Regular".
- Comprovante de pagamento gerado.

### Fluxo Principal

1. O recepcionista identifica o aluno pelo nome ou CPF.
2. O sistema exibe o valor em aberto conforme o plano.
3. O recepcionista seleciona a forma de pagamento (Dinheiro, Cartão ou PIX).
4. O sistema registra a transação e atualiza a situação de acesso.

### Fluxos Alternativos

- **A1 — Pagamento Parcial:**
O sistema impede a operação conforme regra de negócio.

### RF Relacionados

- RF03, RF04

### RNF Relacionados

- RNF03

### RN Relacionadas

- RN04, RN07

---

## UC04 — Validar Acesso na Catraca

### Ator Principal

Sistema (via integração com hardware)

### Objetivo

Controlar a entrada física dos alunos nas dependências da academia.

### Pré-condições

- Aluno deve aproximar a TAG RFID da catraca.

### Pós-condições

- Catraca liberada e registro de entrada salvo.

### Fluxo Principal

1. O sistema recebe o ID da TAG via API.
2. O sistema consulta a situação financeira e o plano do aluno.
3. O sistema envia comando de "Liberar" para a catraca.
4. O sistema registra a data e hora do acesso.

### Fluxos Alternativos

- **A1 — Inadimplência (> 5 dias):**
O sistema nega o acesso e exibe mensagem "Procure a recepção".

### RF Relacionados

- RF04, RF05

### RNF Relacionados

- RNF03, RNF06

### RN Relacionadas

- RN01

---

## UC05 — Agendar Aula Coletiva

### Ator Principal

Aluno

### Objetivo

Reservar uma vaga em aulas com limite de participantes (ex: Crossfit, Dança).

### Pré-condições

- Aluno deve estar com a mensalidade em dia.
- Deve haver vagas disponíveis.

### Pós-condições

- Vaga reservada para o aluno.

### Fluxo Principal

1. O aluno acessa o aplicativo e visualiza o quadro de horários.
2. O aluno seleciona a aula desejada.
3. O sistema verifica a disponibilidade de vagas.
4. O sistema confirma o agendamento e envia notificação.

### Fluxos Alternativos

- **A1 — Aula Lotada:**
O sistema impede o agendamento e oferece opção de "Lista de Espera".

### RF Relacionados

- RF06, RF10

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN02, RN06

---

## UC06 — Realizar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar métricas corporais e evolução do aluno.

### Pré-condições

- Aluno deve estar ativo e regular.
- Instrutor deve estar autenticado.

### Pós-condições

- Relatório de avaliação gerado e disponível para o aluno.

### Fluxo Principal

1. O instrutor seleciona o aluno no sistema.
2. O instrutor insere as medidas (Peso, % de gordura, dobras cutâneas).
3. O sistema calcula automaticamente o IMC e índices de saúde.
4. O instrutor finaliza e salva a avaliação.

### Fluxos Alternativos

- **A1 — Aluno Inativo:**
O sistema bloqueia o preenchimento da avaliação.

### RF Relacionados

- RF08

### RNF Relacionados

- RNF02

### RN Relacionadas

- RN05, RN06

---

## UC07 — Emitir Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Identificar alunos com pagamentos atrasados para ações de cobrança.

### Pré-condições

- Usuário com perfil de Gerente.

### Pós-condições

- Lista de inadimplentes exibida ou exportada.

### Fluxo Principal

1. O gerente acessa o módulo de relatórios.
2. O gerente filtra o período desejado.
3. O sistema busca no banco de dados todos os alunos com mensalidade vencida.
4. O sistema gera a listagem com nome, valor e dias de atraso.

### RF Relacionados

- RF09

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

## UC08 — Criar/Editar Plano

### Ator Principal

Gerente

### Objetivo

Configurar as opções de planos que serão oferecidos aos alunos.

### Pré-condições

- Acesso com perfil administrativo.

### Pós-condições

- Plano disponível para venda na recepção.

### Fluxo Principal

1. O gerente informa o nome do plano (ex: Anual Gold).
2. O gerente define o valor, a periodicidade e as modalidades inclusas.
3. O sistema valida os campos obrigatórios.
4. O sistema salva a configuração.

### Fluxos Alternativos

- **A1 — Desativar Plano:**
O gerente marca um plano como inativo; ele deixa de ser oferecido para novos alunos, mas permanece nos contratos vigentes.

### RF Relacionados

- RF02

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

---

## UC09 — Cancelar Agendamento de Aula

### Ator Principal

Aluno

### Objetivo

Liberar a vaga em uma aula caso o aluno não possa comparecer.

### Pré-condições

- Aluno possuir reserva ativa para a aula.

### Pós-condições

- Vaga liberada para outros alunos; Notificação enviada à lista de espera.

### Fluxo Principal

1. O aluno acessa seus agendamentos no sistema.
2. O aluno solicita o cancelamento da reserva.
3. O sistema verifica se o horário atual respeita a antecedência mínima.
4. O sistema confirma o cancelamento.

### Fluxos Alternativos

- **A1 — Fora do prazo:**
O sistema impede o cancelamento e informa que a antecedência mínima é de 1 hora.

### RF Relacionados

- RF06

### RNF Relacionados

- RNF03

### RN Relacionadas

- RN03

---

## UC10 — Registrar Presença em Aula

### Ator Principal

Instrutor

### Objetivo

Confirmar a presença dos alunos agendados para controle de ocupação e métricas.

### Pré-condições

- Aula em andamento ou finalizada.

### Pós-condições

- Histórico de presença do aluno atualizado.

### Fluxo Principal

1. O instrutor acessa a lista de alunos agendados para sua aula.
2. O instrutor marca o check-box de presença para cada aluno presente.
3. O sistema salva a lista.

### Fluxos Alternativos

- **A1 — Aluno não agendado:**
O instrutor pode adicionar manualmente um aluno presente, desde que haja vaga.

### RF Relacionados

- RF07

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

---

## UC11 — Enviar Notificação de Vencimento

### Ator Principal

Sistema (Automático)

### Objetivo

Alertar o aluno sobre o vencimento próximo da mensalidade.

### Pré-condições

- Fatura vencerá em 3 dias.

### Pós-condições

- Mensagem enviada via Push ou E-mail.

### Fluxo Principal

1. O sistema varre diariamente a base de pagamentos.
2. O sistema identifica mensalidades com vencimento próximo.
3. O sistema dispara a mensagem personalizada.

### RF Relacionados

- RF10

### RNF Relacionados

- RNF01

### RN Relacionadas

- (Nenhuma relacionada)

---

## UC12 — Gerar Relatório de Alunos Ativos

### Ator Principal

Gerente

### Objetivo

Extrair o quantitativo de alunos que utilizam a unidade.

### Pré-condições

- Perfil de acesso de Gerente.

### Pós-condições

- Relatório gerado em tela ou PDF.

### Fluxo Principal

1. O gerente solicita o relatório de alunos ativos.
2. O sistema filtra todos os alunos com status "Ativo".
3. O sistema agrupa por tipo de plano.

### RF Relacionados

- RF09

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

## UC13 — Registrar Manutenção de Equipamento

### Ator Principal

Instrutor / Gerente

### Objetivo

Sinalizar que uma máquina ou acessório está impróprio para uso.

### Pré-condições

- Identificação visual de defeito no equipamento.

### Pós-condições

- Equipamento marcado como "Em Manutenção" no inventário.

### Fluxo Principal

1. O ator seleciona o equipamento na lista de patrimônio.
2. O sistema solicita a descrição do defeito.
3. O ator confirma o chamado de manutenção.
4. O sistema gera um alerta visual no painel administrativo.

### Fluxos Alternativos

- **A1 — Equipamento Crítico:**
O sistema notifica o gerente imediatamente via app.

### RF Relacionados

- (Gestão de Infraestrutura)

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

---

## UC14 — Realizar Venda de Itens (Recepção)

### Ator Principal

Recepcionista

### Objetivo

Registrar a venda de produtos (água, suplementos, camisetas) na recepção.

### Pré-condições

- Item disponível em estoque.

### Pós-condições

- Saída de estoque registrada e valor somado ao caixa do dia.

### Fluxo Principal

1. O recepcionista busca o produto pelo código ou nome.
2. O sistema informa o preço unitário.
3. O recepcionista confirma a forma de pagamento.
4. O sistema emite o recibo de venda.

### Fluxos Alternativos

- **A1 — Estoque Insuficiente:**
O sistema emite alerta mas permite a venda caso o gerente autorize manualmente.

### RF Relacionados

- RF03

### RNF Relacionados

- RNF03

### RN Relacionadas

- RN06

---

## UC15 — Suspender Matrícula (Trancamento)

### Ator Principal

Recepcionista

### Objetivo

Pausar o plano do aluno por um período determinado (ex: atestado ou viagem).

### Pré-condições

- Aluno deve estar regular.

### Pós-condições

- Acesso à catraca bloqueado temporariamente; data de renovação prorrogada.

### Fluxo Principal

1. O recepcionista acessa o contrato do aluno.
2. O recepcionista informa o motivo e a quantidade de dias da suspensão.
3. O sistema recalcula a data de validade do plano.
4. O sistema registra o histórico de trancamento.

### Fluxos Alternativos

- **A1 — Limite de trancamento excedido:**
O sistema impede a operação se o aluno já usou todos os dias permitidos no contrato.

### RF Relacionados

- RF02

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

---

## UC16 — Gerenciar Lista de Espera

### Ator Principal

Sistema (Automático)

### Objetivo

Preencher automaticamente vagas que surgem após cancelamentos de aula.

### Pré-condições

- Aula com lotação máxima atingida.
- Existência de alunos na fila de espera.

### Pós-condições

- Vaga preenchida; aluno notificado.

### Fluxo Principal

1. O sistema detecta o cancelamento de uma reserva (UC09).
2. O sistema identifica o primeiro aluno da fila de espera.
3. O sistema efetiva o agendamento para este aluno.
4. O sistema envia notificação de confirmação.

### Fluxos Alternativos

- **A1 — Fila Vazia:**
O sistema apenas libera a vaga para o público geral.

### RF Relacionados

- RF06, RF10

### RNF Relacionados

- RNF01

### RN Relacionadas

- RN02

---

## UC17 — Aplicar Cupom de Desconto

### Ator Principal

Recepcionista / Gerente

### Objetivo

Conceder descontos em campanhas de marketing ou parcerias.

### Pré-condições

- Cupom deve estar previamente cadastrado e dentro da validade.

### Pós-condições

- Valor da mensalidade atualizado com a redução.

### Fluxo Principal

1. O recepcionista inicia o processo de matrícula ou renovação.
2. O recepcionista insere o código do cupom.
3. O sistema valida as regras (validade, plano específico).
4. O sistema aplica o desconto no total.

### Fluxos Alternativos

- **A1 — Cupom Expirado:**
O sistema exibe mensagem de erro e mantém o valor original.

### RF Relacionados

- RF02, RF03

### RNF Relacionados

- RNF03

### RN Relacionadas

- RN06

---

## UC18 — Consultar Evolução de Medidas (Gráficos)

### Ator Principal

Aluno

### Objetivo

Visualizar o progresso físico comparando diferentes avaliações.

### Pré-condições

- Existência de pelo menos duas avaliações físicas registradas.

### Pós-condições

- Gráficos de desempenho exibidos em tela.

### Fluxo Principal

1. O aluno acessa a aba "Minha Evolução" no app.
2. O aluno seleciona os parâmetros (ex: Peso e % de Gordura).
3. O sistema gera um gráfico comparativo histórico.

### Fluxos Alternativos

- **A1 — Dados Insuficientes:**
O sistema informa que é necessária uma nova avaliação para gerar o gráfico.

### RF Relacionados

- RF08

### RNF Relacionados

- RNF04

### RN Relacionadas

- (Nenhuma relacionada)

---

## UC19 — Fechamento de Caixa Diário

### Ator Principal

Recepcionista

### Objetivo

Conferir os valores recebidos na unidade antes do encerramento do turno.

### Pré-condições

- Registro de pelo menos uma transação financeira no dia.

### Pós-condições

- Relatório de fechamento salvo e enviado ao gerente.

### Fluxo Principal

1. O recepcionista solicita o resumo financeiro do dia.
2. O sistema exibe o total por forma de pagamento (Dinheiro, Cartão, PIX).
3. O recepcionista confirma se os valores físicos batem com o sistema.
4. O recepcionista finaliza o caixa.

### Fluxos Alternativos

- **A1 — Divergência de Valores:**
O recepcionista insere uma observação justificando a diferença antes de salvar.

### RF Relacionados

- RF03, RF09

### RNF Relacionados

- RNF04

### RN Relacionadas

- RN06

---

## UC20 — Solicitar Aula Experimental

### Ator Principal

Usuário (Não cadastrado)

### Objetivo

Permitir que potenciais clientes conheçam a academia sem custo.

### Pré-condições

- Usuário deve fornecer dados básicos de contato.

### Pós-condições

- Liberação temporária de acesso (1 dia).

### Fluxo Principal

1. O usuário preenche o formulário de interesse no site/totem.
2. O sistema valida o e-mail/telefone.
3. O sistema gera um QR Code ou senha temporária para a catraca.
4. O recepcionista é notificado sobre o visitante.

### Fluxos Alternativos

- **A1 — Usuário já realizou aula experimental antes:**
O sistema bloqueia a nova solicitação e sugere os planos vigentes.

### RF Relacionados

- RF01, RF05

### RNF Relacionados

- RNF03

### RN Relacionadas

- (Nenhuma relacionada)

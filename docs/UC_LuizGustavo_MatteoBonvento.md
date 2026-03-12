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
- (inserir RF aqui)

### RNF Relacionados
- (inserir RNF aqui)

### RN Relacionadas
- (inserir RN aqui)


Alunos
- Realizar matricula
- Escolher plano
- Efetuar pagamento
- Realizar cadastro facial na catraca
- Agendar aula
- presença em aulas
- Passar pela avaliação física

Recepcionistas
- Gerenciar matrículas
- Indicar planos
- Gerenciar pagamentos
- Gerenciar horário e agendamento das aulas

Instrutores
- Fornecer horários disponíveis para as aulas
- Executar avaliações fisicas
- Cadastrar facial na catraca para acesso

Gerentes
- Gerenciar planos
- Análise de Relatórios Gerenciais
- Gerir pagamentos de funcionários
- Análisar presença de

Sistema de catraca:
- Sincronizar matriculas
- Boquear o acesso de alunos com pagamentos atrasados
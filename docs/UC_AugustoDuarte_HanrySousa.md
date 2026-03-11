## UC01 — Cadastro de Alunos

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário crie um cadastro com dados pessoais, contato, endereço e plano contratado.

### Pré-condições
- Usuário não deve possuir cadastro ativo.

### Pós-condições
- Cadastro criado com sucesso.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida se não há emails e senha iguais aos informados já registrados.
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


# FitPass Gym Management — Modelagem de Classes

Repositório da atividade de **Modelagem de Classes** do sistema FitPass Gym Management, desenvolvida como parte da disciplina de Análise e Projeto de Sistemas.

---



---

##  Classes do Domínio

### Entidades

| Classe | Requisitos Funcionais | Descrição |
|---|---|---|
| `Aluno` | RF01, RF04, RF05, RF06, RF10 | Dados pessoais, contato, endereço, RFID e status de regularidade |
| `Plano` | RF01, RF02, RF04 | Tipos de plano (mensal, trimestral, anual etc.), valor e status ativo |
| `Pagamento` | RF03, RF04, RF09 | Registro de pagamentos presenciais e online com forma e status |
| `Acesso` | RF05, RF09 | Registro de entradas via catraca com validação por RFID |
| `Aula` | RF06, RF07, RF09 | Horários, capacidade máxima e lista de presença |
| `Agendamento` | RF06, RF10 | Reserva de vagas em aulas pelo aluno |
| `Presenca` | RF07 | Registro de presença dos alunos nas aulas pelos instrutores |
| `AvaliacaoFisica` | RF08, RF10 | Peso, IMC, percentual de gordura, observações e anexo |
| `Notificacao` | RF10 | Notificações de vencimento, agendamento e avaliação física |

### Atores

| Classe | Requisitos Funcionais | Responsabilidades |
|---|---|---|
| `Recepcionista` | RF01, RF03 | Cadastrar alunos e registrar pagamentos presenciais |
| `Instrutor` | RF07, RF08 | Registrar presença e realizar avaliações físicas |
| `Gerente` | RF02, RF09 | Gerenciar planos e emitir relatórios gerenciais |

---

## Relacionamentos Principais

| Relacionamento | Cardinalidade | Requisito |
|---|---|---|
| Aluno → Plano | 1 para 1 | RF01 |
| Aluno → Pagamento | 1 para muitos | RF03 |
| Aluno → Acesso | 1 para muitos | RF05 |
| Aluno → Agendamento → Aula | 1 para muitos | RF06 |
| Instrutor → Presenca ← Aula | muitos para 1 | RF07 |
| Instrutor → AvaliacaoFisica ← Aluno | muitos para 1 | RF08 |
| Aluno → Notificacao | 1 para muitos | RF10 |
| Recepcionista → Aluno | 1 para muitos | RF01 |
| Gerente → Plano | 1 para muitos | RF02 |

---

##  Requisitos Funcionais Cobertos

- **RF01** — Cadastro de Alunos: classe `Aluno` com dados pessoais, plano e status; `Recepcionista` realiza o cadastro
- **RF02** — Gerenciamento de Planos: classe `Plano` com tipo, valor e flag `ativo`; `Gerente` gerencia
- **RF03** — Controle de Pagamentos: classe `Pagamento` com forma e status; `Recepcionista` registra presencialmente
- **RF04** — Regularidade do Aluno: método `verificarRegularidade()` na classe `Aluno`, cruzando `Pagamento` e `Plano`
- **RF05** — Controle de Acesso: classe `Acesso` com RFID referenciado em `Aluno` e flag `autorizado`
- **RF06** — Agendamento de Aulas: classes `Agendamento` e `Aula` com `capacidadeMaxima` e `horario`
- **RF07** — Lista de Presença: classe `Presenca` registrada pelo `Instrutor` vinculada à `Aula`
- **RF08** — Avaliação Física: classe `AvaliacaoFisica` com indicadores biométricos e suporte a `anexo`
- **RF09** — Relatórios Gerenciais: método `emitirRelatorio()` no `Gerente`; dados em `Acesso`, `Pagamento`, `Agendamento`
- **RF10** — Notificações: classe `Notificacao` com `tipo` e `status`, associada ao `Aluno`

---


---

*Atividade entregue em 15/04/2026.*

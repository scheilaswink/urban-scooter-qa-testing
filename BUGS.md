# Relatórios de bug — Urban Scooter (Projeto Final)

Os 13 bugs abaixo foram registrados no Jira durante os testes do Urban Scooter. Como o Jira do projeto é privado, eles foram copiados para cá para que qualquer pessoa possa ler os relatórios.

Os IDs (SF-1 a SF-13) são os mesmos que aparecem na coluna "Link de bug do Jira" da planilha.

## Resumo

| ID | Área | Título | Prioridade sugerida |
|---|---|---|---|
| [SF-1](#sf-1) | Cadastro — Sobrenome | Campo aceita 16 caracteres (limite máximo é 15) | Média |
| [SF-2](#sf-2) | Cadastro — Endereço | Campo rejeita 50 caracteres (limite máximo válido) | Média |
| [SF-3](#sf-3) | Cadastro — Endereço | Sistema avança para "Locação" com Endereço vazio | Alta |
| [SF-4](#sf-4) | Cadastro — Estação de metrô | "7th Street/Metro Center" aparece duplicada na lista | Baixa |
| [SF-5](#sf-5) | Cadastro — Telefone | Campo rejeita 10 caracteres (limite mínimo válido) | Média |
| [SF-6](#sf-6) | Cadastro — Telefone | Campo aceita 13 caracteres (limite máximo é 12) | Média |
| [SF-7](#sf-7) | Locação — Data de entrega | Calendário permite selecionar a data atual | Média |
| [SF-8](#sf-8) | Locação — Data de entrega | Calendário permite selecionar datas de meses passados | Alta |
| [SF-9](#sf-9) | Locação — Data de entrega | Campo aceita digitação manual de data passada | Alta |
| [SF-10](#sf-10) | Locação — Período de locação | Nenhum erro visual quando o campo está vazio | Média |
| [SF-11](#sf-11) | Locação — Cor | Nenhuma mensagem quando nenhuma cor é selecionada | Baixa |
| [SF-12](#sf-12) | Locação — Comentário | Campo aceita mais de 24 caracteres | Média |
| [SF-13](#sf-13) | API — `DELETE /api/v1/courier/:id` | Requisição sem id retorna 404 em vez de 400 | Média |

Ambiente dos testes web: Chrome e Opera, resolução 1280x720.

---

<a id="sf-1"></a>

## SF-1 — [Cadastro - Sobrenome] Campo aceita 16 caracteres (limite máximo é 15)

**Pré-condição:** acessar o Urban Scooter e preencher o Nome.

**Passos para reproduzir:**

1. Inserir `AAAAAAAAAAAAAAAA` (16 caracteres) no campo Sobrenome.

**Resultado esperado:** exibir a mensagem de erro "Insira um nome válido".

**Resultado real:** nenhuma mensagem de erro é exibida.

- **Dados de teste:** `AAAAAAAAAAAAAAAA` (16)
- **Caso de teste:** nº 17
- **Prioridade sugerida:** Média

---

<a id="sf-2"></a>

## SF-2 — [Cadastro - Endereço] Campo rejeita 50 caracteres (limite máximo válido)

**Pré-condição:** acessar o Urban Scooter e preencher Nome e Sobrenome.

**Passos para reproduzir:**

1. Inserir `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa` (50 caracteres) no campo Endereço.

**Resultado esperado:** não exibir mensagem de erro (50 é o limite máximo).

**Resultado real:** exibe a mensagem de erro "Insira um número válido" (o texto da mensagem também está incorreto para um campo de endereço).

- **Dados de teste:** `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa` (50)
- **Caso de teste:** nº 22
- **Prioridade sugerida:** Média

---

<a id="sf-3"></a>

## SF-3 — [Cadastro - Endereço] Sistema avança para "Locação" com Endereço vazio

**Pré-condição:** acessar o Urban Scooter e preencher Nome, Sobrenome, Estação e Telefone corretamente.

**Passos para reproduzir:**

1. Deixar o campo Endereço vazio.
2. Clicar em "Próximo".

**Resultado esperado:** não avançar para a tela "Locação" e exibir erro no campo Endereço, como nos demais campos obrigatórios.

**Resultado real:** nenhum erro é exibido e o sistema avança para a tela "Locação".

- **Dados de teste:** (vazio)
- **Caso de teste:** nº 26
- **Prioridade sugerida:** Alta

---

<a id="sf-4"></a>

## SF-4 — [Cadastro - Estação de metrô] "7th Street/Metro Center" aparece duplicada na lista de sugestões

**Pré-condição:** acessar o Urban Scooter e preencher Nome, Sobrenome e Endereço.

**Passos para reproduzir:**

1. Clicar no campo "Estação de metrô".
2. Observar a lista de sugestões.

**Resultado esperado:** cada estação aparece uma única vez na lista.

**Resultado real:** a estação "7th Street/Metro Center" (marcador roxo) aparece duas vezes, de forma idêntica.

- **Dados de teste:** lista carregada da API
- **Caso de teste:** nº 27
- **Prioridade sugerida:** Baixa

---

<a id="sf-5"></a>

## SF-5 — [Cadastro - Telefone] Campo rejeita 10 caracteres (limite mínimo válido)

**Pré-condição:** acessar o Urban Scooter e preencher Nome, Sobrenome, Endereço e Estação.

**Passos para reproduzir:**

1. Inserir `+111111111` (10 caracteres) no campo Telefone.

**Resultado esperado:** não exibir mensagem de erro (10 é o limite mínimo).

**Resultado real:** exibe a mensagem de erro "Insira um número válido".

- **Dados de teste:** `+111111111` (10)
- **Caso de teste:** nº 32
- **Prioridade sugerida:** Média

---

<a id="sf-6"></a>

## SF-6 — [Cadastro - Telefone] Campo aceita 13 caracteres (limite máximo é 12)

**Pré-condição:** acessar o Urban Scooter e preencher Nome, Sobrenome, Endereço e Estação.

**Passos para reproduzir:**

1. Inserir `+111111111112` (13 caracteres) no campo Telefone.

**Resultado esperado:** exibir a mensagem de erro "Insira um número válido".

**Resultado real:** o campo é aceito como válido com 13 caracteres.

- **Dados de teste:** `+111111111112` (13)
- **Caso de teste:** nº 34
- **Prioridade sugerida:** Média

---

<a id="sf-7"></a>

## SF-7 — [Locação - Data de entrega] Calendário permite selecionar a data atual

**Pré-condição:** preencher a tela de cadastro corretamente e avançar até "Locação".

**Passos para reproduzir:**

1. Clicar no campo de data.
2. Selecionar o dia de hoje (28/09/2026) no calendário.

**Resultado esperado:** a data de hoje não pode ser selecionada; somente a partir do dia seguinte.

**Resultado real:** o calendário permite selecionar a data de hoje, e o campo é preenchido com "28.09.2026".

- **Dados de teste:** `28.09.2026`
- **Caso de teste:** nº 36
- **Prioridade sugerida:** Média

---

<a id="sf-8"></a>

## SF-8 — [Locação - Data de entrega] Calendário permite navegar e selecionar datas de meses passados

**Pré-condição:** preencher a tela de cadastro corretamente e avançar até "Locação".

**Passos para reproduzir:**

1. Clicar no campo de data.
2. Clicar na seta "<" duas vezes (agosto).
3. Selecionar o dia 1.

**Resultado esperado:** não permitir navegar para meses passados ou bloquear a seleção de datas passadas.

**Resultado real:** aceita a seleção de "01.08.2026" (data no passado) sem erro.

- **Dados de teste:** `01.08.2026`
- **Caso de teste:** nº 40
- **Prioridade sugerida:** Alta

---

<a id="sf-9"></a>

## SF-9 — [Locação - Data de entrega] Campo aceita digitação manual de data passada

**Pré-condição:** preencher a tela de cadastro corretamente e avançar até "Locação".

**Passos para reproduzir:**

1. Selecionar o texto do campo de data.
2. Digitar manualmente `01.01.2020`.

**Resultado esperado:** não aceitar digitação manual ou rejeitar a data passada.

**Resultado real:** aceita "01.01.2020" sem erro ou bloqueio.

- **Dados de teste:** `01.01.2020`
- **Caso de teste:** nº 41
- **Prioridade sugerida:** Alta

---

<a id="sf-10"></a>

## SF-10 — [Locação - Período de locação] Nenhum erro visual quando o campo está vazio

**Pré-condição:** preencher o cadastro, avançar até "Locação" e preencher a data de entrega.

**Passos para reproduzir:**

1. Deixar o campo "Período de locação" vazio.
2. Clicar em "Fazer pedido".

**Resultado esperado:** bloquear o pedido e exibir erro visual no campo Período, como nos demais campos obrigatórios.

**Resultado real:** o pedido é bloqueado, mas nenhum erro visual é exibido; o usuário não sabe o motivo.

- **Dados de teste:** (vazio)
- **Caso de teste:** nº 49
- **Prioridade sugerida:** Média

---

<a id="sf-11"></a>

## SF-11 — [Locação - Cor] Nenhuma mensagem exibida quando nenhuma cor é selecionada

**Pré-condição:** acessar o Urban Scooter e avançar até "Locação".

**Passos para reproduzir:**

1. Não marcar nenhuma opção de cor.
2. Prosseguir com o pedido.

**Resultado esperado:** exibir uma mensagem ao usuário.

**Resultado real:** nenhuma mensagem é exibida.

- **Dados de teste:** nenhuma cor
- **Caso de teste:** nº 53
- **Observação:** a planilha classifica Cor como campo opcional. É preciso confirmar o requisito antes de corrigir.
- **Prioridade sugerida:** Baixa

---

<a id="sf-12"></a>

## SF-12 — [Locação - Comentário] Campo aceita mais de 24 caracteres

**Pré-condição:** acessar o Urban Scooter e avançar até "Locação".

**Passos para reproduzir:**

1. Inserir `Este comentário tem mais que 44 caracteres` no campo Comentário.

**Resultado esperado:** impedir a digitação além de 24 caracteres ou exibir erro de validação.

**Resultado real:** o campo aceita o texto inteiro, sem cortar e sem erro.

- **Dados de teste:** `Este comentário tem mais que 44 caracteres`
- **Caso de teste:** nº 55
- **Prioridade sugerida:** Média

---

<a id="sf-13"></a>

## SF-13 — [API - DELETE /api/v1/courier/:id] Requisição sem id retorna 404 em vez de 400

**Pré-condição:** servidor do Urban Scooter em execução.

**Passos para reproduzir:**

1. Enviar uma requisição `DELETE` para `/api/v1/courier/`, sem informar o id e sem corpo.

```bash
curl --location --request DELETE 'https://cnt-0feba43d-065c-4168-a8d5-3106c0c253de.containerhub.tripleten-services.com/api/v1/courier/'
```

**Resultado esperado:** status `400 Bad Request`, mensagem "Não há dados suficientes para remover o entregador" (conforme a documentação da API).

**Resultado real:** status `404 Not Found`, corpo:

```json
{"code": 404, "message": "Not Found."}
```

- **Dados de teste:** id = `""` (parâmetro de caminho vazio)
- **Caso de teste:** nº 8 (Tarefa 3: Caso de Teste - API)
- **Prioridade sugerida:** Média
- **Observação:** o endereço do servidor é de um ambiente temporário do curso.

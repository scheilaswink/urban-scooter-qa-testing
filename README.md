# Urban Scooter — Testes manuais web e de API

Projeto final da formação **Analista de QA da TripleTen**: planejamento e execução de testes manuais para o fluxo de pedido de aluguel de patinetes do aplicativo web **Urban Scooter** e testes da sua API REST.

## 📊 Resumo dos resultados

| Tipo de teste | Casos de teste | Aprovados | Reprovados | Bugs registrados no Jira |
|---|---|---|---|---|
| Web (fluxo "Fazer pedido") | 62 | 50 | 12 | SF-1 a SF-12 |
| API REST (entregadores) | 8 | 7 | 1 | SF-13 |
| **Total** | **70** | **57** | **13** | **13 bugs** |

## 🧪 O que foi testado

**Testes web** — formulário de pedido testado no **Chrome e no Opera (1280x720)**:
- Campos de nome, sobrenome, endereço e telefone
- Seleção de estação com autocomplete
- Calendário de data de entrega
- Lista suspensa de período de locação
- Seleção de cores e campo de comentário
- Regras de obrigatoriedade dos campos

**Testes de API** — endpoints de entregadores (`/api/v1/courier`) no **Postman**:
- Criação de entregador (sucesso, login duplicado, campos obrigatórios ausentes)
- Exclusão de entregador (sucesso, exclusão repetida, ID inexistente, ID vazio)
- Validação de códigos de status (200, 201, 400, 404, 409), corpo da resposta e efeito no banco de dados

## 🛠️ Técnicas e ferramentas

- **Técnicas de design de teste:** classes de equivalência e análise de valores limite
- **Ferramentas:** Postman, Jira, Google Planilhas, Chrome, Opera
- **Documentação:** casos de teste com pré-condição, etapas, dados de teste, resultado esperado e resultado real

## 🐞 Principais bugs encontrados

| Bug | Descrição |
|---|---|
| SF-1 | Campo sobrenome aceita 16 caracteres (acima do limite de 15) |
| SF-2 | Campo endereço não aceita 50 caracteres (limite máximo válido) |
| SF-3 | Pedido avança com o campo endereço vazio |
| SF-4 | Estação "7th Street/Metro Center" aparece duplicada na lista |
| SF-5 | Campo telefone não aceita 10 caracteres (limite mínimo válido) |
| SF-6 | Campo telefone aceita 13 caracteres (acima do limite de 12) |
| SF-7 | Calendário permite selecionar a data de hoje |
| SF-8 | Calendário permite navegar para meses passados |
| SF-9 | Campo de data aceita digitação manual de datas inválidas |
| SF-10 | Pedido avança com o período de locação vazio |
| SF-11 | Nenhuma mensagem quando nenhuma cor é selecionada |
| SF-12 | Campo comentário aceita mais de 24 caracteres |
| SF-13 | API: exclusão sem ID não retorna 400 Bad Request |

## 📁 Arquivos

- [casos-de-teste-web.md](casos-de-teste-web.md) — os 62 casos de teste do fluxo web
- [casos-de-teste-api.md](casos-de-teste-api.md) — os 8 casos de teste da API

## 👩‍💻 Autora

Scheila Schwede Wink — [LinkedIn](https://www.linkedin.com/in/scheila-schwede-wink/)

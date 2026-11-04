# Casos de teste — Web (fluxo "Fazer pedido")

Testes executados no Chrome e no Opera (1280x720), com técnicas de classes de equivalência e análise de valores limite.

| ID | Caso de teste | Resultado esperado | Chrome | Opera | Bug (Jira) |
|---|---|---|---|---|---|
| 1 | Validar se o campo nome não aceita 1 caracter | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 2 | Validar se o campo nome aceita 2 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 3 | Validar se o campo nome aceita 3 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 4 | Validar se o campo nome aceita 14 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 5 | Validar se o campo nome aceita 15 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 6 | Validar se o campo nome aceita 16 caracteres | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 7 | Validar se o campo nome aceita espaços | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 8 | Validar se o campo nome aceita traços | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 9 | Validar se o campo nome não aceita ficar vazio | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 10 | Validar se o campo nome aceita caractere especial | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 11 | Validar se o campo nome aceita números | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 12 | Validar se o campo nome aceita espaçamento no início | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 13 | Validar se o campo sobrenome não aceita 1 caractere | Deve exibir mensagem de erro: "Insira um nome válido" | APROVADO | APROVADO |  |
| 14 | Validar se o campo sobrenome aceita 2 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 15 | Validar se o campo sobrenome aceita 14 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 16 | Validar se o campo sobrenome aceita 15 caracteres | Não exibe mensagem de erro (limite máximo) | APROVADO | APROVADO |  |
| 17 | Validar se o campo sobrenome aceita 16 caracteres | Deve exibir mensagem de erro: "Insira um nome válido" | REPROVADO | REPROVADO | SF-1 |
| 18 | Validar se o campo sobrenome aceita espaços e traços | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 19 | Validar se o campo endereço não aceita 4 caracteres | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 20 | Validar se o campo endereço aceita 5 caracteres | Não exibe mensagem de erro (limite mínimo) | APROVADO | APROVADO |  |
| 21 | Validar se o campo endereço aceita 49 caracteres | Não exibe mensagem de erro | APROVADO | APROVADO |  |
| 22 | Validar se o campo endereço aceita 50 caracteres | Não exibe mensagem de erro (limite máximo) | REPROVADO | REPROVADO | SF-2 |
| 23 | Validar se o campo endereço rejeita 51 caracteres | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 24 | Validar se o campo endereço rejeita caracteres inválidos | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 25 | Validar se o campo endereço remove espaços nas pontas ao perder o foco | Espaços nas extremidades são removidos; valor final "spaced addr" (11 caracteres), campo válido | APROVADO | APROVADO |  |
| 26 | Validar se o campo endereço bloqueia o avanço quando vazio (obrigatoriedade) | Não deve avançar para a tela "Locação"; deve exibir erro no campo Endereço, igual aos demais campos obrigatórios | REPROVADO | REPROVADO | SF-3 |
| 27 | Validar se a lista de sugestões de estação não contém duplicatas | A estação "7th Street/Metro Center" (marcador roxo) deveria aparecer somente uma vez na lista | REPROVADO | REPROVADO | SF-4 |
| 28 | Validar se o campo estação rejeita texto livre que não conste na lista | Campo deve ser limpo e exibir erro "Escolha a estação" | APROVADO | APROVADO |  |
| 29 | Validar autocomplete ao digitar parte do nome da estação | Deve sugerir "103rd Street/Watts Towers" na lista | APROVADO | APROVADO |  |
| 30 | Validar se o campo telefone rejeita número sem o símbolo "+" | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 31 | Validar se o campo telefone rejeita 9 caracteres (com +) | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 32 | Validar se o campo telefone aceita 10 caracteres (com +) | Não exibe mensagem de erro (limite mínimo) | REPROVADO | REPROVADO | SF-5 |
| 33 | Validar se o campo telefone aceita 12 caracteres (com +) | Não exibe mensagem de erro (limite máximo) | APROVADO | APROVADO |  |
| 34 | Validar se o campo telefone rejeita 13 caracteres (com +) | Deve exibir mensagem de erro: "Insira um número válido" (acima do máximo de 12) | REPROVADO | REPROVADO | SF-6 |
| 35 | Validar se o campo telefone rejeita 14 caracteres (com +) | Deve exibir mensagem de erro: "Insira um número válido" | APROVADO | APROVADO |  |
| 36 | Validar se o calendário impede selecionar a data de hoje | A data de hoje não deve ser selecionável; somente a partir do dia seguinte | REPROVADO | REPROVADO | SF-7 |
| 37 | Validar se é possível selecionar a data de amanhã (dia seguinte) | Campo deve ser preenchido com a data de amanhã, sem erro | APROVADO | APROVADO |  |
| 38 | Validar se é possível selecionar uma data futura no fim do mês atual | Campo deve ser preenchido com a data selecionada, sem erro | APROVADO | APROVADO |  |
| 39 | Validar se é possível navegar para o próximo mês e selecionar uma data | Calendário deve navegar para o próximo mês e aceitar a data selecionada | APROVADO | APROVADO |  |
| 40 | Validar se o calendário impede navegar/selecionar datas de meses passados | A seta "anterior" não deveria permitir navegar para meses já passados, ou ao menos as datas passadas deveriam ficar bloqueadas para seleção | REPROVADO | REPROVADO | SF-8 |
| 41 | Validar se o campo impede a digitação manual de uma data | O campo não deveria aceitar digitação manual (somente seleção pelo calendário), ou ao menos deveria rejeitar uma data tão antiga | REPROVADO | REPROVADO | SF-9 |
| 42 | Validar se, ao selecionar uma data no calendário, o valor aparece imediatamente no campo | O valor aparece imediatamente no campo | APROVADO | APROVADO |  |
| 43 | Validar se, ao selecionar uma nova data, o campo é destacado em azul | A nova data é destacada em azul no calendário | APROVADO | APROVADO |  |
| 44 | Validar se o calendário abre com o mês atual | Ao clicar no ícone do calendário, ele abre no mês vigente | APROVADO | APROVADO |  |
| 45 | Validar se o dropdown "Período de locação" exibe as opções de 1 a 7 dias | Deve listar de "um dia" até "sete dias" (7 opções) | APROVADO | APROVADO |  |
| 46 | Validar se é possível selecionar o valor mínimo do período (um dia) | Campo deve ser preenchido com "um dia", sem erro | APROVADO | APROVADO |  |
| 47 | Validar se é possível selecionar o valor máximo do período (sete dias) | Campo deve ser preenchido com "sete dias", sem erro | APROVADO | APROVADO |  |
| 48 | Validar se o valor selecionado no período é preservado ao voltar/avançar entre telas | O valor "sete dias" deve continuar selecionado ao retornar à tela "Locação" | APROVADO | APROVADO |  |
| 49 | Validar se o sistema bloqueia o pedido quando o período está vazio (obrigatoriedade) | Não deve avançar nem abrir a confirmação do pedido; deve exibir erro visual no campo Período, igual aos demais campos obrigatórios | REPROVADO | REPROVADO | SF-10 |
| 50 | Validar se é possível selecionar ambas as cores simultaneamente | Ambas as opções devem poder ser marcadas ao mesmo tempo | APROVADO | APROVADO |  |
| 51 | Validar se é possível selecionar somente a cor preta | Preto marcado corretamente, cinza desmarcado | APROVADO | APROVADO |  |
| 52 | Validar se é possível selecionar somente a cor cinza | Cinza marcado corretamente, preto desmarcado | APROVADO | APROVADO |  |
| 53 | Validar se é possível não marcar nenhuma das opções | Deveria aparecer mensagem para o usuário quando nenhuma opção é marcada | REPROVADO | REPROVADO | SF-11 |
| 54 | Validar se o campo comentário aceita 24 caracteres | Não exibe erro, campo válido (limite máximo) | APROVADO | APROVADO |  |
| 55 | Validar se o campo comentário rejeita mais de 24 caracteres | Deve impedir digitação além de 24 caracteres, ou exibir erro de validação | REPROVADO | REPROVADO | SF-12 |
| 56 | Validar se o campo comentário aceita somente letras | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 57 | Validar se o campo comentário aceita somente números | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 58 | Validar se o campo comentário aceita espaços | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 59 | Validar se o campo comentário aceita pontos | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 60 | Validar se o campo comentário aceita vírgulas | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 61 | Validar se o campo comentário aceita caracteres especiais | Não exibe erro, aceita preenchimento | APROVADO | APROVADO |  |
| 62 | Validar se o campo comentário aceita ficar vazio | Não exibe erro | APROVADO | APROVADO |  |

# Casos de teste — API REST (entregadores)

Testes executados no Postman nos endpoints `/api/v1/courier`.

| ID | Caso de teste | Etapas | Dados (corpo da solicitação) | Resultado esperado | Status | Bug (Jira) |
|---|---|---|---|---|---|---|
| 1 | Criar um entregador | 1. Envie uma solicitação POST para /api/v1/courier. 2. Faça login (POST /api/v1/courier/login) para confirmar que o entregador foi criado no banco. | `{ "login": "ninja", "password": "1234", "firstName": "saske" }` | Status 201 Created, corpo `{"ok": true}`. Entregador criado no banco de dados. | Aprovado |  |
| 2 | Criar um entregador com login existente | 1. Envie uma solicitação POST para /api/v1/courier com um login já existente. | `{ "login": "ninja", "password": "1234", "firstName": "saske" }` | Status 409 Conflict, mensagem "Este login não está disponível". Nenhuma alteração no banco de dados. | Aprovado |  |
| 3 | Criar um entregador sem o parâmetro "login" | 1. Envie uma solicitação POST para /api/v1/courier sem o parâmetro "login". | `{ "password": "1234", "firstName": "saske" }` | Status 400 Bad Request, mensagem "Não há dados suficientes para criar uma conta". Nenhuma alteração no banco de dados. | Aprovado |  |
| 4 | Criar um entregador sem o parâmetro "password" | 1. Envie uma solicitação POST para /api/v1/courier sem o parâmetro "password". | `{ "login": "ninja", "firstName": "saske" }` | Status 400 Bad Request, mensagem "Não há dados suficientes para criar uma conta". Nenhuma alteração no banco de dados. | Aprovado |  |
| 5 | Excluir um entregador | 1. Envie uma solicitação DELETE para /api/v1/courier/29. 2. Faça login com o entregador excluído para confirmar a remoção. | id = 29 (parâmetro de caminho) | Status 200 OK, corpo `{"ok": true}`. Entregador removido do banco de dados. | Aprovado |  |
| 6 | Excluir um entregador duas vezes | 1. Envie novamente uma solicitação DELETE para /api/v1/courier/29. | id = 29 (parâmetro de caminho) | Status 404 Not Found, mensagem "Não há entregador com este ID". | Aprovado |  |
| 7 | Excluir um entregador inexistente | 1. Envie uma solicitação DELETE para /api/v1/courier/999. | id = 999 (parâmetro de caminho) | Status 404 Not Found, mensagem "Não há entregador com este ID". | Aprovado |  |
| 8 | Excluir um entregador sem enviar o id | 1. Envie uma solicitação DELETE para /api/v1/courier/ sem o id. | id = "" (parâmetro de caminho vazio) | Status 400 Bad Request, mensagem "Não há dados suficientes para remover o entregador". | Reprovado | SF-13 |

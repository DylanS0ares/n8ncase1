# Case 1 — Automação de tarefas por e-mail

Este fluxo do **n8n** automatiza o envio por e-mail de itens que precisam de atenção, usando uma planilha do Google Sheets como fonte de dados.

## O que a automação faz

1. É executada diariamente às **15h**, conforme o agendamento configurado no n8n.
2. Busca as linhas da planilha conectada.
3. Seleciona as linhas em que `ESTOQUE_ATUAL` é igual a `ESTOQUE_MINIMO`.
4. Converte os resultados em um arquivo Excel (`.xlsx`).
5. Envia o arquivo por e-mail como anexo.

## Requisitos

- Uma instância do [n8n](https://n8n.io/).
- Uma planilha do Google Sheets com as colunas `ESTOQUE_ATUAL` e `ESTOQUE_MINIMO`.
- Credenciais do Google Sheets e do Gmail configuradas no n8n.

## Como importar e configurar

1. No n8n, importe o arquivo [`Case 1.json`](./Case%201.json).
2. No nó **Get row(s) in sheet**, selecione a planilha, a aba e as credenciais do Google Sheets.
3. No nó **Send a message**, selecione as credenciais do Gmail e informe o destinatário, o assunto e a mensagem.
4. Confira o fuso horário da instância para que a execução ocorra no horário desejado.
5. Execute um teste manual e confirme que o e-mail e o anexo estão corretos antes de ativar o fluxo.

O arquivo do fluxo está desativado e contém valores substitutos nos campos que precisam ser configurados. Nenhuma credencial está incluída.

## Observação

O filtro seleciona apenas linhas em que os valores são **iguais**. Ele não inclui automaticamente itens cujo estoque esteja abaixo do mínimo.

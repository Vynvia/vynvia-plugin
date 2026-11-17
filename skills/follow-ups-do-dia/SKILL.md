---
name: follow-ups-do-dia
description: Rodar o dia de prospecção na Vynvia — compromissos de hoje e atrasados, retornos para quem não respondeu, primeiros contatos da fila e os contatos esperando desfecho. Use quando o usuário perguntar "o que tenho pra hoje", pedir para rodar os follow-ups, retomar leads ou organizar a agenda de vendas.
---

# O dia de prospecção na Vynvia

## Comece pela lista do dia

Chame `ver_hoje`. Ela traz, no horário de Brasília:

- `compromissos`: retornos marcados para hoje ou atrasados, com o lembrete do que foi combinado;
- `sem_primeiro_contato`: leads que ainda não receberam nada;
- `esperando_desfecho`: quem foi contatado, já passou a espera e ninguém disse o que aconteceu.

Resuma em poucas linhas e proponha a ordem: compromissos primeiro, depois desfechos, depois primeiros contatos.

## Compromissos e retornos

1. Para cada lead, leia a conversa com `ver_lead` antes de escrever: a continuação precisa saber o que já foi dito e o que o lead respondeu.
2. Gere o retorno com `gerar_mensagem` (`objetivo: "follow_up"`). Envie como no primeiro contato: aprovado, um por vez, `proximo_envio` e depois `confirmar_envio`.
3. Compromisso cumprido: `agendar_follow_up` com `concluir: true`. Novo combinado: `agendar_follow_up` com a data (e o `lembrete`). Combinado desfeito: `cancelar: true`.

## Esperando desfecho

Pergunte ao usuário o que aconteceu com cada um e registre com `registrar_desfecho`:

- respondeu → `replied`, com o texto da resposta em `resposta`, nas palavras do lead;
- não respondeu → `no_reply`;
- não quer → `not_interested`.

Resposta de robô (ausência, menu) não é desfecho: use `registrar_mensagem_automatica`.

## Organizar

Só quando o usuário pedir, nunca por dedução: `marcar_fechado` (fechou negócio), `descartar_lead` (tirar da lista), `favoritar_lead`, `anotar_lead` (detalhe para o próximo contato). Envio registrado por engano: `desfazer_envio` com o id do `historico` do `ver_lead`.

## Envio sem aprovação

Se o usuário pedir para você enviar sozinho, ainda assim revise cada texto antes de enviar, respeite o ritmo do `proximo_envio`, pare se o WhatsApp pedir login e, no fim, diga quem recebeu e quem ficou de fora.

---
name: follow-ups-do-dia
description: Rodar o dia de prospecção na Vynvia — compromissos de hoje e atrasados, triagem de quem está esperando desfecho, retornos para quem não respondeu e primeiros contatos da fila, com um resumo no fim. Use quando o usuário perguntar "o que tenho pra hoje", pedir para rodar os follow-ups, retomar leads ou organizar a agenda de vendas.
---

# O dia de prospecção na Vynvia

## 1. Monte o quadro do dia

- `ver_hoje`: compromissos (hoje e atrasados), leads sem primeiro contato e contatos esperando desfecho. Se vier `lista_incompleta`, avise que a conta tem mais do que a lista mostra.
- `ver_cota`: quantos primeiros contatos e retornos ainda cabem hoje.

Resuma em poucas linhas e proponha a ordem: compromissos, depois desfechos, depois primeiros contatos. Diga o que cabe hoje e o que fica para amanhã.

## 2. Compromissos

Para cada um, leia a conversa com `ver_lead` e o lembrete do compromisso. Decida:

- **Era para retomar a conversa**: gere o retorno (`gerar_mensagem`, `objetivo: "follow_up"`) a partir do que foi combinado.
- **Já foi resolvido**: `agendar_follow_up` com `concluir: true`.
- **Mudou a data**: `agendar_follow_up` com a data nova e o `lembrete`.
- **Não faz mais sentido**: `cancelar: true`.

## 3. Triagem de quem está esperando desfecho

Sem resposta também é desfecho. Para cada lead da fila, descubra se ele respondeu: olhe a conversa no WhatsApp, se você controla o navegador; senão, pergunte ao usuário (em lote: mostre a lista e peça para ele apontar quem respondeu).

- **Respondeu**: `registrar_desfecho` com `replied` e o texto em `resposta`, nas palavras do lead. Depois, a continuação.
- **Respondeu um robô** (ausência, menu): `registrar_mensagem_automatica`. Não conta como resposta.
- **Não respondeu**: `registrar_desfecho` com `no_reply`. Então veja na conversa (`ver_lead`) quantas mensagens ele já recebeu sem responder:
  - primeira ou segunda tentativa: gere o retorno, com um ângulo diferente do anterior;
  - terceira sem resposta: não insista. Diga ao usuário que esse lead encerrou e sugira `descartar_lead` (só descarte se ele concordar).
- **Disse que não quer**: `not_interested`, e não escreva de novo.

Nunca marque `no_reply` em quem respondeu depois do último contato.

## 4. Primeiros contatos

Com o que sobrar do limite do dia, pegue os primeiros da fila `sem_primeiro_contato`, priorizando quem tem WhatsApp e gancho na ficha. Gere, revise contra a ficha e mostre.

## 5. Envio

Aprovado, um por vez: `proximo_envio`, envio no WhatsApp, `confirmar_envio`. Respeite os `aguardar_segundos`. Fora do horário de envio (segunda a sexta, 8h às 19h de Brasília), só sai resposta a quem já respondeu.

Se o usuário pediu para você enviar sozinho, você é a última revisão: leia cada mensagem inteira antes de enviar, pare se o WhatsApp pedir login e não envie por fora.

## 6. Resumo do dia

Feche com: quem recebeu retorno, quem recebeu primeiro contato, quem respondeu (e o que pediu), quem encerrou, o que ficou para amanhã e os compromissos marcados. Se alguém pediu para falar depois, confirme que o retorno está agendado.

## Organizar

Só quando o usuário pedir, nunca por dedução: `marcar_fechado`, `descartar_lead`, `favoritar_lead`, `recuperar_lead_apagado`. Detalhe para o próximo contato vai em `anotar_lead`. Envio registrado por engano: `desfazer_envio`, com o id do `historico` do `ver_lead`.

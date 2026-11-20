---
name: follow-ups-do-dia
description: Rodar o dia de prospecção na Vynvia — compromissos de hoje e atrasados, triagem de quem está esperando desfecho, retornos para quem não respondeu, primeiros contatos da fila e, quando o usuário pedir, a reativação de quem ficou sem responder, com um resumo no fim. Use quando o usuário perguntar "o que tenho pra hoje", pedir para rodar os follow-ups, retomar ou reativar leads, ou organizar a agenda de vendas.
---

# O dia de prospecção na Vynvia

## 1. Monte o quadro do dia

- `ver_hoje`: compromissos (hoje e atrasados), leads sem primeiro contato e contatos esperando desfecho. Se vier `lista_incompleta`, avise que a conta tem mais do que a lista mostra.
- `ver_cota`: quantos primeiros contatos e retornos ainda cabem hoje, e se a `janela_de_envio` está aberta (segunda a sexta, 8h às 19h de Brasília). Fechada, avise o usuário antes de gerar mensagem.

Resuma em poucas linhas e proponha a ordem: compromissos, depois desfechos, depois primeiros contatos. Diga o que cabe hoje e o que fica para amanhã. Se o aplicativo exibiu o cartão da Vynvia com a lista ou a ficha, não repita o conteúdo.

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
  - recebeu só a primeira: gere o retorno, com um ângulo diferente do anterior;
  - já recebeu o retorno e não respondeu: não insista. A Vynvia encerra esse lead sozinha: ele sai da lista do dia e passa para a reativação (seção 6). O padrão é parar na segunda mensagem; se a conta escolheu três tentativas, o segundo retorno ainda cabe.

Quem recebeu a primeira mensagem e ficou duas semanas sem o retorno também sai da lista do dia e vai para a reativação. Não precisa descartar ninguém por isso.
- **Disse que não quer**: `not_interested`, e não escreva de novo.

Nunca marque `no_reply` em quem respondeu depois do último contato. `marcar_desfechos_sem_resposta` (marca todos de uma vez) só a pedido do usuário.

## 4. Primeiros contatos

Com o que sobrar do limite do dia, pegue os primeiros da fila `sem_primeiro_contato`, priorizando quem tem WhatsApp e gancho na ficha. Gere, revise contra a ficha e mostre. Lead com `whatsapp_recusado` não recebe mensagem de WhatsApp: outro canal ou pule; `reabrir_whatsapp` só se o usuário disser que o número está certo. Se vier `sem_gancho`, a mensagem sai genérica: avise.

## 5. Envio

Aprovado, um por vez: `proximo_envio`, envio no WhatsApp, `confirmar_envio`. Respeite os `aguardar_segundos`. Fora do horário de envio (segunda a sexta, 8h às 19h de Brasília), só sai resposta a quem já respondeu.

Aprovado, mas o envio não pode sair agora (janela fechada, espera longa): guarde cada mensagem com `guardar_na_fila`. Para enviar o que está guardado, `proximo_da_fila`, uma por vez, com `confirmar_envio` depois de cada uma. `tirar_da_fila` só a pedido do usuário.

Se o usuário pediu para você enviar sozinho, você é a última revisão: leia cada mensagem inteira antes de enviar, pare se o WhatsApp pedir login e não envie por fora.

## 6. Reativação (só quando o usuário pedir)

Reativar é mandar uma nova mensagem a quem recebeu as anteriores, não respondeu e saiu da lista do dia. Nunca faça por conta própria: espere o usuário pedir ("quem eu posso reativar?", "reativa os melhores").

- `ver_reativar`: traz o total, os `sugeridos` (melhor nota, com WhatsApp) e as `prontas` (já têm a mensagem escrita). Se vier `lista_incompleta`, avise que há mais do que a lista mostra.
- **Prontas**: o texto vem no campo `mensagem`. Confira contra a ficha (`ver_lead`) e envie. Não gere de novo.
- **Sugeridos**: `gerar_mensagem` com `objetivo: "reactivation"`. Leia antes a conversa em `ver_lead` e peça um ângulo diferente das mensagens que ele já recebeu.
- É uma mensagem por lead: depois do envio ele sai da lista e não volta.
- O envio é o da seção 5 e conta como retorno. Veja em `ver_cota` quantos retornos ainda cabem hoje e não passe disso.

## 7. Resumo do dia

Chame `ver_resumo_do_dia` e não conte de cabeça. Feche com: quem recebeu retorno, quem recebeu primeiro contato, quem foi reativado, quem respondeu (e o que pediu), quem encerrou, o que ficou para amanhã e os compromissos marcados. Se alguém pediu para falar depois, confirme que o retorno está agendado. Se algum envio trouxe `texto_reescrito`, diga quais mensagens você reescreveu.

## Organizar

Só quando o usuário pedir, nunca por dedução: `marcar_fechado`, `descartar_lead`, `favoritar_lead`, `recuperar_lead_apagado`. Detalhe para o próximo contato vai em `anotar_lead`. Envio registrado por engano: `desfazer_envio`, com o id do `historico` do `ver_lead`.

## Regras

- Não mostre id ao usuário: chame a empresa pelo nome.
- Não pesquise na web sobre a Vynvia nem sobre link do WhatsApp: use as ferramentas.

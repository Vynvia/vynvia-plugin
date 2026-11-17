# Vynvia para Claude

Prospecção B2B no Brasil pela sua IA. Com o plugin da Vynvia, o Claude busca empresas na região que você quiser, escreve a abordagem com os dados de cada uma, envia pelo WhatsApp no ritmo seguro da sua conta e acompanha follow-ups e respostas. Tudo fica registrado na Vynvia.

## O que vem no plugin

- **Conector `vynvia`**: o servidor MCP da Vynvia (`https://www.vynvia.com.br/api/mcp`), com login pela sua conta (OAuth).
- **Skills**:
  - `prospectar-nicho`: buscar um tipo de empresa numa região, escrever e enviar o primeiro contato;
  - `follow-ups-do-dia`: compromissos, retornos, primeiros contatos e desfechos do dia;
  - `responder-lead`: registrar a resposta de um lead e escrever a continuação.

## O que você precisa

Uma conta na [Vynvia](https://www.vynvia.com.br) num plano com o MCP (Start ou Business). Na primeira chamada, o Claude abre a tela de autorização da Vynvia para você permitir o acesso.

## Exemplos

- "Busque escritórios de contabilidade em Juiz de Fora - MG e me mostre as primeiras mensagens."
- "O que eu tenho pra hoje na Vynvia?"
- "A Clínica Sorriso respondeu: 'pode me mandar mais detalhes?'. Como respondo?"

## Instalar no Claude Code

```bash
/plugin marketplace add Vynvia/vynvia-plugin
/plugin install vynvia@vynvia
```

## Política de privacidade

O plugin não guarda dados: ele liga o Claude ao servidor da Vynvia, que trata os dados conforme a [Política de Privacidade](https://www.vynvia.com.br/privacidade). Em resumo:

- **Coleta**: os dados da sua conta e os das empresas que você busca (dados públicos de pessoas jurídicas).
- **Uso e armazenamento**: para buscar, escrever e registrar a prospecção na sua conta, em servidores no Brasil.
- **Compartilhamento**: com os provedores necessários ao serviço (hospedagem, banco de dados, modelos de IA), sem venda de dados.
- **Retenção**: enquanto a conta estiver ativa, e pelo prazo previsto na política depois do encerramento.
- **Contato**: privacidade@vynvia.com.br.

A IA conectada nunca recebe o telefone dos leads: o envio pelo WhatsApp sai por um link que a Vynvia monta, dentro do limite diário da conta.

## Suporte

suporte@vynvia.com.br · [vynvia.com.br/mcp](https://www.vynvia.com.br/mcp)

## Licença

MIT

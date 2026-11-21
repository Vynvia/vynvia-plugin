# Vynvia para Claude

Prospecção B2B no Brasil pela sua IA. Com o plugin da Vynvia, o Claude busca empresas na região que você quiser, escreve a abordagem com os dados de cada uma, envia pelo WhatsApp uma mensagem por vez, em ritmo variado e dentro do limite diário da sua conta, e acompanha follow-ups e respostas. Tudo fica registrado na Vynvia.

## O que vem no plugin

- **Conector `vynvia`**: o servidor MCP da Vynvia (`https://www.vynvia.com.br/api/mcp`), com login pela sua conta (OAuth).
- **Skills**:
  - `prospectar-nicho`: escolhe o nicho, busca, prioriza os melhores leads pelo perfil da conta e pelo limite do dia, escreve, revisa e envia o primeiro contato;
  - `follow-ups-do-dia`: compromissos, triagem de quem está esperando desfecho (respondeu, não respondeu, encerrou), retornos, primeiros contatos, reativação de quem ficou sem responder (quando você pedir) e um resumo no fim;
  - `responder-lead`: registra a resposta, classifica o que o lead quer e escreve a continuação certa para cada caso;
  - `o-que-esta-funcionando`: balanço da prospecção por nicho e região, com a recomendação da próxima busca.

## O que você precisa

Uma conta na [Vynvia](https://www.vynvia.com.br), em qualquer plano (Free, Start ou Business). Na primeira chamada, o Claude abre a tela de autorização da Vynvia para você permitir o acesso.

## Exemplos

- "Busque escritórios de contabilidade em Juiz de Fora - MG e me mostre as primeiras mensagens."
- "O que eu tenho pra hoje na Vynvia?"
- "A Clínica Sorriso respondeu: 'pode me mandar mais detalhes?'. Como respondo?"
- "Como está a minha prospecção? Onde eu busco a seguir?"

## Instalar no Claude Code

```bash
/plugin marketplace add Vynvia/vynvia-plugin
/plugin install vynvia@vynvia
```

## Política de privacidade

O plugin não guarda dados: ele liga o Claude ao servidor da Vynvia, que trata os dados conforme a [Política de Privacidade](https://www.vynvia.com.br/privacidade). Em resumo:

- **Coleta**: os dados da sua conta e os das empresas que você busca (dados públicos de pessoas jurídicas).
- **Uso e armazenamento**: para buscar, escrever e registrar a prospecção na sua conta. A aplicação e o banco de dados ficam no Brasil (região de São Paulo); alguns provedores, como os de inteligência artificial, tratam dados fora do país, como descreve a política de privacidade.
- **Compartilhamento**: com os provedores necessários ao serviço (hospedagem, banco de dados, modelos de IA), sem venda de dados.
- **Retenção**: enquanto a conta estiver ativa, e pelo prazo previsto na política depois do encerramento.
- **Contato**: privacidade@vynvia.com.br.

Os campos de telefone dos leads não vão para as listas nem para a ficha (só a indicação de que há telefone), e e-mail, site ou Instagram em que a Vynvia encontre um número de telefone saem omitidos. O envio pelo WhatsApp sai pelo link que a Vynvia monta, dentro do limite diário da conta.

## Suporte

suporte@vynvia.com.br · [vynvia.com.br/mcp](https://www.vynvia.com.br/mcp)

## Licença

MIT

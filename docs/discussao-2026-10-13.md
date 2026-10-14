# Discussão de planejamento — imobia (2026-10-13)

Registro da conversa que originou o projeto. Status: **proposta em discussão**.

## 1. Pedido inicial

O usuário trouxe uma recomendação (gerada por outro assistente) para uma imobiliária com atendimento
por WhatsApp, Instagram, site e corretores:

- **EspoCRM + extensão Real Estate** — CRM de imóveis e clientes (open source).
- **Chatwoot** — central omnichannel (WhatsApp, Instagram, Facebook, chat do site), distribui conversas.
- **Twenty CRM** — alternativa para construir CRM próprio com IA.
- **n8n** — integração e automação.
- **API oficial da Meta** — WhatsApp.
- **Agente de IA** — atende 24h, qualifica, busca imóveis no CRM, agenda visita, encaminha ao corretor.
- **VPS própria** — hospedagem.

Pedido do usuário: *"quero um sistema simples de atendimento e gestão, com resposta automática.
Usar Evolution para WhatsApp. Sistema completo mas simples, direto, excluir tudo que incomoda.
O uso interno deve ser via Telegram."*

## 2. Análise da proposta original

| Peça | Problema | Decisão |
|---|---|---|
| Chatwoot | Painel web inteiro só para a equipe ler conversas | **Cortar** — Telegram é a central da equipe |
| EspoCRM | CRM PHP pesado; integração WhatsApp manual | **Cortar** — modelo de dados próprio |
| n8n | Mais um serviço; lógica espalhada em fluxos visuais | **Cortar** — um serviço com código |
| API oficial Meta | Custo por mensagem, aprovação | **Trocar por Evolution API** |
| Instagram/Facebook/portais | Escopo extra | **Fase 2** |

Alertas levantados:
1. Evolution é não oficial — risco de banimento. Mitigar com chip dedicado e sem disparo em massa.
2. A resposta automática exige um modelo de IA via API (custo mensal da imobiliária). Nenhuma API é
   chamada no desenvolvimento sem autorização explícita; testes com respostas simuladas.
3. Projetos locais servem de referência: `~/projetos/imob360` e `~/projetos/wacrm`.

## 3. Respostas do usuário

- Imobiliária **real**, **venda e locação**, **5 corretores**, para uma pessoa da comunidade.
- **Nada de usar outros sistemas** — usar as referências e criar um sistema **nosso**.
- Olhar o que já temos, as referências passadas e buscar outras.
- **Simplicidade, nada de formulários, quase tudo automático.**
- Contato da equipe: **Telegram** ou **painel de monitoramento**.

## 4. Entendimento registrado (a confirmar)

- Cliente final fala só por WhatsApp (Instagram/site depois).
- IA atende 24h, qualifica, sugere imóveis **reais do cadastro**, envia fotos, propõe visita.
- Corretor assume a conversa quando quiser; a IA silencia naquela conversa.
- Cadastro de imóvel automático: corretor manda fotos + áudio/texto no Telegram; IA extrai campos.
- Painel **só de leitura**: leads, conversas, funil, imóveis, desempenho por corretor.
- IA via API de LLM (custo da imobiliária; escolha do modelo depois).
- Roda numa VPS com Docker.
- **Sucesso:** nenhum lead sem resposta, todo lead chega qualificado ao corretor certo, o dono vê
  tudo no painel sem ninguém preencher nada.

## 5. Pesquisa

Detalhes em [`pesquisa-2026-10-13.md`](pesquisa-2026-10-13.md). Principais achados:
- Não existe projeto pronto com Evolution + IA + handoff por Telegram — construir o nosso.
- imob360: melhor modelo de dados (Property, Person, Lead, Visit, Contract); código não compila.
- wacrm: melhor lógica de handoff IA→humano, follow-up agendado, base de conhecimento, log de custo.
- EspoCRM: matching imóvel × necessidade do cliente, nos dois sentidos.
- Telegram: supergrupo com tópicos — um tópico por lead.

## 6. Decisão em aberto

Como a equipe trabalha no Telegram:
- **A) Grupo com um tópico por cliente** (recomendado).
- **B) Privado de cada corretor com o bot.**
- **C) Misto** (grupo para supervisão + privado por corretor).

Pergunta pendente ao usuário: A, ou é preciso que um corretor não veja os clientes do outro (B/C)?

Plano detalhado: [`plano-arquitetura.md`](plano-arquitetura.md).
